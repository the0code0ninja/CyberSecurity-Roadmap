
#  3 Basic steps

##  7 Advance steps

##  Total 10 steps For ```'Passive Recon' ```

#  Basic steps

### 1) Know about your target:- 

use social media platforms to gain basic information about the target, like what is type of organisation, how many members, place, etc.
We can use social media platforms like Instagram, LinkedIn, Twitter(Now X), etc In order to gain some information

### 2) Using NSLOOKUP and Hacking search engines

i)Nslookup :-```https://www.nslookup.io/```

nslookup (Name Server Lookup) is a vital command-line tool used to query the Domain Name System (DNS) to map domain names to IP addresses or vice-versa. It helps network administrators diagnose DNS issues, verify record configurations, and check the health of specific DNS servers.

<img width="1524" height="695" alt="image" src="https://github.com/user-attachments/assets/a6e9938f-1f90-4af2-a236-1ee64f0b6cc6" />


ii)Shodon: -```https://www.shodan.io/```

Shodan is a specialized search engine designed to find and map internet-connected devices, often referred to as the "search engine for the Internet of Things (IoT)." Unlike Google, which indexes web pages, Shodan crawls the backend of the internet to discover routers, servers, webcams, industrial control systems, and smart home appliances

<img width="1522" height="775" alt="image" src="https://github.com/user-attachments/assets/16eaef31-fb74-45aa-b3f6-80eb109ca0e8" />


iii) Censys :- ```https://search.censys.io/```

This can show some more information about the target machines, ip address, sometimes open ports and many more.
<img width="1536" height="777" alt="image" src="https://github.com/user-attachments/assets/04d16888-cb4a-4415-80e9-1c3e9d0d3392" />


### 3) Google Dorking:- 

We can see specific things related to target , with the use of google dorking.

Some examples are:- filetype, cache, intext, inurl, AllinURL, etc.

Resource :- ``` https://gist.github.com/sundowndev/283efaddbcf896ab405488330d1bbc06``` 

# Advance steps

1) To know the web-technologies being used on website.

We can see this, by using the extensions ‘Netcraft’, ‘Wappalyzer’.
<img width="1459" height="746" alt="image" src="https://github.com/user-attachments/assets/2d464c92-4736-4c85-8c6d-6836dd9136ef" />
<img width="1453" height="753" alt="image" src="https://github.com/user-attachments/assets/ccf19d0f-e629-4b42-9c15-a87b926fde6e" />

2) Find Subdomains of a site

We can get the subdomains by using website ‘sub-domain finder’.
Resource:- ```https://subdomainfinder.c99.nl/```
<img width="1523" height="765" alt="image" src="https://github.com/user-attachments/assets/53319f94-b1b6-4a75-b468-97919d0f3902" />


3) Find all the URLs of website

We can get all the links of target by just simply copying the url of target and paste it into website 'Link-extractor'
Resource: -```https://www.firecrawl.dev/tools/url-extractor```
<img width="1191" height="728" alt="image" src="https://github.com/user-attachments/assets/bc3de393-b05e-404d-8375-96962f77232e" />


4) Finding the buffer size of website

We can use terminal to check the maximum buffer size of target.

Ping target_url

command:- ```Ping -f -l any_size target_url```

 5) Finding more details of security of target website.

‘SSLabs.com’ in this website, paste the target url and then click on ‘test your server’.
Resource:- ```https://www.ssllabs.com/ssltest/```
<img width="1517" height="753" alt="image" src="https://github.com/user-attachments/assets/ab595f17-e12f-461c-b088-3f61168a7eb0" />


  6) Find how security headers of a target is deployed.

We can get this on ‘Security headers.com’
Resource:-  ````https://securityheaders.com/````
<img width="1524" height="726" alt="image" src="https://github.com/user-attachments/assets/4fe799f9-344e-45b9-b388-e67c9f2f78b1" />


 7) Using ‘WayBack Machine’ the check previous view of target url’

‘archive.org’ is the website, we have to paste our target url to see the previous view of website.

This is used to see how a particular website looks before 3-5 yrs ago.

We use this, to get some sensitive information of a website, that is been removed after sometime, and not present in today's interface.
Resoruce:- ```https://archive.org/```
<img width="1528" height="751" alt="image" src="https://github.com/user-attachments/assets/e92c2128-ab25-4ac1-a581-9564d3268b2f" />


# ``` BONUS ``` 
=============================================================================================================
1) Getting Info related to email adddress
   Resource: -```https://behindtheemail.com/```
   <img width="1523" height="766" alt="image" src="https://github.com/user-attachments/assets/8f4895c8-ce72-44e8-a8ef-fd4a9d816ebc" />
   Resource 2:- ```https://dehashed.com/search#breachCheck```
   This is for gathering breached credentials.
   <img width="1527" height="662" alt="image" src="https://github.com/user-attachments/assets/0a4ac8bd-ec19-4136-beb1-7113ae99416b" />


