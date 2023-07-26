---
title: "Infrastructure from Code - Klotho"
categories:
  - Posts
tags:
  - serverless
  - architecture
  - design-patterns
---

I got an email from PERSON NAME (CEO of Klotho) to give Klotho a try. Before I start my review, I should say that I only spent a few hours with Klotho so please take my comments with a grain of salt. I skimmed the getting started guide and developed a proof of concept with Klotho. As I did with my Serverless Cloud PoC, again I used TypeScript and Nodejs this time with ExpressJS. Here is my 2 cents:

What does it bring:

- Seamless integration with Typescript, Nodejs and ExpressJS
- User friendly CLI to help you build and test
- Generates infrastructure architecture diagrams. You can see what is going to happen when you deploy your application.
- User friendly documentation, easy to read and execute
- Great collection of sample apps repository: You can select from a variety of sample apps and start easily
- Klotho API is easy to use and doesn’t interfere with the development. You write your code just like you write a regular express application.
- Supports customisation via auto generated YAMLs. You can tweak the resources that is generated.

What do we lose:

- Klotho uses comment based infrastructure generation. You put comments on top of your functions/methods and depending on those so called “annotations”, Klotho generates a YAML during compilation time with underlying infrastructure operations. That’s a big deal breaker for me because I would argue if Klotho is a IfC tool or not. Comments are comments and should not be used as a means of declaration of logic/infrastructure. For typescript they could use actual annotations but then what are you going to use in vanilla javascript then.
- Because of the nature of Klotho (comment based annotations), you cano not use packagers like WebPack or ESBuild which will remove comments during compile time.
- Only supports Pulumi as its underlying IaaC solution. No Terraform, Cloudformation, CDK, etc. support. This is fine, it is a choice of the team at the end but I believe that using a mainstream IaaC solution would increase the adoption.
- Hard to deploy. You need to use two CLIs, Klotho CLI to build your application, Pulumi CLI to deploy your infrastructure. I don’t know why but you need to create accounts to use both of those CLIs.
- No plugin support. You can not extend current functionality without plugin support.

I hope Klotho gets better adoption from people but I wouldn’t use it for my Typescript projects because of the nature of the comment based annotations. Of course with a good clean code architecture and correct usage separation of concerns principle, you can easily get away with the confusion.
