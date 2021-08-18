# Google Summer of Code 2021 - OWASP-SecureTea Project (Final Submission)

## Table of Contents

- [Overview](#overview)
    - [About me](#about-me)
    - [Project details](#project-details)
    - [Proposed summary](#proposed-summary)
    - [Work done](#work-done)
    - [Over Timeline](#timeline)

- [Screenshots screenscasts and tutorial videos](#screenshots-screenscasts-and-tutorial-videos)

## Overview

### About Me

- **Name:** Shaik Ajmal R
- **Major:** Computer Science & Engineering
- **University:** Vellore Institute of Technology 
- **GitHub:** [@pwned-17](https://github.com/pwned-17)
- **E-mail:** shaikajmal.r2000@gmail.com
- **Project URL:** https://www.github.com/OWASP/SecureTea-Project<br>

### Project details

The OWASP SecureTea Project focuses on providing a one-stop security solution for various devices (personal computers / servers / IoT devices).

Currently the following features are supported:

- [x] Intrusion Detection System
- [x] Firewall
- [x] Web Application Firewall
- [x] AntiVirus
- [x] Server Log Monitor
- [x] System Log Monitor
- [x] Local Web Deface Detection & Prevention System
- [x] Auto Web Server Patcher
- [x] IoT Anonymity checker
- [x] Auto report generation using OSINT
- [x] Notifying suspicious activities using various mediums (Twitter, Telegram, Slack, Gmail, SMS, AWS & more)
- [x] Interactive GUI for ease of setting up
- [x] History Logger
- [x] GUI with authentication for Enterprise networks
- [x] Social Engineering
- [x] Eligibility traces based method for automatic blacklisting of ip addresses



**Organisation:** OWASP Foundation<br>
**Project URL:** https://www.github.com/OWASP/SecureTea-Project<br>
**IRC channel:** https://t.me/joinchat/FCDsOABUOJ2ZCWy1<br>
**Mentor:** Rejah Rehim [(@rejahrehim)](https://github.com/rejahrehim), Ade Yoseman Putra[(@adeyosemanputra)](https://github.com/adeyosemanputra)<br>
**Proposal Title:** Building a Web Application Firewall that uses Machine Learning to Detect anomalies in Web Traffic.<br>
**Tag:** securetea tools<br>

### Proposed Summary 

#### Propsed Summary as per Proposal 

The primary goal of my idea is to implement a WAF which uses Machine Learning to detect anomalies in web traffic.

***The proposed idea***
A Proxy server that helps to intercept the Request made by a web application. Then a set of features are extracted from the request and given to a model which uses a clustered dataset to predict whether the given features lie in the good or bad traffic.

Based on the prediction the request is blocked or passed. I have also decided to include an alert mechanism in cases of an incident.

#### Change in the Implemtation idea
The initial  proposed idea had some minor changes after discussing with the mentors and started to work on the idea of building a WAF with this workflow:

Since the Securtea is a software that is used on the server-side of an application. In order to implement a WAF we need to monitor the traffic that is being sent to the Web Server. This could be done by utilizing the Ngnix 's and Apache's reverse Proxy.
Where we configure the reverse proxy to proxy pass every request to a listening server that is capable of analyzing the traffic. Once the analysis is done it can be passed back to the required server and the response is sent back to the proxy and the proxy would send it back to the client.

TLS Termination: When a client's request hits a Ngnix or Apaches server we would perform TLS termination where we would terminate the SSL and send the request to the WAF server.
When the response arrives back to the proxy the proxy would then Initiate the SSL and encrypt the traffic back to the client.

The Entire Flow of Request
```Request <-----> Reverse Proxy <--------> WAF <--------> Server```

### Work done

**Summary of the work done during the GSoC Phase (I - II):**

- [SSRF Detection Module](https://github.com/OWASP/SecureTea-Project/pull/278):
     - [Installation Bug Fix : Attribute Dist not found](https://github.com/OWASP/SecureTea-Project/pull/278/commits/97f00ec2678c40e1b3c48f0f4e843ae335b53a28)
     - [ Implemented SSRF detection Module for Server Log Monitoring](https://github.com/OWASP/SecureTea-Project/pull/278/commits/bb1fb003b8fc5e0c34477f28f185f5f9d25795d3)
     - [ Addedd UnitTest for SSRF Attack Detection ](https://github.com/OWASP/SecureTea-Project/pull/278/commits/f55ac5ecf03803e4833faa435eba2350a2f46443)
     - [Fix CI/CD Build Error ](https://github.com/OWASP/SecureTea-Project/pull/278/commits/40aa8e4c6bc5bf1ff16ca9ab08aa7bb9211f75d3)
   
     
- [WAF Server/Listener ](https://github.com/OWASP/SecureTea-Project/pull/278):
    - [Implemented WAF server for listening to incoming traffic](https://github.com/OWASP/SecureTea-Project/pull/281/commits/f10e333e99abca3a65e81176a1c33f6c940b9961)
    - [Code Refactor](https://github.com/OWASP/SecureTea-Project/pull/281/commits/439b551e0c160c94abbbf32e4cfebc7611f3ffb8)
    
- [WAF Server and Feature Extractor](https://github.com/OWASP/SecureTea-Project/pull/287)
    - [Added Feature Extraction for Incoming Request](https://github.com/OWASP/SecureTea-Project/pull/287/commits/669f66874da1342e7dcec3d09d312230056d3908)
    - [Improved Server](https://github.com/OWASP/SecureTea-Project/pull/287/commits/bd978f5490a5d3dbef0b80058f484812b2341df6)
    - [Code Refractror](https://github.com/OWASP/SecureTea-Project/pull/287/commits/a79c3f5a79e0958012e31d4a7818452d65c1007c)
    - [Working WAF Implemented](https://github.com/OWASP/SecureTea-Project/pull/287/commits/5a26fb52e53f35a914f126d7d29823f2cb5ee680)
    - WAF was implemented that was able to classify incoming web traffic to be bad or good.
    - Classifier was implemented.
    
    
- [Model Improvement of WAF](https://github.com/OWASP/SecureTea-Project/pull/290)
   <br>
   Very important pull request as it had the first improved model , integrations to secureTea , bug fixes etc.
    - [Adding N-gram based tokenizer for the ML Model](https://github.com/OWASP/SecureTea-Project/pull/290/commits/b5c9debc214e74331c4e5e77bf94305b900e14e3)
    - Trainned model on a new dataset
    - [integrated the WAF with the SecureTea CLI ](https://github.com/OWASP/SecureTea-Project/pull/290/commits/5eb4ef9781dc2b2aa8ece71904fa376b674dfbcb)
    - [Added Logging and Error Fix](https://github.com/OWASP/SecureTea-Project/pull/290/commits/7195ff3f9793e1c029a23fef069873bf8bd06b1f)
    - [WAF firewall was integrated to function with the Server Mode](https://github.com/OWASP/SecureTea-Project/pull/290/commits/5423e1f8c8bfbf75b3619b8f1d9f5751baa830db)
    
- [Sever Mode error Fix and Added WAF to server mode](https://github.com/OWASP/SecureTea-Project/pull/293)
    <br>
    Minor Error Fixes in Server Mode where tackled in this pull request 
     - [Errors](https://github.com/OWASP/SecureTea-Project/pull/293/commits/366b245ab9bb6114d7bb1130520dd7ccc36b2290)
- [Server Improvement and New WAF Model ](https://github.com/OWASP/SecureTea-Project/pull/297)
     <br>
     The asyncio server had some issuses with performance , in order to tackle that introduced uvloop policy. Gathered a New Set of Data to trian the WAF model. 
     - [Improved WAF Server and Added New Model](https://github.com/OWASP/SecureTea-Project/pull/297/commits/ebd9e7239d12c641649c03654ba11549d7d950ff)
- [Modifying WAF to Work with Nginix ](https://github.com/OWASP/SecureTea-Project/pull/305)
- [Added WAF Logger ](https://github.com/OWASP/SecureTea-Project/pull/308)






