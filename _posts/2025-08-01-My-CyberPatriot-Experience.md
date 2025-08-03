---
title: My CyberPatriot Experience
description: A reflection on my experience and gained knowledge from 3 years of competing in the United States AFA blue teaming competition, CyberPatriot. 
author: John
date: 2025-08-01 01:00:00 +0800
categories: [Extracurriculars]
tags: [Extracurriculars, Cybersecurity]
media_subpath: '/assets/2025-08-01-My-CyberPatriot-Experience'
---


### Preface

Before I begin, I recognize that there have been previous blog posts and discussions on CyberPatriot from retired competitors, particularly the one by former CyberAegis captain Akshay. However, I hope to take a bit of a different approach in my reflection on the competition. Contrary to some of the other posts, I hope to focus less on my general approach to the competition and instead emphasize my specific experiences and strategies. I competed in CyberPatriot for a relatively short amount of time with a small organization and as such, I hope to provide a bit of a unique perspective on the competition. 

<br />

### My Accalades

First, I would like to establish my credibility to speak on the competition.

For anyone unfamiliar with the CyberPatriot online community, I'm known online as St3wart. I come from the team '1984'. 

I was originally introduced to CyberPatriot during my sophomore year of high school (CP season 15, 2022-2023), and competed through my senior year (CP season 17, 2024-2025). I specialized in Windows security and tackled the Windows boxes for each of the 12 virtual rounds I competed in. In each of my 3 seasons, my team qualified for the Platinum Open division and won the Nevada State Championship. I also made a single trip to the national finals in Washington D.C.

In my final round of competition, CP 17 Platinum Semifinals, my cumulative Windows scores placed 7th in the competition. I am extremely proud of this statistic, as I was tasked with securing both the Windows 11 box and the Windows Server 22 box while also assisting in other challenges. This is a task typically dedicated to 2-3 competitors, rather than a single individual.

|Team ID    |Windows Server 22 Score (x/100)|Windows 11 Score (x/100)       |Total  |
|:---       |:----                          |:----                              |:----  |
|1141       |90                             |79                                 |169    |
|0555       |81                             |77                                 |158    |
|0224       |79                             |62                                 |141    |
|1905       |84                             |55                                 |139    |
|1142       |69                             |66                                 |135    |
|3096       |66                             |69                                 |135    |
|1369 (Me)  |78                             |56                                 |134    |

<br />

### My Journey

#### Obstacles

I competed in CyberPatriot via my high school, Faith Lutheran High School (Las Vegas, NV). Competing with this particular high school was extremely difficult. In my first 2 years of competing, our coach was not employed full time by the school and only came to the school for CyberPatriot meetings. In my final year, we had a science teacher act as a temporary coach. Our team oftentimes had difficulty receiving competition information or basic resources from our coaches. Our club and accomplishments were also never recognized by the school or administration. The program was small, with there being less than 10 kids enrolled in the program during my final year. We had difficulty just getting 5 kids with basic technical skills to fill the roster for a single team. Nonetheless, the goal each year was the same, to make it to the national finals in D.C. However, my unique combination of small program and large goals led to a rather interesting three year journey.


#### CP 15

As I mentioned previously, I was originally introduced to CyberPatriot during my sophomore year of high school. With little technical experience, I was a bit lost. As I talked to some fellow competitors in preparation for the season, I was told that I would be tasked with finding vulnerabilities within images. Me, having absolutely no idea what a virtual machine was, thought that these "images" were in reference to actual graphical images. This led to a rather steep learning curve during my first year. 

After joining the CyberPatriot club, I was told that there was an absence of Windows specialists. In CyberPatriot, there are 3 main areas of competition: Cisco, Linux, and Windows. Our team already had competitors prepared to take on Linux and Cisco, but none for Windows. As such, I decided to fill this role. After my performance in tryouts (the practice rounds and the official round 1), I was selected to be on the pseudo "Varsity" team. 

During CP 15, our team was placed into the Platinum division after our R1/R2 performances. We then won the Nevada State Championships during R3 and moved on to semifinals (R4). Through our performance in semifinals, we were able to secure a spot in the national finals (of which only the top 12 teams from the US & Canada are invited). 

![CP15 Team](/cp15Team.jpg){: width="2964" height="1514" }

![CP15 Team 2](/cp15Team2.jpg){: width="3192" height="1520" }
_My CyberPatriot team at the national finals in Washington D.C_

#### CP 16

