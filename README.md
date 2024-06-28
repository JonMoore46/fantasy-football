# fantasy-football
This document outlines why I want to use the premise of a fantasy football site for my side project as part of my architectural learning.

## Overview
The offical Premier Legage Fantasy Football game - https://fantasy.premierleague.com attracts over 10million sign ups every year and is open to users worldwide.

The general premise is users have a budget of £100million to select a squad of 15 players. Each player is given a price based on a number of factors including how good they are and how good the team they play for is.

The best players can be worth up-to £15million while the worst players are typically around £4million.

The Fantasy Football game is played over a season, which consists of 38 rounds of matches. Each round is refered to as a gameweek and all matches for a gameweek are typically played over a weekend. But its possible to have gameweek 2 finisihing on a Sunday and gameweek3 begining on a Tuesday.

Users can select 11 of thier 15 players to be eligiable to earn points each gameweek.

Points are awareded to players based thier performance e.g scores they score, if their Premier League team doesn't conceded any goals etc.........

Players can also be awarded an additioanl 3,2 or 1 point(s) for a gameweek based on their overall performance.

The winner is the user whose sqaud of 15 players has the most total points at the end of the season, when all 38 gameweeks have been completed.

You can read more detailed information on rules and how everythng works here - https://fantasy.premierleague.com/help

The deadline for users to finalise thier squad of 11 players for each gameweek is 1hour 30minutes before the first match of a gameweek. 

But Premier League teams don't officaly announce who is playing for them each gameweek until 1hour before the match starts. So 30minutes after users have to finalise their squads.

## Why my interest
Having been a user for the past 3 years, there are two/three main aspects that I have wondered about architecualry with this game.

### Premier League Team leaks
There is an active Twitter (X) community, probably several 100,000 users at least, that share ideas and discuss the game. Some of these people are luckily enough to get information (leaks) about which players are starting for premier league teams for a particular gameweek before the deadline for users to finalise thier squads.

This informaiton is posted on Twitter and if one of the players confirmed as playing or not is a popular player, then all engeaged users on social media will try and access the site or app to add or remove this player to/from thier squads at roughly the same time. This has often caused the site and app to crash or become unsuable.

I have always wondered if its possible to design an architecure and associated apps and services to handle this volumne of users that means the site doesn't crash when this happens.

### Site is taken offline
Once the deadline for users to finalise thier squad is reached, the site is taken offline for around an hour. Once the site is accessible again, users can see a view of their players for the current gameweek and can start selecting their players for the next gameweek.

I have wondered if there is a need to take the site offline or, even though there is 10million squads, any data processing can happen in the background whilst the site is still accessible.

### Bonus points are not assigned straight away.
The offical Fantsay Football site does not assign the 3,2 and 1 bonus points until a couple of hourse after the gameweek has finished. Yet other sites such as https://www.livefpl.net and https://fpl.team/ are able to assign bonus points in realtime.

So I have wondered why the offical site doesn't assign these points in real time?

## Critera
Below are headings for some rough criteria that has been set before and how these project meets each aspect.

But I'm aware the criteria is still to be finalised.

### UI component
There will need to be a UI component for users and potentially an admin UI to set players and prices for users to pick from etc.....

### Server side components - therefore infrastructure needs to be considered
There will be at least one server side component to handle request from the UI component(s)

### Data storage - therefore databases need to be considered, hosted and integrated with
Data will need to be stored for players, users, user squads etc...

### Interaction with a third part API
Will need to integrate with a third party api e.g https://www.api-football.com/ to get data required to calcualte points - (Potential for cost considerations around getting the data realtime depending on API and assocaited pricing)

### Potential for considering development and deployment pipelines.
Will need to deploy at least one app and service

### The need for logging (e.g. DataDog) and monitoring
Will need to monitor for spikes in traffic, issues logging in etc......
