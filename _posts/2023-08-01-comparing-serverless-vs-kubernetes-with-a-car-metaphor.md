---
title: "Comparing Serverless vs Kubernetes with A Car Metaphor"
categories:
  - Posts
tags:
  - serverless
  - architecture
---

After years of going all with serverless, I decided to go one step back and decided to spent some time with Kubernetes. I decided to explain how I felt as a car analogy. I hope you like it.

The difference between being a DevOps engineer in a Serverless ecosystem and a Kubernetes ecosystem was like renting an autonomous car vs buying a semi-autonomous car.
In Serverless, every optional feature is instantly available. You can enable and disable them whenever you need them and depending how many KMs you drove with those features, you pay for only for that amount. At the end of the month, system checks how many KMs you drove and then calculates each feature and how many KMs those features were enabled. Then you pay for them.

## Advantages

- You don’t think about maintenance.
- You don’t think about size, baggage capacity, horsepower, torque, etc. Company checks them for you and change the car without you realising it.
- You don’t need a handyman that can configure the options for you. You can handle them yourself or at least you should be.

## Disadvantages

- You should be aware of how many KMs you drive.
- If you are driving a lot, you may want to consider renting a car and a good maintenance guy. They will cost less in the long run.

In Kubernetes you first plan all the features you are going to need, then select a car that allows you to fit all those features. You only pay your monthly car rent. You can use as much as you want without thinking about how many KMs you drove. You can enable / disable any feature you want and it doesn’t matter. You still have to pay the same amount. In case you realize that you don’t need a car that big or maybe that car is too small for your needs, you can change it but again you have to plan and configure everything yourself.
