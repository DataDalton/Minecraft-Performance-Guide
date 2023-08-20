![Minecraft Performance Guide Logo - Full][Logo Full]

###### This is the Sources and Credits for the detailed Minecraft Java Arguments guide and is a part of the overarching Minecraft Performance Guide

<br>

Credits
======

The original information for the Java arguments guide came from [brucethemoose/Minecraft-Performance-Flags-Benchmarks](https://github.com/brucethemoose/Minecraft-Performance-Flags-Benchmarks). Unfortunately, it seems the guide became stale and hasn't been updated in 7 months leading me to believe it has been abandoned. I have tried to contact the repository owner and had no luck in doing so, which is why I took the lead and made this entire guide originally. The original repository also has an [MIT license](https://github.com/brucethemoose/Minecraft-Performance-Flags-Benchmarks/blob/main/License.txt) which allows for this.

All credits for the original information goes to brucethemoose and the contributors of the above repository:

brucethemoose,

Godeps2891,

Radplay,

he3als

<br>

I have overhauled the entire look of the guide and brought it to a much more up-to-date standpoint and plan on maintaining it for quite a while moving forward.

I have also performed my own independent, extensive testing to ensure that accurate results and benchmarking have taken place.

<br>

Original Sources
======

These sources are the sources from the original repository which I felt like should be maintained here.

- Updated Aikar flags from this repo: https://github.com/etil2jz/etil-minecraft-flags
- Reddit post from a Forge dev: https://www.reddit.com/r/feedthebeast/comments/5jhuk9/modded_mc_and_memory_usage_a_history_with_a/
- Red Hat's optimization guide: https://www.redhat.com/en/blog/optimizing-rhel-8-run-java-implementation-minecraft-server
- GraalVM release notes: https://www.graalvm.org/release-notes/
- Oracle's Java 17 Documentation: https://docs.oracle.com/en/java/javase/17/docs/specs/man/java.html
- VM Options explorer: https://chriswhocodes.com/
- Java itself, via the `-XX:+PrintFlagsFinal` and the `-XX:+JVMCIPrintProperties` flags to dump flag descriptions/defaults.
- OpenJDK source: https://github.com/openjdk/jdk/
- Testing from @keyboard.tn in Discord.
- https://research.spec.org/icpe_proceedings/2014/p111.pdf
- https://www.diva-portal.org/smash/get/diva2:1466940/FULLTEXT01.pdf
- https://malloc.se/blog/zgc-jdk17
- https://docs.oracle.com/javase/8/embedded/develop-apps-platforms/codecache.htm


[Logo Small]: ../assets/Minecraft%20Performance%20Guide%20-%20Logo.png
[Logo Full]: ../assets/Minecraft%20Performance%20Guide%20-%20Full.png