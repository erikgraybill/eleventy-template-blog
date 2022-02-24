---
title: An Introduction to Open Web Components
description: This is a post explaining how to install the required materials to start using Open Web Components.
date: 2022-02-24
tags:
  - Open Web Components
  - JavaScript
layout: layouts/post.njk
---

JavaScript is used widely across the internet, as it is natively run in your web browser. As a web developer, familiarizing yourself with JavaScript is vital to success. Open-wc streamlines aspects of development and utilizes Node.js and npm. From the open-wc Git Repository's README: "Open Web Components provides a set of defaults, recommendations and tools to help facilitate your web component project."

What do Node.js and npm have to do with JavaScript? Node.js is a cross-platform JavaScript run-time environment that executes JavaScript code outside of a browser. The Node Package Manager, or npm, is a software registry of over 800,000 packages installed alongside Node.js according to w3schools. Node.js is one of the most popular tools for open-source developers to work with JavaScript. In this article, I will walk through the steps required to start using open-wc on a Windows machine.

## Getting Started
First things first, you will need an IDE to work with JavaScript. You may use any IDE you are comfortable with if it is compatible with JavaScript, but I will be using Visual Studio Code which can be downloaded [here](https://code.visualstudio.com/).

## Installing Node.js and npm

![Download page](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/qkk0ponf32aod6a3gqwl.png)
To install Node.js, go [here](https://nodejs.org/en/download/). Get the most current LTS version for your operating system for the best stability, or the latest current version for new features at the cost of some stability. Since npm is included with the Node.js install, you should now have both; open your terminal and enter `node -v` to check if Node.js was installed, and `npm -v` to check if npm was installed. You're all set to continue if you see version numbers after running those commands.

![Check if Node.js and npm are installed](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ivrqvddmt4b436pqlh5u.png)

## Starting a new open-wc project
To begin with open-wc, make a directory to put your project in. Change your terminal directory to this new location, and enter `npm init @open-wc`. If everything has been installed correctly, this should run and you can now begin working on your open-wc project. I initialized my project with these options:

- New project scaffold
- Web component
- Linting, Testing, and Demoing enabled
- No TypeScript
- Install using npm

![open-wc initialization](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/045vzmnqn7t8awe2qwo5.png)

The hello-world element is located in the `/src/` folder to be edited further. And with that, you have just created your first web component!