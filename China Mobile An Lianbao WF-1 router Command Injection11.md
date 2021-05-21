# Background
China Mobile An Lianbao WF-1 router is an AX1800 router based on Qualcomm's five-core processor. It adopts a new generation of 11AX technology, 2.4G and 5G dual-band concurrently, and can provide a wireless rate of 1800M, providing high-speed and stable WiFi coverage

# Description
China Mobile An Lianbao WF-1 router provide web interface /api/ZRRuleFilter/set_firewall_level which receive parameters by POST request, and the parameter firewall_level has a command injection vulnerability, An attacker can use the vulnerability to execute remote commands

# Affect Versions
V1.0.1

# POC
![image](https://user-images.githubusercontent.com/13774458/119132056-cc321280-ba6c-11eb-9ece-13347288a464.png)



Interface set_firewall_level recevice params from post request as follow：

![image](https://user-images.githubusercontent.com/13774458/119132097-d94f0180-ba6c-11eb-9256-a2cecfe272cb.png)

![image](https://user-images.githubusercontent.com/13774458/119132104-dce28880-ba6c-11eb-8e62-746647aeb2bf.png)

Cause command injection:

![image](https://user-images.githubusercontent.com/13774458/119132128-e5d35a00-ba6c-11eb-9a5b-28c1a79c87ed.png)

result of POC is：

![image](https://user-images.githubusercontent.com/13774458/113553708-bd151380-962a-11eb-9e78-e5a77f98379a.png)

# Acknowledgements
repoter :Lewei Qu and Dongxiang Ke

# References
https://www.cnvd.org.cn/flaw/show/CNVD-2021-03520

https://www.ebuy7.com/item/china-mobile-wireless-router-qualcomm-qiki-wifi6-routing-mesh-network-home-5g-dual-frequency-double-gigabit-port-wall-wall-high-speed-%E2%80%8B%E2%80%8Bhigh-power-enhanced-dormitory-students-an-lianbao-wf-1-628692180620

http://iot.10086.cn/?l=en-us
