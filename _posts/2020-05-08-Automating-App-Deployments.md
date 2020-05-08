---
layout: post
author: Jett
published: true
title: Automating Intune App Deployments with Power Automate
date: 2020-05-08 21:53:00 +0800
categories: [howto, automation, microsoft]
---

I've recently been working a lot with Microsoft's Power Automate platform, which I've actually found quite an enjoyable experience. It's quite nice to still have that feeling of being relatively close to the code (by being able to preview the JSON that builds each element) while also being able to test and assemble everything super efficiently.

So, to get to the task at hand, I was brought an issue which was to automatically push an app to phones after a consent form was filled in. While the task description was initially daunting, I quickly found out that it was vastly easier than I had imagined.

# Setup

Getting ready for this is super simple, all you need is the correct license for Power Automate, an Intune deployment and an Azure AD environment. You'll also need to create an Azure AD group for the users that have signed the form, keep a note of the Group ID, we'll come back to that later.

The final bit of setup is to find the app in Intune, edit the assignments and add the group you've just created into the required section.

# The Flow

To get started, we'll create a new automated flow and select "When a new response is submitted" - Microsoft Forms for the trigger then select the appropriate form.

Next up, we'll grab the response details with the "Get response details" action, which we'll pass the form we selected earlier and then add the dynamic content "responseId".

Now we'll have an optional step, which is using the form response to decide whether to push the app or not, for this we'll use a condition block and then enter the appropriate logic for your form.


Now we add the last bits which is using the Azure AD "Get User" block to pull the User ID from the Responders Email and then use "Add User to Group" to add the user ID we just retrieved to the group ID I mentioned to save previously.

