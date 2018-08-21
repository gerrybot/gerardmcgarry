---
title: 'Handling pseudo selectors like :hover in SASS'
date: Tue, 04 Feb 2014 11:14:42 +0000
draft: false
tags: [CSS, SASS, Web Design]
---

SASS is an amazing CSS preprocessor that allows you to rapidly code websites using nested rules and variables and a lot more. However, one thing the basic SASS instructions won't tell you about is how to handle pseudo selectors when you're nesting your rules. I'm talking about :hover, :before, :after and :visited states. Do you create a whole new CSS rule for a pseudo selector, or is there a way to nest them? Well, you'll be pleased to know that it's actually quite easy to nest pseudo selectors in SASS - with the help of our friend, the ampersand: & Ordinarily, your code for a hover effect would look like this:

    .box {
        border: 1px solid #000;
        background: #f5f5f5;
    }
    .box:hover {
        background: #f5f5f5;
    }
    

But with SASS, you simply use the ampersand (&) to reference the parent selector. Like this:

    .box {
        border: 1px solid #000;
        background: #f5f5f5;
        &:hover {
            background: #f3f3f3;
        }
    }
    

From there, you can chain and nest other rules. It's easy. Do you have any other SASS tips that you want to share with the class? Let me know in the comments.