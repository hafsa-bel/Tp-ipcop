# Tp-ipcop

# Introduction : 

  **IPCop** is an open-source Linux distribution designed to be used as a network firewall. It is based on the Linux *Netfilter/IPtables* framework and provides a user-friendly web interface for firewall configuration and management. **IPCop** is often used in small and medium-sized businesses as well as home networks to protect local networks from external threats.

The primary role of **IPCop** is to control the flow of incoming and outgoing data in the network by applying specific security rules. It allows for defining restrictions and access policies to prevent attacks from the internet, restrict access to certain services or websites, and safeguard sensitive data from intrusions.

# Schema :

 Here's an architecture of what we're going to do: 
<p align="center">
  <img width="1000" src="https://github.com/hafsa-bel/Tp-ipcop/assets/73228919/a1c0323f-0995-4d4b-bb18-2fd289755a17">
</p>



# IPCOP'S installation :

- ***Domain name selection***:
Enter the domain name for this IPCop.
<p align="center">
  <img width="1000" src="https://github.com/hafsa-bel/Tp-ipcop/assets/73228919/0c7529a8-5a8e-4f7b-b0c5-22e6cd9f0d16">
</p>

- ***Network card assignment***:
Here we're going to select each interface and we're going to assign the ip addresses to each one.
<p align="center">
  <img width="1000" src="https://github.com/hafsa-bel/Tp-ipcop/assets/73228919/3ed3b701-166d-4fd3-ac31-5d3d20879d89">
</p>

```diff
+ For the green interface we assigned the ip address : 192.168.1.10
! For the orange interface we assigned the ip address : 192.168.2.10
```

