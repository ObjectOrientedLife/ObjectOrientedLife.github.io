---
title: "MapleStory Global"
excerpt: "As a Gameplay & Engine Programmer at Nexon Korea"
order: 2
categories: 
    - ProfessionalProjects
---

My professional software engineer career began at Nexon Korea. From August 2022 to September 2023, I worked as a **Gameplay & Engine Programmer** for **Global MapleStory**, which was developed and serviced by [Nexon Korea](https://company.nexon.com/kr/). From now on, let me explain the detailed experiences I had there. I hope this short biography helps everyone understand my professional experience in the game industry in depth.

![Logo](../../Images/2023-12-16-NexonKorea/Logo.png){: width="700"}{: .align-center}

# **MapleStory**

MapleStory is a massively multiplayer online role-playing game (MMORPG) renowned for its vibrant 2D side-scrolling graphics and charming pixel art style. Initially developed by the Wizet and published by Nexon Korea, MapleStory takes players on a whimsical journey through the magical realm of Maple World. Players embark on quests, hunt mobs, and raid boss monsters while exploring diverse landscapes through a distinctive 2D platformer environment. 

The game allows for extensive character customization with various classes, skills, and items. With its nostalgic appeal and continuous updates introducing new content, MapleStory has not only maintained a service since its initial release in 2003 but also continuously grown a dedicated player base, currently up to one hundred million players worldwide. 

MapleStory is publishing globally in five regions: South Korea (KMS), Japan (JMS), China (CMS), Taiwan (TMS), South East Asia (MSEA), and Global (GMS, mainly targeting Europe and North America). As the primary service region, most content is initially launched through MapleStory Korea. However, due to the preferences and legal issues that differ by country, each service has its own localized boundary where diverse customizations take place.

![MapleStory](../../Images/2023-12-16-NexonKorea/MapleStory.jpg){: width="600"}

# Responsibility

## Role in General

As a **Gameplay & Engine Programmer** for the live service, I primarily integrated the user client and the servers so that players could have seamless experiences from all aspects of the game. My responsibility was maintaining two remote sides, handling issues from a broad range: stage loading, layer sorting, text encoding, and social features to payment system and user data management.

Even an AAA game service cannot persist merely by standing still. All members of the MapleStory division, including me, always fueled the project periodically with new content for users to immerse themselves. The project has accumulated for two decades without undergoing significant restructuring, its code exceeding millions of lines. Obviously, the project surpasses the capacity of a single programmer to comprehend.

Within this circumstance, a programmer will likely be familiar with a small portion of the code base, while outlining call chains for the other modules is unwieldy. To overcome those difficulties, I developed my own strategy for debugging and analyzing chunks of code: **Guess and Verify**. Employing this approach, I searched for *pivot points* within the code, planting breakpoints relying on inference. Once the breakpoints hit, stages between the entry point and those pivot points are traced backward using a call stack. Those pivot points subsequently become another base camp from which the analysis can proceed a few steps further.

Sustained workload is one of the characteristics exclusive to massive-scaled live services. Updates are scheduled back to back: a major update once a month and erratic but frequent minor patches. These natures inherent to the project mandate that software engineers pass each milestone in a timely manner. I coped with such a tight timeline by ordering tasks by their priority, often consulting other teammates to share solutions, fostering collaboration, and ensuring a collective effort in meeting deadlines.

On the pathway to goals, I worked closely with designers, QA engineers, and overseas publishers who played a key role in directing the game to ensure unparalleled joy. As programmers are the primary contributors to the codebase, cooperating with colleagues from other roles on a technical topic was often challenging. Nevertheless, I successfully bridged this gap by aligning myself with their perspective, fluently clarifying technical terms and concepts in a way that resonated with them.

My ability as a cooperative team player contributed to streamlining the timeline of the entire MapleStory project. Throughout my career at MapleStory team, I consistently sought to extend the boundaries and make substantial contributions to the project. Whenever I was confident of what I believed would bring great improvement, I actively proposed my opinions to colleagues without any hesitation. Through my dedicated efforts, I played a crucial role in my team's winning the title of **Best Team of the Year**.

## Tech Stacks

Because of its long history, the MapleStory project consists of a wide tech stack, some of which is considered a technical debt nowadays. Here are some of those tech stacks publicly stated on their job descriptions looking for software engineers.

- **Visual C++** for the main programming language.
- **Win32** for underlying API
- **DirectX 9** for graphics API 
- **MSSQL** for DBMS
- **Python and C#** for in-house tools

You may not find the names of modern game engines like 'Unreal' or 'Unity' in the list. Instead of relying on commercial game engines, the founding fathers of MapleStory decided to construct the entire game structure from the ground up using C++ and supporting APIs, which was extremely common in the game industry at that time.

In this circumstance, I was among the C++ programmers who had extensively worked with the Win32-styled C++ codebase from earlier times. Even though the architecture was far from being 'modern', it provided me with insights into directly managing lower layers that grant programmers greater control over the hardware.

As the necessity for modernizing the C++ code arose, programmers were required to deeply understand modern C++. For me, this involved adopting the latest features, such as smart pointers for effective memory management, utilizing lambda expressions for expressiveness, implementing iterators to facilitate range-based for loops for a file accessor and modularizing repetitive utility functions with advanced template techniques such as SFINAE. Beyond coding, I actively contributed to shaping a robust coding convention, guiding the code to align with modern C++ standards.

I also made a substantial impact in the database domain. Holding an extensive user base, the database processed an extraordinary volume of requests simultaneously. Recognizing the necessity for efficiency, I engaged deeply in optimizing queries by taking in-house courses about query tuning. I sought knowledge about the overall data structure of a database along with associated concepts such as key, clustering, IO, and various join tactics. The outcome of this effort was a marked improvement in database performance, even in the face of intense real-time request loads.

## Tasks

### Fixing Bugs

A significant portion of the tasks I engaged in stemmed from legacies that composed the codebase. The most common duty was fixing bugs I discovered or reported by QA engineers and designers. The gameplay issues I handled covered every single component of the client and servers (note that the word *server* is pluralized, as multiple servers were taking distinct roles).

The general strategy to address issues began with scrutinizing them in a short time using the aforementioned *guess and verify* tactic. Then, I carefully revised the problematic code, taking caution to potential side effects that my code might introduce even with trivial modifications. I pushed the envelope to render my code as generic as possible so that other software engineers could understand my contribution and append their own seamlessly.

I have never discarded breakpoints placed during the debugging process; instead, I exported those breakpoints in the XML format through the Visual Studio Export Breakpoints feature, reusing them later to shorten the time taken to cope with similar issues. Moreover, I often shared them with teammates to boost the debugging process of the entire project.

### Dealing With Challenging Issues

Whenever I found myself to be having a tedious day, I used to encounter challenging issues that were extremely tricky to figure out their root causes, reproduce, or even figure out what was wrong with them. This kind of issue usually had one or more of these characteristics.

1. Concurrency issues (deadlock, race condition, ...)
2. Dependent on hardware or system
3. Lacking debug info
4. Non-reproducible

Server crashes usually satisfy the condition one and two. Servers are inherently multithreaded; one thread corresponds to a client. Multithreading allows the server to accept multiple requests simultaneously. This is evidently a huge leap over single-threaded applications, but it comes at a cost: concurrency issues.

Deadlocks were a very common issue on servers. Addressing deadlocks primarily involved analyzing crash dumps containing the context where the deadlock had occurred. I first identified which two threads had been holding the same resources with the [Visual Studio *Parallel Stack*](https://learn.microsoft.com/en-us/visualstudio/debugger/using-the-parallel-stacks-window?view=vs-2022). If they had been doing so in the reverse order, waiting for each other to release the other mutex, the deadlock was successfully identified. Subsequently, to resolve the deadlock, I rearranged the mutexes according to the priority of resources in the source code.

![ParallelStack](../../Images/2023-12-16-NexonKorea/ParallelStack.png){: width="700"}{: .align-center} Viewing multiple threads in Visual Studio Parallel Stack
{: .text-center}

Race conditions were less evident than deadlocks. Actually, it was the very last case I would attribute to whenever I encountered a server crash, as finding clues was almost impossible. They were 'guessed' rather than 'detected' in situations where a single-threaded process would not end up. One instance of race condition was multiple threads' acquiring iterators to the same file. I doubted it as a race condition because where one of the pointers turned out to be nullified right after a null check. I ensured that this was a data race by successfully reproducing the crash of the overly parallelized file handling test. I amended the logic with additional mutexes, verifying that the race condition would not emerge again.

Given the worldwide service of MapleStory, it is not surprising that the project suffered text encoding issues. Texts encoded with [Multi-Byte Character Set (MBCS)](https://en.wikipedia.org/wiki/Variable-width_encoding) to support characters other than the ASCII set(especially Asian characters) often puzzled programmers as it required special treatments, unlike plane [ASCII](https://en.wikipedia.org/wiki/ASCII) strings. I dealt with an issue that arose from erroneously processing MBCS strings on a per-byte basis. The first rectification did not work, as the system encoding server was different from what I expected (case 2 - system-dependent!). After carefully experimenting with different setups, I was able to resolve the issue correctly.

For the purpose of sharing knowledge, I gave a detailed presentation about text encoding schemes in the project, as it was an unrecognized but significant topic. Teammates praised the section as *"dealing with an issue that has been neglected so far, but crucial for stable service"*.

### Crafting Gameplay Contents
The entire MapleStory project is updated with novel content periodically, most of which are seasonal events. One remarkable event out of many seasonal events I developed is **Bugcat Capoo Season 2** for TMS. 

{% include video id="Bxt1FGQ6AS8" provider="youtube" %}

First, I constructed an event dialog with sophisticated behaviors. It consisted of multiple widgets interacting with the event progress. Buttons were designed to enable itself only if the conditions for proceeding were satisfied. Then, the client side was associated with a backend-side logic. The logic stored the status of the quest in the database, handled requests from players, validated the requests to prevent abuse, and then managed daily progress and compensations.

Bugcat Capoo Season 2 employed a structural solution following the **Data-Driven Programming** pattern that I have explained in one of my articles in depth. The code I created executed fundamental operations and relied on external data to determine the actual flow. Instead of translating the design specifications written by cooperating designers, I offered them interfaces to modify the UI layout and adjust server-side parameters without consulting me. This not only gave designers more elaborate control over the conditions but also enhanced the productivity of software engineering with a succinct implementation.

### **Anti-Cheating**

MapleStory, being a massive globally-serviced game, always encountered cheating that would cause frequent headaches for the gaming community and developers. The cheating patterns were as diverse as the number of cheaters, but the root cause of naive validation in most cases. To save players from suffering losses caused by cheaters, the entire project members, including me, took extra care to eliminate abusive behaviors.

The No.1 principle I hold when programming the server-side logic is **"Never Trust What Clients Send"**, as cheaters could have manipulated the packets to make unfair profits. I consistently made an effort to thoroughly verify the authenticity of items sent by users, as the consequences of not double-checking packets were server crashes at least and disturbed in-game economy at worst.

The billing server underwent significant refactoring to eliminate potential cheating threats that could affect profits. I considered all scenarios where a cheater can abuse the purchase process to gain items at no cost. I eliminated such possibilities by establishing a crucial principle that opposes a renowned financial service (BNPL): *pay first, buy later*. By applying this rule, I ensured that items were granted only after the payment had been contracted in any scenario on the billing server. The renewal not only stabilized the billing server but also eventually contributed to promoting the sales of in-game cash items.  

Of course, anti-cheating measures cannot eliminate every single abuse. That is why a logging system is mandatory. At one point, the MapleStory project faced significant abuse issues related to missions. To distinguish cheaters from normal players, I investigated a pile of play logs for the detection of abnormal play patterns. The visualization of aggregated logs showed a clear division between the two groups, significantly contributing to penalizing cheaters.

### **Operations**

During my experience with the MapleStory team, my most exotic contribution was the development of an operation tool. It was a web-based application written in Javascript and C#, with which publishers could directly manipulate user data through an abstract interface. I added several features to help publishers manage the gaming service in a more straightforward way.

For AAA games, evaluating updates is as important as planning them. I used to write queries to extract players' content attending patterns to provide publishers and designers insight into players' preferences. Updates were often followed by user data loss that required direct data manipulation over the database to restore the original copy. Writing SQL commands to compensate for those losses was another duty of mine. 

# **Conclusion**

In the vast world of MapleStory, my responsibility involved all sorts of things that required me to learn the approach of a professional software engineer. The scale of service and the volume of the codebase were unprecedented throughout my lifetime. The experiences not only enriched my understanding of diverse tech stacks but also fortified my problem-solving skills and taught me the importance of operation.

Also, I had various technical experiences exclusive to the AAA project. Tackling rushing bugs was a big part of my daily routine, showing how committed I was to giving users a smooth experience. The server was heavily burdened, frequently facing deadlocks and race conditions due to a substantial player base's high volume of requests. I resolved the issue by counting only on limited debug info, which was challenging but worthwhile for expanding my horizon.

My role in the MapleStory project extended far beyond writing code; it encompassed a holistic commitment to the success of the large-scale service, significantly reducing the number of cheaters causing in-game chaos. I also figured out how crucial it is to log status and analyze things afterward to grasp how the service flows. I learned that the responsibility of a software engineer is not confined to expanding the codebase but stretches to ensuring the sustainability of the application in action.

The invaluable journey of expanding the project was a collective achievement, not accomplished solely by myself. Were it not for the help from talented colleagues, I would not have made it to meaningful milestones. Although it was not a long period, I feel fortunate to have worked as a software engineer for MapleStory at Nexon Korea. 