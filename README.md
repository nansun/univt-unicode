
Here is the story.

Many years ago, around 2012 (now it is 2022 when I am writing this down), I was playing with archlinux distribution. I was very happy with many of its features, so I decided to use archlinux as my daily desktop operating system.

I did my best to use console instead of X Window System to enjoy the simplicity and efficiency. However, I noticed that the Linux console didn't support Chinese font display in tty. As a Chinese, I would be very happy to read Chinese directly in tty.

I did some search and research and noticed that youbest (孙海勇) developed a kernel patch univt, which resolved my problem like a charm. I applied the patch onto my linux kernel 3.8.4 with abs (the famous archlinux tool back in 2012 which unfortunately has been deprecated now in 2022). Here I'd like to say thank you for all of his contributions to the Linux community and all the Chinese.

Then I was thinking at that time, that if the code works very well, can I extend the font support from Chinese to all the Unicode characters? Per my further research, I noticed unifont, a unified font supporting all the languages. It's from GNU, meaning I can use it freely.

I converted unifont to glyphs and replaced the static unsigned char font_utf8[2097152] in https://github.com/nansun/univt-unicode/blob/master/before.changed/utf8-kernel-2.6-fonts-3.patch. You can see every single character has a glyph in this file, so I can easily recognize which character it is.

Then I patched my kernel again, and it worked. Now all the languages get a full support in Linux console.

I uploaded this package to ABS and call it univt-unicode, since it became an extended version of univt which supports all the unicode characters.

10 years has passed since then, now it is 2022 and Shanghai is locked down due to the COVID-19 pandemic. Suddenly I recalled this patch, and now I have plenty of time to play with archlinux again. I installed archlinux the latest version, but noticed abs is no longer supported, and the patch I uploaded cannot be found. Fortunately, I fetched a backup copy from my dropbox account.

However, the linux kernel has changed dramatically since then, the code no longer applies to the current kernel 5.18. So, I'm doing search and research again on the internet.

I found cjktty, maintained by @microcai, who was inspired by youbest and contributed his patch to gentoo community. Gentoo is also a good distribution, which goes even further than archlinux into the source compiling. I played with it many years ago, but cannot stand the long time of compilation.

Then I found @zhmars, who forked univt first and then cjktty. I saw my font file was kept and used in kernel version < 4.2. Then the relevant kernel code changed significantly, and the font size changed as well. I'd like to appreciate @zhmars for his update on the later versions of linux kernel, and I am grateful for his contribution to these Chinese console patches.

I can see the latest kernel 5.18 can use 32 x 32 font size, back then it was 16 x 16 when I converted the unifont in 2012. And thanks a lot to @zhmars, who re-convert the latest version of unifont to 32 x 32 glyph and applied it to both univt and cjktty. The idea of extending the font support from cjk to unicode is kept and shared, by a buntch of Chinese people who love linux, console and Chinese.

So I forked his univt patch repository and added this story to README. I'm so proud to be a Chinese with so many lovely buddies.

- Neil Sun, June 5 2022

========================

# Linux-TTY-Patch
Let `/dev/concole` or `/dev/tty*` support ALL UTF-8 charset. 4.20 has change, some languages has problems, also it appear in previous versions. now(v.4.20) it only work to display CJK charset, but you can ues `setfont` form `kbd` package to solve that.
 ## How To Use
 Change to you kernel source directory, and patch this like other patch. 
```
$patch -Np1 < *you want apply core*
$patch -Np1 < *you want apply fonts*
```
  
  In 4.20, you need put font file in fbdev/core dir, don't patch up the fonts patch. And you must enable `8x16` font, cjk font is `16x16(8x8 + 8x8)`. If you want other languages support, tpye `man setfont` to get info. This may batter then change kernel, and the new patch only affects CJK.  
  
  The unicode bitmap fonts file is here:  
    `drivers/video/fbdev/core/fonts_utf8.h`  
  In old version, font file on:  
    `drivers/video/console/fonts_utf8.h`  
  
  ## About
  I edit it make it can use on linux kernel 4.20. And i have't contacted the original author of this patch, this patch is too old. Bat the patch may batter then CJKTTY. It handled separately the wide character from the general character, this make it can custom glyph. CJK font cannot be change yet.
