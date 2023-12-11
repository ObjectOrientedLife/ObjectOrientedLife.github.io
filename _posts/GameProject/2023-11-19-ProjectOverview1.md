---
title: "Indie Game Project: Peninsula (1)"
excerpt: "Overall Introduction About the Project"
order: 0
categories: 
    - GameProject
---

Like many other kids, making a game has always been my dream. Indeed, a game is a fantasy world constructed upon imagination. While playing games, I could do anything I wanted, go anywhere I dreamed of, and meet anyone beyond the barrier. Therefore, it is no wonder that I was determined to become a *game developer* (note that it's not a '*game programmer*', as I was not knowledgeable about the game industry) and create a surprising game one day.

On entering college, I stepped into the world of computer science and fell in love with programming. That programming is one of the few fields that require both logical reasoning and creativity quickly fascinated me, and I was determined by my primary career path as a software engineer. Nonetheless, I have never abandoned the dream of becoming a *game developer* who directs and produces an entire game alone, and that was the only reason I planned to set up my own indie project, **Peninsula**.

Except for a few months in the last year, I have always struggled with the whole development process, including design, programming, art, and even marketing, all by myself. These experiences have been teaching me lessons from various fields, especially in the programming part, as I have been building my career as a software engineer. Before we dive into the main programming section, let me first give a general description of the design vibe of the Peninsula in this article.

# Designing Peninsula

## Project Introduction

**Peninsula** is a top-view mobile shooter set in the Korean war. The development began in 2019. Initially, I dug into the world of Unity, C#, Git, Blender, and numerous other tools and programming languages required for development. 

From the beginning, Peninsula has never been a toy project to show off my skills. I have always aimed at its commercial success. This imposed several challenges on me, as I had to either break through or find an audible workaround. There has hardly been a choice of circumventing the hardships that I encountered. Still, there is a long way to go until I can release this game on the market. Nevertheless, I shall push the envelope to the final destination, dreaming of Peninsula making a phenomenal hit.

 *A picture is worth a thousand words*. Take a look at the trailers!

{% include video id="b9b-6MzOAi0" provider="youtube" %}

{% include video id="zgcS1foEgOA" provider="youtube" %}

# Design

## Basic Concepts

Searching the gaming market, I found out that numerous games are competing with each other. Deciding the direction of a game is always challenging since an indistinctive game will not be able to survive the overheated marketplace. At the same time, people will never appreciate a completely unprecedented game style either. Hence, I tried to balance between two polars: *gameability* and *originality*.

The very first step to take when producing a game is deciding the genre. I came up with a few keywords about the concept of the project. Here are the central components that are still governing the project to this moment. 

- **Military** - The history of mankind is inseparable from the history of war. There have been a myriad of warfare games beloved by players. I am also one of those military game fanboys. I have been totally into military games, from the *Battlefield* series to the later *Company of Heroes* ones. Given my strong passion for military games, it feels entirely natural for me to create one myself.
- **Top View** - I leaned toward directing my project as a top-view shooter. An overhead view can make players feel they possess more control over their units and, ultimately, battlefields.  
- **Real-Time Tactics (RTT)** - A few real-time strategies exist on a mobile platform, including *Company of Heroes* on iPadOS. Yet, RTS games are often deemed less suitable to be played on a mobile phone due to several challenges posed by the platform. To lighten burdens of players, I opted to emphasize more on combat and rule out a few core components consisting of RTS: resource management, unit production, and exhausting strategies. Players are required to manage fewer units but to cherish them and behave *tactically* to achieve victory.
- **Squad** - In actual warfare, combat units rarely act individually unless they really need to. Instead, they belong to a group called *squad*, which in turn consists of larger groups (platoon, company, battalion, and so on). Moreover, most vehicles may be operated by at least a squad of crews rather than a lone individual. Establishing the squad as the smallest unit of control imbues the game more reality and extends the range of tactics.
- **Integrated Battlefield** - The *integrated battlefield* refers to a battleground fought by diverse combat units: infantry, armored vehicles, aircraft, and even fixed structures. I am a big fan of *the Battlefield* series; thus, they inspired and primarily influenced the idea. With the vehicles at hand, players are expected to be proficient in driving and effectively counteracting enemies' vehicles. It will certainly present players with great immersion despite the increased complexity.

## Squad System

The **Squad System** is the pivot point of the gameplay, around which all the other components revolve. It is mandatory that players maneuver their squad with proper tactics so that their troops can occupy superiority over hostile forces. Compared to controlling a single soldier, controlling a complete squad poses new challenges upon players; they squeeze their brains to figure out the best weapons preset within their squad, place each squad member at dominant positions, and continuously alter plans as the squad shrinks during combat.

Players are not the only ones who receive tasks from the squad system, but I am also the one who, whilst I am designing the gameplay. Without a proper interface, it was anticipated that users would feel awkward about the novelty and unfamiliarity of controlling a group of units individually and in an organized manner. I contemplated what the proper control method is.

- Basically, a player 'drives' a squad with a virtual joystick. This makes it easier to steer and place their squad to intended positions even on a relatively small-sized mobile display. Targeting mobile platforms doesn't necessarily put us at a disadvantage in all cases. We can take advantage of a touch display, with which users swipe or tap with multiple fingers, handling the device in a more intuitive way. Moving and rotating units, plus dealing with sight, rely heavily on the features specific to mobile platforms.
- In contrast, the freedom to treat units individually is also guaranteed for users. Some players pursue simplicity, while others are eager for detailed controllability over their teams. **Group system** with which players can combine squad members into groups, where each group behaves as if they are a single unit. 
- Also, players may outfit their squad members with different firearms to the extent resource allows. As a game proceeds, the limits are gradually lifted so that one can suppress enemies with dominant firepower. Organizing one's squad properly with suitable weapons within availability is the best path to triumph.

![Movement](../../Images/2023-11-19-ProjectOverview1/Movement.gif){: width="800"}{: .align-center} Moving and rotating a squad with a virtual joystick
{: .text-center}

## Other Topics

...And there are many other design components. Engagement, for example, is another core content of this project. However, *this margin is too narrow to contain*. Instead, please look forward to upcoming posts which will be introducing a variety of interesting topics related to **Peninsula**. 
