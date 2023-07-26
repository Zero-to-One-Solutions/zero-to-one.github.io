---
title: "Infrastructure from Code - Serverless Cloud"
categories:
  - Posts
tags:
  - serverless
  - architecture
  - design-patterns
---

I had the opportunity to get an early access to Serverless Cloud. I skimmed the documentation and developed a proof of concept on it. I used typescript and nodejs with server less cloud api. Here is my honest thoughts about it:

What does it bring:

- Seamless integration with Nodejs and Typescript
- Good integration with ExpressJS and other known Nodejs frameworks
- Easy to build and deploy via their own CLI
- Ability to hot reload of underlying infrastructure. Your changes immediately reflected and deployed.
- Hides all technical details around infrastructure. You just focus on your code.
- User friendly documentation. Easy to read and execute.

What do we lose:

- Does not allow to deploy your own Cloud environment: Serverless Cloud has its own infrastructure which you have to deploy. They have an eject option but I didn’t have access to that.
- Hides the underlying infrastructure completely. This is a double edged sword. It may be good in the beginning but kills the customisation and fine tuning in the long run.
- No plugin support yet. I heard that it will be available soon. Plugin support allows others to customise or add new functionalities to the existing framework which is really valuable in the long run.

I believe that Serverless Cloud is the current state of “Infrastructure from Code”. It checks all the benefits of the concept except deployability to customer’s own cloud provider. If it would be possible to deploy to my own cloud provider under my own account, I would definitely employ it but adopting another IaaS solution on top of a cloud provider does not suit me.
