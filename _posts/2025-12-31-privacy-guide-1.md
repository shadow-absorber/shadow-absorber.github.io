---
title: "Digital minimalism: Remove Accounts"
date:  2025-12-31T10:39:21UTC
categories:
  - Privacy
  - Security
tags:
  - Privacy
  - Security
  - Scripts
---

# Digital Minimalism: Remove Accounts

Ello again and Welcome to the series on Privacy and Security!!!

Today shadow is gonna go over some tips and tricks to remove old accounts.

## Why should i remove accounts?
Every account you leave out there links some information back to you.
For example your password if you reuse it can cause problems if there is a data leak
or you used your real name or picture on some site and some person using OSINT finds info about you.

By removing old accounts they are no longer a security or privacy risk as the data is deleted in nearly all instances!
Another option if you are not ready to delete the accounts is to add them to your password manager and keeping the password more complex and hidden!!

## How do i find old accounts that i don't use?
The easiest way would be to check your email( assuming you did not clean out old email which might be a big assumption! ).
So start searching your email using the following search terms:
* "Welcome to"
* "Verify your email"
* "Reset your password"
* "Confirm your account"

Alternatively if that does not find anything you can use the command line tool called [sherlock](https://github.com/sherlock-project/sherlock).

You can easily install sherlock using:
```bash
pipx sherlock
```
and then run it using:
```bash
sherlock your-username-here
```

> [!Warning]
> this will show sites where your username is in use( with some false positives so be sure to check the links ).
> Make sure you own the accounts and it is not someone else with a similar or same username as you!!!

If you find some old accounts using these that you don't want to keep check the next section for how to delete the accounts.

## Delete unused accounts!
Next step would be to delete accounts you no longer need or use.
The easiest way to achieve this would be to check the website:
[https://justdeleteme.xyz/](https://justdeleteme.xyz/)

Search up the site or service you are trying to remove your account from on justdeleteme and then follow the explanation!

## Feel happy and accomplished
After following this guide feel relieved that you now have less exposed accounts out there!


## SHADOW OUT
And that has been the first part of the privacy and security journey, tomorrow we are gonna tackle password managers for the accounts that are left after this!

Enjoy
And shadow is now out!
