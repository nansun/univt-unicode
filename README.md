
Here is the story.

故事是这样的。

Many years ago, around 2012 (now it is 2022 when I am writing this down), I was playing with archlinux distribution. I was very happy with many of its features, so I decided to use archlinux as my daily desktop operating system.

多年以前，大概2012年前后（当我写下此文时是2022年），我那时候在玩archlinux发行版。我特别喜欢里面的一些特性，于是就决定要用archlinux作为我日常使用的操作系统。

I did my best to use console instead of X Window System to enjoy the simplicity and efficiency. However, I noticed that the Linux console didn't support Chinese font display in tty. As a Chinese, I would be very happy to read Chinese directly in tty.

我尽量用控制台而不用X Window，因为它简单、高效。但我发现，Linux控制台不支持中文字体显示。作为中国人，我肯定希望能在控制台里直接显示中文。

I did some search and research and noticed that youbest (孙海勇) developed a kernel patch univt, which resolved my problem like a charm. I applied the patch onto my linux kernel 3.8.4 with abs (the famous archlinux tool back in 2012 which unfortunately has been deprecated now in 2022). Here I'd like to say thank you for all of his contributions to the Linux community and all the Chinese.

我在网上搜了搜，也做了些研究，发现youbest（孙海勇）做了个内核补丁叫univt，很好地解决了我碰到的问题。于是我用abs给3.8.4的Linux内核打了补丁（abs在当时是archlinux里面很有名的一个工具，可惜现在的2022年却已经退休了）。在此感谢孙海勇对整个Linux社群和中国用户所做出的贡献。

Then I was thinking at that time, that if the code works very well, can I extend the font support from Chinese to all the Unicode characters? Per my further research, I noticed unifont, a unified font supporting all the languages. It's from GNU, meaning I can use it freely.

那时候我就想，如果代码可以正常运作，那我是不是可以把对字体的支持从中日韩扩展到unicode呢？我又做了些研究，找到了unifont，它可以用一种字体支持所有的语言。更重要的是，它源自于GNU，我可以自由地使用它。

I converted unifont to glyphs and replaced the static unsigned char font_utf8[2097152] in https://github.com/nansun/univt-unicode/blob/master/before.changed/utf8-kernel-2.6-fonts-3.patch. You can see every single character has a glyph in this file, so I can easily recognize which character it is.

于是我把unifont字体转化为字形，并替换了https://github.com/nansun/univt-unicode/blob/master/before.changed/utf8-kernel-2.6-fonts-3.patch 里面的静态字符数组 static unsigned char font_utf8[2097152]。该文件中每一个字符都有图形化的字形显示作为注释，让我可以一眼认出这是哪个字符。

Then I patched my kernel again, and it worked. Now all the languages get a full support in Linux console.

然后我又重新编译了一遍内核，好用。现在所有的语言都能在Linux控制台里面显示啦。

I uploaded this package to ABS and call it univt-unicode, since it became an extended version of univt which supports all the unicode characters.

我把这个软件包上传到了ABS，并把它叫做univt-unicode，因为它扩展了univt，使其支持所有unicode字符。

10 years has passed since then, now it is 2022 and Shanghai is locked down due to the COVID-19 pandemic. Suddenly I recalled this patch, and now I have plenty of time to play with archlinux again. I installed archlinux the latest version, but noticed abs is no longer supported, and the patch I uploaded cannot be found. Fortunately, I fetched a backup copy from my dropbox account.

在那之后又过去了10年，如今2022，受新冠疫情影响，上海封城。我忽然想起了这个补丁，也忽然又有了时间再玩一玩archlinux。于是我安装了最新版的archlinux，却发现abs已经不受支持了，我之前上传的软件包也找不到了。还好，我从dropbox账号里找回了备份。

However, the linux kernel has changed dramatically since then, the code no longer applies to the current kernel 5.18. So, I'm doing search and research again on the internet.

但是，从那个时候到现在，linux内核已经改变了太多。原来的代码已经不能再应用到目前的5.18版内核了。于是我只好继续到网上搜索，看看有些什么发现。

I found cjktty, maintained by @microcai, who was inspired by youbest and contributed his patch to gentoo community. Gentoo is also a good distribution, which goes even further than archlinux into the source compiling. I played with it many years ago, but cannot stand the long time of compilation.

我找到了由@microcai 维护的cjktty，他受youbest（孙海勇）的启发，开发了这个补丁并贡献给了gentoo社区。Gentoo也是个很赞的发行版，在编译源代码的路上比archlinux走得更远。多年以前我也玩过，但实在等不了长时间的编译。

Then I found @zhmars, who forked univt first and then cjktty. I saw my font file was kept by @detiam and used in kernel versions < 4.2. Then the relevant kernel code changed significantly, and the font size changed as well. I'd like to appreciate @zhmars and @detiam for their update on the later versions of linux kernel, and I am grateful for their contribution to these Chinese console patches.

后来我又找到了@zhmars，他先fork了univt，又fork了cjktty。我看到自己当初做的字体文件被@detiam保留了下来，用在了4.2版本之前的内核上。后来这部分内核代码改动很大，字体大小也改了。在此我要感谢@zhmars和@detiam，他们把这个补丁持续地更新到后来版本的Linux内核，也对这些中文控制台的补丁做出了独有的贡献。

I can see the latest kernel 5.18 can use 32 x 32 font size, back then it was 16 x 16 when I converted the unifont in 2012. And thanks a lot to @zhmars, who re-convert the latest version of unifont to 32 x 32 glyph and applied it to both univt and cjktty. The idea of extending the font support from cjk to unicode is kept and shared, by a bunch of Chinese people who love linux, console and Chinese.

我发现最新版本的5.18内核已经可以使用32 x 32大小的字体，当初我在2012年转换unifont的时候还是16 x 16。谢谢@zhmars的卓越贡献，他重新转换了最新版的unifont字体，用上了新的32 x 32的尺寸，还同时应用到了univt和cjktty补丁上。我很高兴当年那个想要把Linux控制台的字体支持从中日韩扩展到unicode的想法被保留了下来，并被我们这一帮热爱Linux、控制台和中文的中国人们共享。

So I forked his univt patch repository and added this story to README. I'm so proud to be a Chinese with so many lovely buddies.

于是，我fork了他的最新版univt补丁代码库，并把这个故事加到了README里面。作为一个中国人，我很自豪有这样一群素不相识，却如此可爱的小伙伴。

- Neil Sun, June 5 2022, in Shanghai, China

- 孙楠，2022年6月5日，于中国上海

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
