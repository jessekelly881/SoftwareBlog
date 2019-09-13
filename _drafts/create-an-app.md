---
title: How to start a blog!
layout: posts/default
copyright_year: 2019
tags: [blogging, jekyll, wordpress]
---

npm init -y

npm install parcel --save

*boiler*

parcel build index.html

creates dist folder

npm install -g capacitor (Sudo might be necessary)


npm install --save @capacitor/cli


npx cap init
capacitor.config.json

change
  "webDir": "www"
to

  "webDir": "dist"


yay -S android-studio
export JAVA_HOME=/usr/lib/jvm/java-11-openjdk