In my second season, I entered with a bit more knowledge. However, this year our team suffered from some administrative issues. Most of our team had graduated the year prior. In response, our coach blatantly told our club that he did not want us to work towards making the national finals. He removed our top Linux competitor from the roster and refused to add some of the newer and passionate competitors to the team.

Despite these issues, our team still maintained our position as the top team in the region, being placed in the Platinum division, winning the state championship, and proceeding to semifinals. However, in the semifinals, our team performed extremely poorly. It was the lowest I placed in any round of CyberPatriot. While we had faint dreams of somehow turning the team around and making a second straight national finals appearance, we were unable to come through.

#### CP 17

In my final season, I came back reinvigorated. Over the summer, I developed "St3wart", a collection of security scripts I had designed to semi automate the securing of Windows machines. While St3wart was designed for CyberPatriot, it was configurable to be able to secure almost any enterprise Windows system. This, in combination with a new team, led to a rather strong series of performances. 

However, in the semifinals, our team fell prey to a common mistake many teams in CyberPatriot face. Due to our team having only 2 main competitors, we were overwhelmed in the semifinals and the additional challenges that were introduced during this round. Despite being top 5 in pure image scores, our scores in the other challenges pushed us just out of the top 12, denying us a trip to the national finals, and concluding my 3 year journey. 

<br />


### What I Learned

I would like to share three main points about my growth and learning from this competition:

#### 1. Technical Skills & Experience

As a student who went from not knowing what a VM was to defending against professional red team attacks in Washington D.C in the span of one year, I can confirm with absolute certainty that CyberPatriot is a fantastic way to learn valuable technical skills. 

This is a common point of debate within the competition with competitors arguing that CyberPatriot doesn't teach real world skills. I believe this is argued because these competitors enter the competition with significant preexisting experience in computer science and maybe even cybersecurity. As such, they have little to gain from CyberPatriot.

I will be the first to admit that CyberPatriot does not provide realistic attack scenarios. The idea is that as competitors, we are new technical advisors brought on to evaluate a compromised system. However, I do not believe that searching for arbitrary "prohibited media files" in random system directories constitutes a realistic environment. However, this does not mean that CyberPatriot does not give competitors the opportunity to learn about cybersecurity. While the scenarios they provide may not be entirely accurate, being tasked with managing the policies, users, software, and file systems of enterprise machines is certainly an applicable job skill. 

