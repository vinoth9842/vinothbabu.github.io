---
layout: post
title: Install Plugins for Vim
author: Rangsiman Ketkaew
date: "2019-07-27 23:26:00 +0700"
category:
  - Vi-Vim
  - text-editor
summary: How to install plugins for Vim editor
thumbnail: posts/vim-logo.png
permalink: content/7
comments: true
---

## เกริ่นนำ

สวัสดีครับ ผมเชื่อว่าหลาย ๆ คนที่ใช้งาน Linux หรือ macOS หรือระบบปฏิบัติการ (OS) อะไรก็แล้วแต่ที่ต้อง deal กับ command-line จะต้องรู้จักโปรแกรมแก้ไขอักษร (text editor) ที่ชื่อว่า Vim อย่างแน่นอน นั่นก็เพราะความสามารถที่โดดเด่นซึ่งสามารถช่วยให้เราแก้ไขไฟล์ได้อย่างรวดเร็ว โพสต์นี้ผมจะอธิบายวิธีการติดตั้งโปรแกรมเสริม (extension) หรือปลั๊กอิน (plugin) ให้กับ Vim ซึ่งผมก็จะแสดงตัวอย่างการติดตั้งปลั๊กอินยอดฮิต NERDTree ด้วยครับ

<br>

<img 
  src="/assets/img/posts/vim-help.png" 
  alt="vim-help" 
  width="100%" 
  height="auto" 
/>

<br>

## สารบัญ