![25](https://github.com/hafsa-bel/Tp-ipcop/assets/73228919/dbba7e31-ef10-4221-850b-9b59c020c04d)
![26](https://github.com/hafsa-bel/Tp-ipcop/assets/73228919/e8f82193-659e-46bf-8c6a-94051c8bed24)

- ***Red interface selection***:
This is where you select the type of Red interface on IPCop.
<p align="center">
  <img width="1000" src="https://github.com/hafsa-bel/Tp-ipcop/assets/73228919/858fbcda-6266-49f4-a00f-3d305251cff2">
</p>

We select this option because we need our Red network interface card to obtain a dynamic IP address from a router or cable modem using DHCP. 
And then we defined a range of ip addresses.

After we finished the installation we access to the ipcop interface throught : **192.168.1.10:8443**

<p align="center">
  <img width="1000" src="https://github.com/hafsa-bel/Tp-ipcop/assets/73228919/7b535aeb-fc69-4dbf-a981-3980662548b6">
</p>


## Web Proxy :

In **IPCop**, a web proxy refers to a component or feature that acts as an intermediary between clients (such as web browsers) and web servers. It facilitates the retrieval of web content by clients by caching and managing web requests and responses.

The initial line within the Settings box indicates the current status of the proxy server, indicating whether it is currently stopped or running.

<p align="center">
  <img width="1000" src="https://github.com/hafsa-bel/Tp-ipcop/assets/73228919/20e2d3ae-a0c3-4127-97bb-c3c839e245fd">
</p>

In here we banned the ip address

<p align="center">
  <img width="1000" src="https://github.com/hafsa-bel/Tp-ipcop/assets/73228919/86e096c2-c019-48bc-935d-42dbeea76899">
</p>

And here's the result:
<p align="center">
  <img width="1000" src="https://github.com/hafsa-bel/Tp-ipcop/assets/73228919/c556441a-7aa2-4357-ade2-c8f21e147f30">
</p>

## URL Filtering:

The **URL filter** in IPCop enhances its capabilities by allowing the blocking of unwanted domains, URLs, and files. This feature utilizes the widely recognized squidGuard redirector. The graphical user interface of the URL filter provides access to all necessary settings, including squidGuard-compatible blacklists, as well as constraints based on time, category, and clients.

The initial line within the Settings box indicates the current status of the filter service, indicating whether it is currently stopped or running.

<p align="center">
  <img width="1000" src="https://github.com/hafsa-bel/Tp-ipcop/assets/73228919/a1010b24-6ab1-43ea-9ac2-3eb53401dcaf">
</p>

Before we blocked the domain names we can see that we can access the pages.

<p align="center">
  <img width="500" src="https://github.com/hafsa-bel/Tp-ipcop/assets/73228919/54a8d742-1396-41e4-a893-5c7478b74997">
 <img width="500" src="https://github.com/hafsa-bel/Tp-ipcop/assets/73228919/c7492237-689c-446e-b939-ffcc45120993)">
</p>

After we blocked the domain names here's the result:

<p align="center">
  <img width="500" src="https://github.com/hafsa-bel/Tp-ipcop/assets/73228919/dcf2920a-cfe2-4b39-ab05-2795f56ae2f2">
 <img width="500" src="https://github.com/hafsa-bel/Tp-ipcop/assets/73228919/d1a9ab24-2fa4-44f5-923a-35b247b95d82">
</p>

## Firewall Rules :

- The **Outgoing Traffic** section in IPCop allows you to control the traffic flowing from internal networks to the external network (RED = Internet). If the policy is set to "half-open" or "closed," you need to create rules to explicitly allow the outgoing traffic you want. By default, outgoing traffic may be restricted or blocked, and the rules you create will determine which types of traffic are permitted from your internal networks to the Internet.

- Regarding **IPCop access**, it is necessary to control traffic from internal networks to IPCop itself. If the policy is set to 'closed,' you will need to create rules for each IPCop service you want to use, including services like DHCP, DNS, and Time.

In the case of avoiding logging Netbios Services on the Green Network, you can add a rule in the IPCop Access section.

- To control traffic between internal networks, such as creating a pinhole between Orange and Green networks, you can use the **Internal Traffic** section. Please note that this section is visible only if you have a Blue and/or Orange interface.

- **Port Forwarding** is a special feature that allows you to forward traffic from the external network (RED, Internet) to an internal network. In this case, the source interface is always Red, while the destination is divided into an 'intermediate' destination, which can be IPCop's external address or alias address, and a 'final' destination, referring to the internal server that needs to be accessible from the outside.

- Lastly, the **External IPCop Access** section is used to control traffic from the Red interface to IPCop. This allows you to define rules and restrictions for incoming traffic from the external network to IPCop itself.

In this case, we defined a rule that accept http request from the green to orange

<p align="center">
  <img width="1000" src="https://github.com/hafsa-bel/Tp-ipcop/assets/73228919/23ff4cdb-de0f-418c-b2b3-d61019ffa292">
</p>

We set up an apache server in our DMZ zone and after we tested in the local machine it worked:
<p align="center">
  <img width="1000" src="https://github.com/hafsa-bel/Tp-ipcop/assets/73228919/51e34d27-0020-45ec-bad4-22d01e496089">
</p>

After that we defined a rule that deny http request again, but this time we have an error message that we cannot access to the web page.

<p align="center">
  <img width="1000" src="https://github.com/hafsa-bel/Tp-ipcop/assets/73228919/81d099dc-d979-46bb-a257-c26604f7924c">
</p>

# Conclusion : 

In conclusion, IPCop is a powerful open-source firewall distribution based on Linux Netfilter/IPtables. It provides robust network security, traffic control, and monitoring capabilities for small to medium-sized businesses and home networks. With its user-friendly web interface, IPCop offers a comprehensive set of features, including firewall rules, web proxy, URL filtering, NAT, and port forwarding.

By implementing IPCop, organizations can effectively protect their networks from external threats, control access to websites and services, optimize bandwidth usage, and monitor network traffic. IPCop's modular architecture allows for easy customization and expansion, making it a flexible solution for network security.

Overall, IPCop provides a reliable and cost-effective solution for enhancing network security, ensuring data protection, and enabling efficient network management. Its extensive range of features and community support make it a popular choice for those seeking a robust and user-friendly firewall solution