Now for what I personally learned. The first thing CyberPatriot taught me was how to use a virtual machine. I now use a variety of virtual machines for my various development environments (like the Linux Mint VM I use to manage this website). Other computer science skills I gained include scripting (Powershell, Bash, Python, even C#), application familiarity (how to handle various web servers, databases, mail servers, proxy servers, etc.), and some general knowledge (becoming comfortable with a terminal, networking fundamentals, SSH, etc.). I also learned quite a bit about Windows Security, as I became familiar with the Windows Kernel, The Windows Registry, Policy Management, Windows NTFS, etc. I also learned quite a bit about application security. In each round, there are pieces of critical business software running on each box. This could range from Apache web servers hosting company websites to Active Directory domain controllers managing the entire enterprise's forest. For each of these "critical services", competitors gained points for not just configuring the services, but also finding and remediating specific vulnerabilities within the preexisting configurations of each service. As such, I essentially learned how to pentest these various services as I was tasked with evaluating the security of each system and its services. 

For the "CyberPatriot specific" knowledge, see the [My Windows Strategies](https://www.johndcode.com/posts/My-CyberPatriot-Experience/#my-cyberpatriot-windows-strategies) section.


#### 2. Working w/ a Team

In CyberPatriot, there are 6 members on a team. This includes 5 main competitors and one "sub". The sub is able to enter the competition in replacement of another competitor at any point during the 4 (previously 6) hour competition window. In the Platinum Semifinals round, there are typically 8 challenges:

- 4 Boxes
- 2 Cisco Networking Challenges
- 2 Misc Challenges (Web/Boeing)

This means that 5 competitors have 4 hours to complete 8 challenges. This is quite difficult. It is up to the students to delegate manpower to most effectively score points throughout the 4 hour competition window. Thus, this introduces a particular strategy aspect that is imperative to being successful. 

Now, in a perfect world, students could have Windows specialists, Linux specialists, networking specialists, etc. to perform the various challenges. However, the challenge I face each year and the challenge competitors across the nation face, is that recruiting motivated kids from your school to participate in CyberPatriot is difficult. Coming from a small Christian school with only 300 kids in my grade, this problem worsened. In my final year, this problem was the most apparent, as myself and a freshman student were tasked with completing essentially all 8 challenges. As a result, we could not adequately tackle each challenge. This time crunch became so stressful that we became sloppy, making a critical mistake that led to our team suffering a significant penalty during semifinals. Despite this enormous challenge, we placed 19th in the entire competition (VERY close to nationals, regardless of all those obstacles) and 7th in Windows security (as shown in the table above).

As such, these challenges gave me the absolute best opportunity to learn how to work in a team. In middle and high school, I played various team sports (basketball, football, lacrosse). But I learned more about how to work within a group during 3 years of CyberPatriot than I did in 9 years of playing team sports. In basketball, a single player can take the game winning shot. But in CyberPatriot, 1 competitor can not single-handedly control 5 keyboards. It was up to myself and my teammates to delegate the challenges among ourselves and how to, as a team, prepare for these challenges. Once the challenges for the new season were posted, our team would spend hours deciding how to best tackle semifinals for the year. We then took on a "compete like its semifinals" mantra, applying such a strategy to each round. Even if there were less challenges than there would be during semifinals, we would create our own challenges to fill the gaps, truly treating every round like semifinals. This comradery of collectively strategizing to work towards our goal taught me quite a lot. This level of extreme teamwork taught me so much about working in a group both on competition day itself, but in the countless practices and late nights leading up to each. I collaborated on countless service configurations, scripts, practice challenges, and the aftermentioned strategies almost every day for each of those 3 seasons.

This teaches students how to develop and work in a team environment that mirrors a realistic CS job environment. 

#### 3. How to be Goal Oriented

I consider myself to be a rather goal oriented person. In school, I had particular test scores I wanted to achieve, particular classes I wanted to take, etc. However, these were all in pursuit of a higher, overarching goal, which was to learn and to prepare for college. This hierarchical goal mindset was first introduced to me when I played football. I saw each workout, each practice, each game as me working towards the end goal of a championship. 

I believe the balance between enjoying the present and focusing on goals is imperative to the success of students. CyberPatriot strengthened me in this sense. The structure of the competition is linear. The first two rounds yield scores that divide teams into "tiers" (Platinum, Gold, Silver). The third round determines state awards and advancement to semifinals. Semifinals then determine advancement to nationals. There are steps to the competition. This allowed me to refine my goal oriented mindset. At each step in the competition I was focusing on the current and overarching goal. I was also attempting to apply and test my Windows skills and strategies, allowing me to learn at the moment. 

This balance shaped who I am and my approach to future challenges. 

<br />

### My CyberPatriot Windows Strategies 

Finally, I would like to share my approach to the Windows security aspect of CyberPatriot. I have broken down this explanation into the _vulnerability categories_ that the CyberPatriot office references in their debrief-like release at the conclusion of each round. 

I feel as though it is beyond the scope of this post to describe my entire Windows attack plan, so I have simply linked it [here](https://docs.google.com/document/d/1r-XIc-eUJ3rJI-f0oL4d53lkYbBWCEcIAyly_spQkyo/edit?usp=sharing). I apologize for any odd notes and it may be difficult to follow, but it was made for only my use. I have listed the categories here in the general order in which I tackle them in my attack plan. However, I will note that I do not approach each individual category at a time. I will cover parts of each category at the same time, revisit categories, etc. Once again, see the linked attack plan for more details. 

#### README

In this section, I am going to use the Platinum Semifinals from CP 16 as reference. As such, I have provided images of the README documents from these challenges. Its more of a dump from the photos I have but here:

![README 1](/windowsRM1.jpeg){: width="3024" height="4032" }
![README 2](/windowsRM2.jpeg){: width="3024" height="4032" }
![README 3](/windowsRM3.jpeg){: width="3024" height="4032" }
![README 4](/windowsRM4.jpeg){: width="3024" height="4032" }
![README 5](/windowsRM5.jpeg){: width="3024" height="4032" }
![README 6](/windowsRM6.jpeg){: width="3024" height="4032" }
![README 7](/windowsRM7.jpeg){: width="3024" height="4032" }
![README 8](/windowsRM8.jpeg){: width="3024" height="4032" }
![README 9](/windowsRM9.jpeg){: width="3024" height="4032" }
![README 10](/windowsRM10.jpeg){: width="3024" height="4032" }
![README 11](/windowsRM11.jpeg){: width="3024" height="4032" }
![README 12](/windowsRM12.jpeg){: width="3024" height="4032" }
![README 13](/windowsRM13.jpeg){: width="3024" height="4032" }
![README 14](/windowsRM14.jpeg){: width="3024" height="4032" }
_Windows README from CP-16 Platinum Semifinals_

The CP 16 Server scoring configuration file was also leaked during competition (due to error by organizers). A friend has posted that [here](https://github.com/Dudcom/Advanced-Windows-Hardening-Script-Automation/blob/main/Cyber%20Dump/Random%20Stuff%20form%20my%20team/cpxvi_sf_pg_h_server2022_ScoringResource.xml).

#### Forensics Questions

Forensics Questions are one of the more frustrating parts of the competition. I would love for CyberPatriot to make these more realistic but alas, I have been rather unsatisfied with them. 

In my attack plan, you will see me mention "unrecoverable" and "recoverable" forensics. I use these terms because some forensics can be completed later in the attack plan while some require immediate redress. For example, let's say a forensics question asks competitors to identify a malicious firewall rule (a real example of a question in states CP 16). If I proceed with the attack plan, where several of my scripts may remediate this vulnerability, I would be unable to answer the question because the firewall rule would have been removed. As such, I must identify the answer to the question, gain points for the forensics question, and then remediate the underlying vulnerability. This is an example of an unrecoverable forensics question. On the other hand, let's say a forensics question gives us some pcap file that was recently captured and requires further investigation (another real example). As long as we backup the pcap file, we can always examine this question later. This is recoverable.

The goal of each box, for me, was to get the maximum number of points in the shortest amount of time. Unrecoverable forensics questions require immediate attention for the reasons I outlined above, but I would only attempt forensics questions I believed I could solve rather quickly. Especially in the semifinals, there will be difficult questions. These forensics questions always yield decent points so it's worth the extra effort, but again, you want to score the most amount of points as quickly as possible, so maintain a balance.

I have shared the forensics questions from CP 16 semifinals here:

![Server Forensic 1](/server1.jpeg){: width="3024" height="4032" }
![Server Forensic 2](/server2.jpeg){: width="3024" height="4032" }
![Server Forensic 3](/server3.jpeg){: width="3024" height="4032" }
_Windows Server Forensics Questions from CP-16 Platinum Semifinals_

![Windows Forensic 1](/windows1.jpeg){: width="3024" height="4032" }
![Windows Forensic 2](/windows2.jpeg){: width="3024" height="4032" }
![Windows Forensic 3](/windows3.jpeg){: width="3024" height="4032" }
_Windows Forensics Questions from CP-16 Platinum Semifinals_


#### Application/O.S Updates

I'll keep this short. There are only 3 items I believe are worth mentioning here:

1. I have seen the image creators attempt to spoof the version of the software installed. My strategy is just to backup all configuration files, uninstall the software, and then reinstall it. However, for apps like browsers, clear the configuration files as well. If there was anything maliciously configured, a clean install will take care of it, and the competition scenario will almost never outline anything that requires specific browser configuration.

2. Windows OS updates can take a long time. There are some ways to circumvent this. Downloading the updates to a USB stick beforehand and then installing during the competition or using the Windows Update Powershell module (PSWindowsUpdate) can speed things up quite a bit. 

3. As we can see in the configuration file I've posted above, the scoring engine simply chooses a few random system files and checks the version. If the version is up to date, the update check passes. You could experiment with manually changing the version of system executables, but I never did.

#### User Auditing

This one is also pretty basic. The most complex thing I've ever seen in an image is the image creators creating a user titled "." and then hiding the account by manually changing the permissions of the user's SAM registry key. As such, after my normal auditing, I usually just counted the number of SAM keys and then the number of users in the README (+ system accounts) and made sure they matched. 

I scripted pretty much the entirety of this section but I'll list some specific aspects of user auditing here:

- Remove Unauth Admin Privs
- Remove Unauth Users
- Disable System Accounts
- Setting Secure Pswds For Each Account
- Removing Unauthorized Groups
- Clearing Security Groups (Backup Operators, Device Owners, etc.)
- Enabling Auth User Accounts
- Ensuring Auth User Accounts Not Locked Out
- Ensuring Auth User Accounts Passwords Expire by Default
- Ensuring Auth Users Can Change Pswd
- DC User Vulns (Perms on Computer Accounts, DC User Properties, just look in dsa.msc)


#### Account / Local / Uncat Policies

#### Service Auditing

#### Defensive Countermeasures

#### Prohibited Files / Unwanted Software

#### Malware

#### Application Security