- [เกริ่นนำ](#เกริ่นนำ)
- [สารบัญ](#สารบัญ)
- [ระบบที่ผมใช้](#ระบบที่ผมใช้)
- [ติดตั้ง Plug](#ติดตั้ง-plug)
- [ติดตั้งปลั๊กอินเสริมอื่น ๆ ผ่าน Plug](#ติดตั้งปลั๊กอินเสริมอื่น-ๆ-ผ่าน-plug)
- [ทดสอบปลั๊กอิน](#ทดสอบปลั๊กอิน)
- [ควบคุมปลั๊กอินใน vim](#ควบคุมปลั๊กอินใน-vim)
- [คำสั่งอื่น ๆ ที่อาจจะมีประโยชน์](#คำสั่งอื่น-ๆ-ที่อาจจะมีประโยชน์)

<br>

## ระบบที่ผมใช้

- Windows Linux Subsystem (WLS)
- Ubuntu: Version: 18.04.2 LTS (Bionic Beaver)
- Vim editor (vim-gnome)
```
VIM - Vi IMproved 8.0 (2016 Sep 12, compiled Jun 06 2019 17:31:41)
Included patches: 1-1453
Modified by pkg-vim-maintainers@lists.alioth.debian.org
Compiled by pkg-vim-maintainers@lists.alioth.debian.org
```

<br>

## ติดตั้ง Plug

ไลบรารี่สำหรับการจัดการปลั๊กอิน (plugin manager) ที่ผมพบว่าสามารถติดตั้งปลั๊กอินเสริมสำหรับ Vim ได้แบบไม่ยุ่งยากชีวิตมากนักก็คือ [Plug](https://github.com/junegunn/vim-plug) ซึ่งสามารถดาวน์โหลดใช้งานได้ฟรี

1. เปิด terminal

2. ดาวน์โหลด source code ของ Plug มาที่เครื่องของเรา
```sh
curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```

1. เปิดไฟล์ ~/.vimrc
```sh
vi ~/.vimrc
```

1. เพิ่มคำสั่งเพื่อเรียกใช้งาน plugin หรือ extension ที่ต้องการ ซึ่งคำสั่งจะขึ้นต้นด้วยคีเวิร์ด **Plug** ดังตัวอย่างต่อไปนี้
```
Plug 'junegunn/vim-easy-align'
```
---
ตัวอย่างไฟล์ .vimrc ของผมครับ
<script src="https://gist.github.com/rangsimanketkaew/ac5e705540fd1feeeda5866e32073deb.js"></script>

1. อัพเดทการตั้งค่าของไฟล์ .vimrc โดยการ activate ไฟล์ด้วยคำสั่งต่อไป
```sh
source ~/.vimrc
```

1. เปิด vim แล้วเข้า Normal Mode โดยกดปุ่ม **Esc** และกด **shift** + **;**
   (สังเกตว่าด้านล่างซ้ายของหน้าต่าง vim จะปรากฎ **:** ขึ้นมา)
```sh
vi
```

1. รันคำสั่งต่อไปนี้เพื่อติดตั้ง plugin ทั้งหมดที่ระบุในไฟล์ .vimrc ด้วย plug แล้ว Enter
```
:PlugInstall
```

1. รอสักครู่จนกระทั่งการติดตั้งเสร็จเรียบร้อย หากต้องการตรวจสอบสถานะของ Plug และปลั๊กอินอื่น ๆ สามารถทำได้โดยรันคำสั่งต่อไปนี้
```
:PlugStatus
```

<br>

## ติดตั้งปลั๊กอินเสริมอื่น ๆ ผ่าน Plug

หากเราต้องการติดตั้ปลั๊กอินตัวอื่น ๆ อีก สามารถทำได้โดยการเพิ่ม Plug command สำหรับปลั๊กอินนั้น ๆ ในไฟล์ .vimrc ซึ่ง Plug command สามารถเช็คได้จากเว็บไซต์ [https://vimawesome.com/](https://vimawesome.com/) ซึ่งเปรียบเสมือน server ของ ปลั๊กอินสำหรับ vim นั่นเอง

<img 
  src="/assets/img/posts/vim-awesome-screenshot.png" 
  alt="vim-awesome-screenshot" 
  width="100%" 
  height="auto" 
/>

<br>

เช่น ผมต้องการติดตั้งปลั๊กอิน python-mode สามารถทำได้ดังนี้

1. เพิ่มคำสั่งต่อไปนี้เข้าไปยังไฟล์ .vimrc
```
Plug 'klen/python-mode'
```

2. เปิด vim แล้วรันคำสั่งต่อไปนี้ใน Normal Mode
```
:source %
:PlugInstall
```

3. รอสักครู่จนการติดตั้งจะเสร็จสมบูรณ์
<img 
  src="/assets/img/posts/install-python-plugin-vim.png" 
  alt="install-python-plugin-vim" 
  width="100%" 
  height="auto" 
/>

<br>

## ทดสอบปลั๊กอิน

หลังจากติดตั้งปลั๊กอินเสร็จเรียบร้อยแล้ว การเรียกใช้งานปลั๊กอินตัวละตัวนั้นก็จะแตกต่างกันไป ผมจะลองยกตัวอย่างการใช้งานปลั๊กอินที่ชื่อว่า NERDTree ซึ่งเป็นปลั๊กอินเสริมแบบ File explorer

การเรียกใช้งาน NERDTree ทำได้ดังต่อไปนี้

1. เปิด vim
```
vi
```

2. เข้า Normal Mode และรันคำสั่งต่อไปนี้
```
:NERDTree
```

3. เมื่อ NERDTree ทำงาน จะปรากฎหน้าต่าง File/Folder explorer ขึ้นมาทางด้านซ้าย ซึ่งจะเป็นการแสดงไฟล์และแฟ้มข้อมูลแบบ tree นั่นเอง ซึ่งปลั๊กอินตัวนี้มีประโยชน์อย่างมากในการทำงานที่ต้องมีการแก้ไขหลาย ๆ ไฟล์พร้อมกัน
<img 
  src="/assets/img/posts/vi-nerdtree-test.png" 
  alt="vi-nerdtree-test" 
  width="100%" 
  height="auto" 
/>

<br>

## ควบคุมปลั๊กอินใน vim

หากเราต้องการให้ vim เรียกใช้งานปลั๊กอินที่เราต้องการแบบอัตโนมัติทุกครั้งที่เราเปิด vim สามารถทำได้โดยการเพิ่มคำสั่งดังต่อไปนี้เข้าไปในไฟล์ .vimrc

```
autocmd VimEnter * NERDTree
```

และหากเราต้องการให้ cursor อยู่ที่ Editor windows ทุกครั้ง สามารถทำได้โดยใช้คำสั่งต่อไปนี้

```
autocmd VimEnter * wincmd p
```

<br/>

## คำสั่งอื่น ๆ ที่อาจจะมีประโยชน์

- อัพเดทปลั๊กอิน
```
:PlugUpdate
```

- อัพเกรด Plug
```
:PlugUpgrade
```
