# HawkEye

{% hint style="warning" %}
Always open malware in a secure environment like a VM.
{% endhint %}

{% hint style="info" %}
We will be using the [REMnux](https://remnux.org/) distribution which is specifically made for reverse engineering.
{% endhint %}

##

> Q1. How many packets does the capture have?

* In order to find the number of packets we have to go to the `Statistics > Capture File Properties` section.&#x20;

<figure><img src="../.gitbook/assets/hawkeye 1.png" alt=""><figcaption></figcaption></figure>

##

> Q2. At what time was the first packet captured?

* We have to set the format to UTC in the `View > Time Display Format` section.&#x20;

<figure><img src="../.gitbook/assets/hawkeye 2.png" alt=""><figcaption></figcaption></figure>

* Alternatively, we can also find the answer in the `Capture File Properties` section.!

<figure><img src="../.gitbook/assets/hawkeye 2.2.png" alt=""><figcaption></figcaption></figure>

##

> Q3. What is the duration of the capture?

* Again this answer can be found in the `Capture File Properties` section.&#x20;

<figure><img src="../.gitbook/assets/hawkeye 3.png" alt=""><figcaption></figcaption></figure>

##

> Q4. What is the most active computer at the link level?

* If we go to the `Statistics > Endpoints` section, we can see information about all the devices in the packet transfer.&#x20;

<figure><img src="../.gitbook/assets/hawkeye 4.png" alt=""><figcaption></figcaption></figure>

##

> Q5. Manufacturer of the NIC of the most active system at the link level?

* We can use [A-Packets](https://apackets.com/), in order to find the answer easily.
* Open the `Ethernet` section of the file.&#x20;

<figure><img src="../.gitbook/assets/hawkeye 5.png" alt=""><figcaption></figcaption></figure>

* Alternatively, we can also use Wireshark to find the NIC manufacturer.
* Put the following filter on in order to filter for relevant traffic.

```
eth.addr==00:08:02:1c:47:ae
```

* On applying the filter, we can see the following packet.&#x20;

<figure><img src="../.gitbook/assets/hawkeye 5.3.png" alt=""><figcaption></figcaption></figure>

* The source address is `00:08:02:1c:47:ae`. Let's search this MAC address on [DNSChecker](https://dnschecker.org/).

<figure><img src="../.gitbook/assets/hawkeye 5.2.png" alt=""><figcaption></figcaption></figure>

* Same answer as the one we got from A-Packets.

##

> Q6. Where is the headquarter of the company that manufactured the NIC of the most active computer at the link level?

* A quick Google search tells us where the headquarters are located.&#x20;

<figure><img src="../.gitbook/assets/hawkeye 6.png" alt=""><figcaption></figcaption></figure>

##

> Q7. The organization works with private addressing and netmask /24. How many computers in the organization are involved in the capture?

* The `/24` subnet mask denotes that the first 24 bytes are part of the network and the last 8 bytes are part of the host.
* This means that every host within the `10.4.10.x/24` subnet is part of the organization.

<figure><img src="../.gitbook/assets/hawkeye 7.png" alt=""><figcaption></figcaption></figure>

* We can see that the first 3 devices are part of the same subnet thus the same organization. Note that the broadcast address is not counted.

##

> Q8. What is the name of the most active computer at the network level?

* Since we already know the MAC address of the most active host, we can set a filter for that address and `dhcp` to find the host name.

```
eth.addr==00:08:02:1c:47:ae && dhcp
```

* Let's look at the `Host Name` option.&#x20;

<figure><img src="../.gitbook/assets/hawkeye 8.png" alt=""><figcaption></figcaption></figure>

##

> Q9. What is the IP of the organization's DNS server?

* In the `DNS` section of A-Packets, we can see the IP of the organization.&#x20;

<figure><img src="../.gitbook/assets/hawkeye 9.png" alt=""><figcaption></figcaption></figure>

* We can also filter for `dns` packets in Wireshark.&#x20;

<figure><img src="../.gitbook/assets/hawkeye 9.2.png" alt=""><figcaption></figcaption></figure>

##

> Q10. What domain is the victim asking about in packet 204?

* Let's analyze the 204th packet.&#x20;

<figure><img src="../.gitbook/assets/hawkeye 10.png" alt=""><figcaption></figcaption></figure>

##

> Q11. What is the IP of the domain in the previous question?

* Let's look through the `Connections` section in A-Packets.&#x20;

<figure><img src="../.gitbook/assets/hawkeye 11.png" alt=""><figcaption></figcaption></figure>

* In order to find the answer in Wireshark, we have to set the following filter:

```
frame contains proforma-invoices.com
```

* Look in the destination IP address field.

<figure><img src="../.gitbook/assets/hawkeye 11.2.png" alt=""><figcaption></figcaption></figure>

##

> Q12. Indicate the country to which the IP in the previous section belongs.

* We can use the `IP Lookup` tool in DNSChecker.

<figure><img src="../.gitbook/assets/hawkeye 12.png" alt=""><figcaption></figcaption></figure>

##

> Q13. What operating system does the victim's computer run?

* Let's filter the http requests using the following filter:

```
eth.addr==00:08:02:1c:47:ae && http.request
```

* Go to `Follow > TCP Stream` in order to see the entire message.&#x20;

<figure><img src="../.gitbook/assets/hawkeye 13 (1).png" alt=""><figcaption></figcaption></figure>

* We can also find the OS in the `HTTP` section of A-Packets.&#x20;

<figure><img src="../.gitbook/assets/hawkeye 13.2.png" alt=""><figcaption></figcaption></figure>

##

> Q14. What is the name of the malicious file downloaded by the accountant?

* In the `HTTP Headers` section of A-Packets, we can find the file that is being downloaded. !

<figure><img src="../.gitbook/assets/hawkeye 14.png" alt=""><figcaption></figcaption></figure>

* Alternatively, in Wireshark we can filter for `GET` request using the following filter:

```
http.request.method == GET
```

* Only the 210th packet is accessing a file.&#x20;

<figure><img src="../.gitbook/assets/hawkeye 14.2.png" alt=""><figcaption></figcaption></figure>

##

> Q15. What is the md5 hash of the downloaded file?

* Let's extract the file via `File > EXport Objects > HTTP`.
* We can now use `md5sum` command in order to obtain the file hash.

```
$ md5sum tkraw_Protected99.exe 
71826ba081e303866ce2a2534491a2f7  tkraw_Protected99.exe
```

* We can also upload the file to [VirusTotal](https://www.virustotal.com/gui/home/search) in order to find the file hash.&#x20;

<figure><img src="../.gitbook/assets/hawkeye 15.png" alt=""><figcaption></figcaption></figure>

##

> Q17. What software runs the webserver that hosts the malware?

* In Wireshark, we can again follow the TCP Stream in order to find the server.&#x20;

<figure><img src="../.gitbook/assets/hawkeye 17.png" alt=""><figcaption></figcaption></figure>

##

> Q18. What is the public IP of the victim's computer?

* Let's filter for all HTTP requests:

```
http.request
```

* If we follow TCP Stream, we can find the public IP.&#x20;

<figure><img src="../.gitbook/assets/hawkeye 18.png" alt=""><figcaption></figcaption></figure>

##

> Q19. In which country is the email server to which the stolen information is sent?

* We can use the `IP Lookup` tool in DNSChecker.&#x20;

<figure><img src="../.gitbook/assets/hawkeye 19.png" alt=""><figcaption></figcaption></figure>

##

> Q20. Analyzing the first extraction of information. What software runs the email server to which the stolen data is sent?

* Put on the following filter:

```
ip.addr == 10.4.10.132 && smtp.req
```

* We can follow the TCP stream.

<figure><img src="../.gitbook/assets/hawkeye 20.png" alt=""><figcaption></figcaption></figure>

##

> Q21. To which email account is the stolen information sent?

* Further down in the TCP stream we can see the email that the information is sent to. !

<figure><img src="../.gitbook/assets/hawkeye 21.png" alt=""><figcaption></figcaption></figure>

##

> Q22. What is the password used by the malware to send the email?

* We will use the same filter as before:

```
ip.addr == 10.4.10.132 && smtp.req
```

* We can see a password. However, it seems to be base64 encoded.&#x20;

<figure><img src="../.gitbook/assets/hawkeye 22.2.png" alt=""><figcaption></figcaption></figure>

* Let's use CyberChef to decode the password.&#x20;

<figure><img src="../.gitbook/assets/hawkeye 22.png" alt=""><figcaption></figcaption></figure>

##

> Q23. Which malware variant exfiltrated the data?

* If we follow the same TCP stream, we can see a huge blob of data.

<figure><img src="../.gitbook/assets/hawkeye 23.2.png" alt=""><figcaption></figcaption></figure>

* This has been base64 encoded. We have to again use CyberChef to decode it.&#x20;

<figure><img src="../.gitbook/assets/hawkeye 23.png" alt=""><figcaption></figcaption></figure>

##

> Q24. What are the bankofamerica access credentials? (username:password)

* This information is available in the output for the previous question.&#x20;

<figure><img src="../.gitbook/assets/hawkeye 24.png" alt=""><figcaption></figcaption></figure>

##

> Q25. Every how many minutes does the collected data get exfiltrated?

* If we look at the SMTP packets, we can see that the email is sent every 10 minutes.

<figure><img src="../.gitbook/assets/hawkeye 25.png" alt=""><figcaption></figcaption></figure>
