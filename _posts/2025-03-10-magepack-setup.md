---
title: Magepack Setup on Imac
author: Bhavesh Prajapati
date: 2025-03-10
category: Jekyll
layout: post
mermaid: true
---

Install and use magepack with magento

```bash
brew uninstall node

# Setup NVM
brew --prefix nvm
nano ~/.zshrc
export NVM_DIR="$HOME/.nvm"
[ -s "/usr/local/opt/nvm/nvm.sh" ] && \. "/usr/local/opt/nvm/nvm.sh"
source ~/.zshrc
nvm --version

# Install Node and NVM
nvm install 16.20.0
nvm use 16.20.0
node -v
npm -v

# Install magepack globally
npm install -g magepack
magepack -v

# Run this at magento root
npm install --save magepack

rm magepack.config.js

magepack generate --cms-url="https://bhavesh-lumalume.px.seepossible.link/" --category-url="https://bhavesh-lumalume.px.seepossible.link/jewelry.html" --product-url="https://bhavesh-lumalume.px.seepossible.link/rg0032-rd-150-18-rs-rg0032-rd-150-18-rs.html"

php excludeJsInBundle.php magepack.config.js excludeJsInBundle.txt

# upload generated magepack.config.js file to the your server then run

fulldeploy
 
# after successfull deployment run

magepack bundle --config magepack.config.js
```
