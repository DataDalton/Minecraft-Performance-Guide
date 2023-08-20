![Minecraft Performance Guide Banner][Banner]

###### This is the Large Page files guide and is a part of the overarching Minecraft Performance Guide

<br>

Large Page Files
======

**NOTE: Large Pages requires admin privledges on Windows. This is a security risk, and you should skip this section if you aren't comfortable with that.**

Enabling large pages improves the performance of both Minecraft servers and clients. Here are some great tutorials for enabling it:

- [Windows 10 Pro](https://www.chaoticafractals.com/manual/getting-started/enabling-large-page-support-windows)
- [Windows 10 Home](https://awesomeprojectsxyz.blogspot.com/2017/11/windows-10-home-how-to-enable-lock.html?m=1)
- [Tool mirrors for the Windows 10 Home tutorial](https://gist.github.com/eyecatchup/0107bab3d92473cb8a3d3547848fc442)
- [Windows 11 Youtube](https://www.youtube.com/watch?v=v6A2clXcC9Y)

- [Linux](https://kstefanj.github.io/2021/05/19/large-pages-and-java.html)

On Windows, you **must** run Java, and your launcher, as an administrator.

That means checking the ["run as administrator" compatibility checkbox](https://support.sega.com/hc/en-us/articles/201556551-Compatibility-Mode-and-Running-as-Administrator-for-PC-Games) for `javaw.exe`, `java.exe` and `your launcher.exe`, otherwise Large Pages will silently fail. Add `-XX:+UseLargePages -XX:LargePageSizeInBytes=2m` to your JVM arguments.

On linux, you generally want to use `-XX:+UseTransparentHugePages`. To manually allocate memory instead (for a bigger performance boost), Red Hat has a good tutorial for RHEL-like linux distros, [like Fedora, CentOS, or Oracle Linux](https://www.redhat.com/en/blog/optimizing-rhel-8-run-java-implementation-minecraft-server)

Check and see if large pages is working with the `-Xlog:gc+init` java argument in Java 17.

In any Java version/platform, if large pages isn't working, you will get a warning in the log similar to this:
`Java HotSpot(TM) 64-Bit Server VM warning: JVM cannot use large page memory because it does not have enough privilege to lock pages in memory.`

> Note: With modern computers it is more beneficial to allocate more memory than to increase page file size

<br>

---

### [Credits](../Java%20Arguments/Sources_Credits.md)

<br>

[Logo]: ../assets/Minecraft%20Performance%20Guide%20-%20Logo.png
[Banner]: ../assets/Minecraft%20Performance%20Guide%20-%20Banner.png