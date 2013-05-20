---
layout: post
title: "Why you should switch to declarative programming"
date: 2013-05-19 12:52
comments: true
categories: 
published: false
---

The time of programming in imperative languages is coming to an end, and declarative languages are the future. 

When applications written in imperative languages grow, the code becomes convoluted. Why? Imperatively programmed applications contain statements such as `if X do Y else do Z`. As `Y` and `Z` contain *invisible* side-effects the correctness of the program relies on some implicit invariant. This invariant has to be maintained by the programmer or else the code will break. Thus each time a new feature is added to an application or a bug is fixed the code for the application gets more complex as keeping the invariant intact becomes harder. After a while the code becomes spaghetti-code and bugs are introduced as the programmer fails to maintain the invariant. This is going to happen despite the best intentions of the programmer to keep things clean. Why is this? 

<!-- more -->

An imperative language is a type of language that tells the computer what to do and in which order. However, most, if not all, applications are nothing but a translation of some business domain into a computer program. In order to get the imperative code the programmer has to translate the business model to a set of imperative instructions, the business logic. The imperative instructions bear little resemblance to the original description of the business model. When the business model changes the imperative counterpart could change entirely but what happens is that programmers make incremental updates to the code. This is done because either they do not see that a more drastic change is necessary or because they are under pressure to deliver results. Over time this leads to bugs and unmaintainable code. Summarized, bugs are introduced because there is a manual translation step between the business model and the program code.

Imagine a system for calculating whether a person should receive a certain allowance. To receive the allowance a person has to meet several criteria such as age > 18 and income < 2400. We can denote this in the following way:


``` ruby
def receives_allowance?(age, income) 
  age > 18 && income < 2400
end
```

There are several remarks to be made for this code. Adding a criteria such as marital status would involve adding a parameter to the function and changing the boolean expression. We could already avoid having to change parameters when we had chosen a parameter of type Person that contains the information about a person. But what if we would introduce time as an aspect in our criteria? We need to change the function again. And what if the age criteria changed? If the programmer erroneously codes something like “age > 18 && age < 18” into the condition we would only find the bug during testing, if we are lucky. Additionally when our criteria become more complex we would like to extract criteria to their own functions. In short, it is easy to make mistakes this way.

A solution to this is to avoid the translation process by using a declarative language. By encoding and thereby recording the business model into a set of declarative statements it becomes easier to spot irregularities in the business logic as the business logic reads more like the description of the business model. In this manner the programmer no longer tells the computer how to perform a computation but rather what the computation should be. This makes it easier to maintain 

However, we take it even to an higher level entirely. By just using the declarative language, such as Haskell or Prolog, you are still using a general-purpose language and are thus lacking domain specific checks. It would be advantageous to devise a Domain Specific Language (DSL) instead. This would be a language specifically geared towards your business domain and can be done easily in a language such as Haskell. Creating a DSL has a great benefit: Because the business domain is written down in code the responsibility of translating the business domain into a program shifts from the programmer to the interpreter of the DSL. This has two benefits: the translation is consolidated to one single point (the interpreter) and can be verified or even proven to be correct, and secondly the programmer cannot make mistakes in the translation of the business logic to imperative code.[todo: reference to belastingdienst toeslagen system] 

A simple DSL embedding the idea of the allowance could like the code below. The interpreter / compiler is able to inspect the separate rules and check whether they would cause a tautology or contradiction.

```
age > 18 ^ income < 2400
```

Because the business-logic is now represented by the DSL it can be written by domain experts instead of the programmers of the application itself. The compiler can provide feedback when something is wrong in the DSL and there is less chance for errors in the implementation of the business logic. Additionally this frees the programmes for implementing better translations of the DSL or other projects saving time and other resources.

To summarise 4 reasons why you should switch to declarative languages:

1. Direct translation of the business model into business logic 
2. Better readability of the business logic
3. Better scalability for the program in terms of functionality
4. Less bugs

And 3 reasons why you should use DSLs to boot:

1. Free up programmers to do important stuff
2. Let the domain-experts handle the business logic
3. It is just awesome
