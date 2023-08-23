![Minecraft Performance Guide Banner][Banner]

###### This is the detailed Minecraft Java Arguments guide and is a part of the overarching Minecraft Performance Guide

<br>

Minecraft Java Arguments
======

This repository serves the purpose of having an updated list of Java Arguments for Minecraft. Testing has been conducted for both Modded Minecraft and Vanilla Minecraft.

This guide will be a more in-depth version of the general guide in the Minecraft Performance Guide.

This guide contains information about different types of Java Runtime Environments's (JREs) and the Java Virtual Machine (JVM) arguments for each of them.

<br>

Disclaimer
======

It is possible depending on the system for these arguments to only minimally provide Ticks Per Second (TPS) and Frames Per Second (FPS) gains.

The purpose of these tweaks are to reduce stutters on the client as a result of garbage collection and other JVM issues which can be fixed through JVM arguments, however, significant server stutters will also be reduced as a result of these arguments if they are in-use on the server.

It is also possible as a result of the usage of these arguments to increase Random Access Memory (RAM) and Central Processing Unit (CPU) usage, which is not necessarily a negative aspect.

<br>

Mod lag
======

Since the purpose of this is not to necessarily fix TPS or FPS issues caused by mods I would recommend looking at these two mods in order to help diagnose your lag issues:

[Spark - Curseforge](https://www.curseforge.com/minecraft/mc-mods/spark) >=1.12.2

[Spark - Modrinth](https://modrinth.com/mod/spark?hl=en-US) >=1.12.2

or

(Observable is an updated version of LagGoggles)

[Observable - Curseforge](https://www.curseforge.com/minecraft/mc-mods/observable) >=1.16.5

[Observable - Modrinth](https://modrinth.com/mod/observable) >=1.16.5

or

[LagGoggles - Curseforge](https://www.curseforge.com/minecraft/mc-mods/laggoggles) 1.10.2, 1.12.2

<br>

### World Pregen

I also highly recommend pregenerating your world as this will greatly help with memory usage.

[Chunk-Pregenerator - Curseforge](https://www.curseforge.com/minecraft/mc-mods/chunkpregenerator) >=1.4.6

or

[Chunky - Curseforge](https://www.curseforge.com/minecraft/mc-mods/chunky-pregenerator-forge) >=1.16.5

[Chunky - Modrinth](https://modrinth.com/plugin/chunky) >=1.16.5

<br>

***Note: All mods above have Forge/Fabric versions***

<br>

Minecraft Version and Java Version
======

| **Minecraft Version** | **Java Version** |
|---|---|
| > 1.16.5 | 17 |
| = 1.16.5 | It is recommended to use Java 17 for Minecraft 1.16.5, however, in certain cases this may break some things, if you notice it is unplayable I recommend switching to Java 8. Although, some people may recommend going with Java 11/15/16 which should work with 1.16.5 it should have a better performance boost defaulting to Java 8. |
| < 1.16.5 | 8 |
| < 1.7.10 | You may need to use Java 7, for example 1.6.4 |

> Depending on your launcher you may be asked to use a different Java version. Curseforge and Prism will ask you to use Java 8 when you are on Minecraft 1.16.X, however, most 1.16.5 mods are compatible with Java 17.

<br>

Java Runtime Differences
======

There are many different Java Runtime's and people who own these Runtimes. There are quite a few which are almost identical, as a result of this quite a few different ones have been skipped as they do not provide any substantial differences between them which would result in a meaningful difference.

The most popular companies/people behind the different Runtimes are: Adoptium, Amazon, Azul, IBM, Intel, Microsoft, Oracle, and Red Hat.

The most notable differences between these different Java Runtimes are as follows:


- **Oracle GraalVM (EE)** - Comes with a more aggressive Java compiler - this is currently the most recommended JVE for performance

- **Intel's Clear Linux OpenJDK** - Uses the same code as many other OpenJDKs which makes it highly compatible, making it highly compatible. The build process itself and the dependencies are [optimized for newer CPUs](https://www.phoronix.com/review/zen4-clear-linux/2). You can get it from Clear Linux's repositories via `swupd`, from [Distrobox](https://github.com/89luca89/distrobox), or from [Docker](https://hub.docker.com/r/clearlinux/openjdk). It is important to note that in order to use this you must currently use the Java 17 release, and that Java 18 [reverts some of the performance enhancements](https://github.com/clearlinux-pkgs/openjdk/commit/14202e83f919643031cfb7a6318b067310be90f1).

- **Azul's Prime OpenJDK** - *Very* fast since it hooks into [LLVM](https://llvm.org/), but its currently incompatible with most mods and is linux-only. You can get it from [Azul Prime's docs](https://docs.azul.com/prime/prime-quick-start-tar)

- **Red Hat Java 8** - Has the Shenandoah garbage collector. It's gated behind a free email signup at [Redhat](https://developers.redhat.com/products/openjdk/download)

- **IBM's OpenJ9** - *Substantially* slower in Minecraft, and uses totally different flags than any other Java build, but it does consume less memory than OpenJDK-based runtimes. See [Frequently Asked Questions](#frequently-asked-questions), and [this Gist for low memory consumption flags](https://gist.github.com/FluffyFoxUwU/69f8f156feefae3d826ad0d15c694002).

<br>


If you dont know what to pick, I recommend GraalVM for the newest version of Minecraft using Java 17, or GraalVM EE using Java 8 (see below) or the latest [Adoptium Java 17 JRE](https://adoptium.net/)

Couleur maintains a good running list of [JREs](https://rentry.co/JREs) (Note: This may be a little outdated now)

<br>

Launchers
======
It is important to note that the launcher you use may influence the behavior of how you input your java arguments/flags.

[Prism Launcher](https://prismlauncher.org/wiki/help-pages/java-settings/)

[ATLauncher](https://atlauncher.com/help/extra-arguments)

Depending on your launcher, you may also have to edit the available copy-paste ready flags. Typically, the only thing you need to modify is removing the `-Xmx8G -Xms8G` at the start. This is because the launcher already has a way to set the memory allocation and you should use that instead.

<br>

Memory Allocation
======
Minimum and maximum (`-Xms` and `-Xmx`) memory should be set to the same value, as [explained](https://dzone.com/articles/benefits-of-setting-initial-and-maximum-memory-siz)

**One exception:** if you are on a low-memory system, and Minecraft takes up almost all your RAM, set your minimum memory below your maximum memory to conserve as much as possible.

Sizes are set in megabytes (`-Xms4096M`) or gigabytes (`-Xmx8G`)

Allocating too much memory can break garbage collection or just slow Minecraft down, even if you have plenty to spare.

Allocating too little can also slow down or break the game.

Keep a close eye on the Window's Task manager (or your DE's system monitor) as Minecraft is running, and allocate only as much as it needs (which is usually less than 8GB but can be more for larger modpacks! As a client I recommend <16GB in most situations). [`/sparkc gcmonitor`](https://spark.lucko.me/docs/Command-Usage#spark-gcmonitor) will tell you if your allocation is too high (the pauses will be too long) or too low (frequent garbage collection with a low memory warning in the notification).

*You should also only ever allocate >=32GB of ram when you are on a server. Once you enable 32GB of memory you disable [compressed OOPs](https://www.baeldung.com/jvm-compressed-oops) which will impact performance. It is possible to enable OOPs when using >=32GB, however, it will still negatively impact performance*

*Many people are still under the belief that you should only use 4-8GB of memory, this is not true and has not been true for a very long time. Most modded packs perform best when using 6-16GB of memory client-side. It is also possible, depending on the version and if there are mods, and how many mods, that you need less or even more than this 6-16GB range. I highly recommend testing this yourself and seeing what performs best as there is a large amount of variables to consider.*

> Note: I highly recommend hosting both vanilla and modded on a server. Hosting on a server will reduce client stress and will increase overall performance. If you are looking for a free option, Oracle offers a permanent always free-tier (which should not be confused with the free trial) you can find a good guide how to setup an Oracle server with this [Youtube video](https://www.youtube.com/watch?v=RyC-m725uTs)

<br>

Base Java (>8) Flags
======

These flags run with any Java 11+ Environment. They work on both servers and clients:

(**You *must* add garbage collection flags to these java arguments. These arguments only act as a base to append further flags to.**)


```-XX:+UnlockExperimentalVMOptions -XX:+UnlockDiagnosticVMOptions -XX:+AlwaysActAsServerClassMachine -XX:+AlwaysPreTouch -XX:+DisableExplicitGC -XX:+UseNUMA -XX:NmethodSweepActivity=1 -XX:ReservedCodeCacheSize=400M -XX:NonNMethodCodeHeapSize=12M -XX:ProfiledCodeHeapSize=194M -XX:NonProfiledCodeHeapSize=194M -XX:-DontCompileHugeMethods -XX:MaxNodeLimit=240000 -XX:NodeLimitFudgeFactor=8000 -XX:+UseVectorCmov -XX:+PerfDisableSharedMem -XX:+UseFastUnorderedTimeStamps -XX:+UseCriticalJavaThreadPriority -XX:ThreadPriorityPolicy=1 -XX:AllocatePrefetchStyle=3```

<br>

Base Java 8 Flags
======

These flags run with any Java 8 Environment, they work on both servers and clients:

These flags will work with OpenJDK8, along with Shenandoh GC, or G1GC:

```-XX:+UnlockExperimentalVMOptions -XX:+UnlockDiagnosticVMOptions -XX:+AlwaysActAsServerClassMachine -XX:+ParallelRefProcEnabled -XX:+DisableExplicitGC -XX:+AlwaysPreTouch -XX:+PerfDisableSharedMem -XX:+AggressiveOpts -XX:+UseFastAccessorMethods -XX:MaxInlineLevel=15 -XX:MaxVectorSize=32 -XX:+UseCompressedOops -XX:ThreadPriorityPolicy=1 -XX:+UseNUMA -XX:+UseDynamicNumberOfGCThreads -XX:NmethodSweepActivity=1 -XX:ReservedCodeCacheSize=350M -XX:-DontCompileHugeMethods -XX:MaxNodeLimit=240000 -XX:NodeLimitFudgeFactor=8000 -XX:+UseFPUForSpilling -Dgraal.CompilerConfiguration=community```

x86 Java 8 users (aka most Java 8 users) can add these additional arguments:

```-XX:+UseXMMForArrayCopy```

<br>

Garbage Collection
======

**Garbage collection flags must be added to Minecraft servers and clients**, as the default pauses/stutters to stop and collect garbage manifest on the client and lag on servers. Use the `/sparkc gcmonitor` command with the [Spark](https://www.curseforge.com/minecraft/mc-mods/spark) mod to observe stutters in-game. *Any* old generation pauses are bad, and young generation G1GC collections should be infrequent, but short enough to be not noticeable.

Pick one set of flags. ~~I recommend **Shenandoah on clients**, **ZGC on powerful Java 17 servers**, and **G1GC on Graal** or on servers/clients with less RAM and fewer cores:~~

<br>

### ZGC

ZGC is great for high memory and high core count servers. It has no server throughput hit which can be significantly measured, and does not stutter. However, it requires more RAM and more cores than most other garbage collectors.

ZGC may cause a significant client FPS hit. See the "ZGC" benchmarks in the benchmarks folder. It's not available in Java 8, and much less performant in Java 11 than in Java 17.

`-XX:+UseZGC -XX:AllocatePrefetchStyle=1 -XX:-ZProactive` enables it, but allocate more RAM and more `ConcGCThreads` than you normally would for other garbage collectors.

> Note: ZGC does not like AllocatePrefetchStyle=3, hence setting it to 1 overrides the previous entry which has already been done in these flags for you.

<details>
    <summary>If we were to use Java >8 with only ZGC it would look like this</summary>

```-Xmx8G -Xms8G -XX:+UnlockExperimentalVMOptions -XX:+UnlockDiagnosticVMOptions -XX:+AlwaysActAsServerClassMachine -XX:+AlwaysPreTouch -XX:+DisableExplicitGC -XX:+UseNUMA -XX:NmethodSweepActivity=1 -XX:ReservedCodeCacheSize=400M -XX:NonNMethodCodeHeapSize=12M -XX:ProfiledCodeHeapSize=194M -XX:NonProfiledCodeHeapSize=194M -XX:-DontCompileHugeMethods -XX:MaxNodeLimit=240000 -XX:NodeLimitFudgeFactor=8000 -XX:+UseVectorCmov -XX:+PerfDisableSharedMem -XX:+UseFastUnorderedTimeStamps -XX:+UseCriticalJavaThreadPriority -XX:ThreadPriorityPolicy=1 -XX:AllocatePrefetchStyle=3 -XX:+UseZGC -XX:AllocatePrefetchStyle=1 -XX:-ZProactive```

</details>

<br>

### Shenandoah

Shenandoah performs well on clients, but may kill server throughput.

Enable it with `-XX:+UseShenandoahGC -XX:ShenandoahGCMode=iu -XX:ShenandoahGuaranteedGCInterval=1000000 -XX:AllocatePrefetchStyle=1`

See more tuning options [here](https://wiki.openjdk.org/display/shenandoah/Main). The "herustic" and "mode" options don't change much for me (except for "compact," which you should not use). Like ZGC, Shenandoah does not like AllocatePrefetchStyle=3.

> Note: Shenandoah is not in Java 8. It's also not currently in any Oracle Java builds. If you are a Java 8 user, you must use Red Hat OpenJDK to use [Shenandoah](https://developers.redhat.com/products/openjdk/download)

<details>
    <summary>If we were to use Java >8 with only Shenandoah it would look like this</summary>

```-Xmx8G -Xms8G -XX:+UnlockExperimentalVMOptions -XX:+UnlockDiagnosticVMOptions -XX:+AlwaysActAsServerClassMachine -XX:+AlwaysPreTouch -XX:+DisableExplicitGC -XX:+UseNUMA -XX:NmethodSweepActivity=1 -XX:ReservedCodeCacheSize=400M -XX:NonNMethodCodeHeapSize=12M -XX:ProfiledCodeHeapSize=194M -XX:NonProfiledCodeHeapSize=194M -XX:-DontCompileHugeMethods -XX:MaxNodeLimit=240000 -XX:NodeLimitFudgeFactor=8000 -XX:+UseVectorCmov -XX:+PerfDisableSharedMem -XX:+UseFastUnorderedTimeStamps -XX:+UseCriticalJavaThreadPriority -XX:ThreadPriorityPolicy=1 -XX:AllocatePrefetchStyle=3 -XX:+UseShenandoahGC -XX:ShenandoahGCMode=iu -XX:ShenandoahGuaranteedGCInterval=1000000 -XX:AllocatePrefetchStyle=1```

</details>

<br>

### Client G1GC

G1GC is the default garbage collector for all JREs, (and was previously the only available garbage collector for GraalVM). ~~and is the only available garbage collector for [GraalVM users](https://github.com/oracle/graal/issues/2149).~~

Aikar's [famous Minecraft server G1GC arguments](https://aikar.co/2018/07/02/tuning-the-jvm-g1gc-garbage-collector-flags-for-minecraft/) run great on clients

There are two caveats: they effectively [clamp](https://www.oracle.com/technical-resources/articles/java/g1gc.html) the `MaxGCPauseMillis` parameter by setting `G1NewSizePercent` so high, producing long stutters on some clients, and they collect oldgen garbage too aggressively (as the client produces *far* less than a populated server).

These flags are similar to the aikar flags, but with shorter, more frequent pauses, less aggressive G1 mixed collection and more aggressive background collection: `-XX:+UseG1GC -XX:MaxGCPauseMillis=37 -XX:+PerfDisableSharedMem -XX:G1HeapRegionSize=16M -XX:G1NewSizePercent=23 -XX:G1ReservePercent=20 -XX:SurvivorRatio=32 -XX:G1MixedGCCountTarget=3 -XX:G1HeapWastePercent=20 -XX:InitiatingHeapOccupancyPercent=10 -XX:G1RSetUpdatingPauseTimePercent=0 -XX:MaxTenuringThreshold=1 -XX:G1SATBBufferEnqueueingThresholdPercent=30 -XX:G1ConcMarkStepDurationMillis=5.0 -XX:G1ConcRSHotCardLimit=16 -XX:G1ConcRefinementServiceIntervalMillis=150 -XX:GCTimeRatio=99`

> Note: If you are using Java 20, it does not need the `-XX:G1ConcRefinementServiceIntervalMillis=150` flag and will only print a warning with the flag

`G1NewSizePercent` and `MaxGCPauseMillis` can be used to tune the frequency and duration of your young generation collections. `G1HeapWastePercent=18` should be removed if you are getting any old generation pauses on your setup. Alternatively, you can raise it and set `G1MixedGCCountTarget` to 2 or 1 to make mixed garbage collection even lazier, but will cost higher memory usage.

<details>
    <summary>If we were to use Java >8 with only G1GC, client, it would look like this</summary>

```-Xmx8G -Xms8G -XX:+UnlockExperimentalVMOptions -XX:+UnlockDiagnosticVMOptions -XX:+AlwaysActAsServerClassMachine -XX:+AlwaysPreTouch -XX:+DisableExplicitGC -XX:+UseNUMA -XX:NmethodSweepActivity=1 -XX:ReservedCodeCacheSize=400M -XX:NonNMethodCodeHeapSize=12M -XX:ProfiledCodeHeapSize=194M -XX:NonProfiledCodeHeapSize=194M -XX:-DontCompileHugeMethods -XX:MaxNodeLimit=240000 -XX:NodeLimitFudgeFactor=8000 -XX:+UseVectorCmov -XX:+PerfDisableSharedMem -XX:+UseFastUnorderedTimeStamps -XX:+UseCriticalJavaThreadPriority -XX:ThreadPriorityPolicy=1 -XX:AllocatePrefetchStyle=3 -XX:+UseG1GC -XX:MaxGCPauseMillis=37 -XX:+PerfDisableSharedMem -XX:G1HeapRegionSize=16M -XX:G1NewSizePercent=23 -XX:G1ReservePercent=20 -XX:SurvivorRatio=32 -XX:G1MixedGCCountTarget=3 -XX:G1HeapWastePercent=20 -XX:InitiatingHeapOccupancyPercent=10 -XX:G1RSetUpdatingPauseTimePercent=0 -XX:MaxTenuringThreshold=1 -XX:G1SATBBufferEnqueueingThresholdPercent=30 -XX:G1ConcMarkStepDurationMillis=5.0 -XX:G1ConcRSHotCardLimit=16 -XX:G1ConcRefinementServiceIntervalMillis=150 -XX:GCTimeRatio=99```

</details>

<details>
    <summary>If we were to use Java 8 with only G1GC, client, it would look like this</summary>

```-Xmx8G -Xms8G -XX:+UnlockExperimentalVMOptions -XX:+UnlockDiagnosticVMOptions -XX:+AlwaysActAsServerClassMachine -XX:+ParallelRefProcEnabled -XX:+DisableExplicitGC -XX:+AlwaysPreTouch -XX:+PerfDisableSharedMem -XX:+AggressiveOpts -XX:+UseFastAccessorMethods -XX:MaxInlineLevel=15 -XX:MaxVectorSize=32 -XX:+UseCompressedOops -XX:ThreadPriorityPolicy=1 -XX:+UseNUMA -XX:+UseDynamicNumberOfGCThreads -XX:NmethodSweepActivity=1 -XX:ReservedCodeCacheSize=350M -XX:-DontCompileHugeMethods -XX:MaxNodeLimit=240000 -XX:NodeLimitFudgeFactor=8000 -XX:+UseFPUForSpilling -Dgraal.CompilerConfiguration=community -XX:+UseG1GC -XX:MaxGCPauseMillis=37 -XX:+PerfDisableSharedMem -XX:G1HeapRegionSize=16M -XX:G1NewSizePercent=23 -XX:G1ReservePercent=20 -XX:SurvivorRatio=32 -XX:G1MixedGCCountTarget=3 -XX:G1HeapWastePercent=20 -XX:InitiatingHeapOccupancyPercent=10 -XX:G1RSetUpdatingPauseTimePercent=0 -XX:MaxTenuringThreshold=1 -XX:G1SATBBufferEnqueueingThresholdPercent=30 -XX:G1ConcMarkStepDurationMillis=5.0 -XX:G1ConcRSHotCardLimit=16 -XX:G1ConcRefinementServiceIntervalMillis=150 -XX:GCTimeRatio=99```

</details>

<br>

### Server G1GC

Longer pauses of garbage collection are more acceptable on servers. These flags are very close to the aikar defaults:

`-XX:+UseG1GC -XX:MaxGCPauseMillis=130 -XX:+UnlockExperimentalVMOptions -XX:+DisableExplicitGC -XX:+AlwaysPreTouch -XX:G1NewSizePercent=28 -XX:G1HeapRegionSize=16M -XX:G1ReservePercent=20 -XX:G1MixedGCCountTarget=3 -XX:InitiatingHeapOccupancyPercent=10 -XX:G1MixedGCLiveThresholdPercent=90 -XX:G1RSetUpdatingPauseTimePercent=0 -XX:SurvivorRatio=32 -XX:MaxTenuringThreshold=1 -XX:G1SATBBufferEnqueueingThresholdPercent=30 -XX:G1ConcMarkStepDurationMillis=5 -XX:G1ConcRSHotCardLimit=16 -XX:G1ConcRefinementServiceIntervalMillis=150`

> Note: If you are using Java 20, it does not need the `-XX:G1ConcRefinementServiceIntervalMillis=150` flag and will only print a warning with the flag

<details>
    <summary>If we were to use Java >8 with only G1GC, server, it would look like this</summary>

```-Xmx8G -Xms8G -XX:+UnlockExperimentalVMOptions -XX:+UnlockDiagnosticVMOptions -XX:+AlwaysActAsServerClassMachine -XX:+AlwaysPreTouch -XX:+DisableExplicitGC -XX:+UseNUMA -XX:NmethodSweepActivity=1 -XX:ReservedCodeCacheSize=400M -XX:NonNMethodCodeHeapSize=12M -XX:ProfiledCodeHeapSize=194M -XX:NonProfiledCodeHeapSize=194M -XX:-DontCompileHugeMethods -XX:MaxNodeLimit=240000 -XX:NodeLimitFudgeFactor=8000 -XX:+UseVectorCmov -XX:+PerfDisableSharedMem -XX:+UseFastUnorderedTimeStamps -XX:+UseCriticalJavaThreadPriority -XX:ThreadPriorityPolicy=1 -XX:AllocatePrefetchStyle=3 -XX:+UseG1GC -XX:MaxGCPauseMillis=130 -XX:+UnlockExperimentalVMOptions -XX:+DisableExplicitGC -XX:+AlwaysPreTouch -XX:G1NewSizePercent=28 -XX:G1HeapRegionSize=16M -XX:G1ReservePercent=20 -XX:G1MixedGCCountTarget=3 -XX:InitiatingHeapOccupancyPercent=10 -XX:G1MixedGCLiveThresholdPercent=90 -XX:G1RSetUpdatingPauseTimePercent=0 -XX:SurvivorRatio=32 -XX:MaxTenuringThreshold=1 -XX:G1SATBBufferEnqueueingThresholdPercent=30 -XX:G1ConcMarkStepDurationMillis=5 -XX:G1ConcRSHotCardLimit=16 -XX:G1ConcRefinementServiceIntervalMillis=150```

</details>

<details>
    <summary>If we were to use Java 8 with only G1GC, server, it would look like this</summary>

```-Xmx8G -Xms8G -XX:+UnlockExperimentalVMOptions -XX:+UnlockDiagnosticVMOptions -XX:+AlwaysActAsServerClassMachine -XX:+ParallelRefProcEnabled -XX:+DisableExplicitGC -XX:+AlwaysPreTouch -XX:+PerfDisableSharedMem -XX:+AggressiveOpts -XX:+UseFastAccessorMethods -XX:MaxInlineLevel=15 -XX:MaxVectorSize=32 -XX:+UseCompressedOops -XX:ThreadPriorityPolicy=1 -XX:+UseNUMA -XX:+UseDynamicNumberOfGCThreads -XX:NmethodSweepActivity=1 -XX:ReservedCodeCacheSize=350M -XX:-DontCompileHugeMethods -XX:MaxNodeLimit=240000 -XX:NodeLimitFudgeFactor=8000 -XX:+UseFPUForSpilling -Dgraal.CompilerConfiguration=community -XX:+UseG1GC -XX:MaxGCPauseMillis=130 -XX:+UnlockExperimentalVMOptions -XX:+DisableExplicitGC -XX:+AlwaysPreTouch -XX:G1NewSizePercent=28 -XX:G1HeapRegionSize=16M -XX:G1ReservePercent=20 -XX:G1MixedGCCountTarget=3 -XX:InitiatingHeapOccupancyPercent=10 -XX:G1MixedGCLiveThresholdPercent=90 -XX:G1RSetUpdatingPauseTimePercent=0 -XX:SurvivorRatio=32 -XX:MaxTenuringThreshold=1 -XX:G1SATBBufferEnqueueingThresholdPercent=30 -XX:G1ConcMarkStepDurationMillis=5 -XX:G1ConcRSHotCardLimit=16 -XX:G1ConcRefinementServiceIntervalMillis=150```

</details>

<br>

### More aggressive G1GC

**Warning: In order to use these flags you will need a larger amount of memory as well as a better CPU.**

`-XX:+UseG1GC -XX:MaxGCPauseMillis=20 -XX:+PerfDisableSharedMem -XX:G1HeapRegionSize=16M -XX:G1NewSizePercent=23 -XX:G1ReservePercent=20 -XX:SurvivorRatio=32 -XX:G1MixedGCCountTarget=1 -XX:G1HeapWastePercent=30 -XX:InitiatingHeapOccupancyPercent=15 -XX:G1RSetUpdatingPauseTimePercent=0 -XX:MaxTenuringThreshold=1 -XX:G1SATBBufferEnqueueingThresholdPercent=30 -XX:G1ConcMarkStepDurationMillis=5.0 -XX:G1ConcRSHotCardLimit=16 -XX:G1ConcRefinementServiceIntervalMillis=150 -XX:GCTimeRatio=99`

<details>
    <summary>If we were to use Java >8 with only aggressive G1GC, client, it would look like this</summary>

```-Xmx8G -Xms8G -XX:+UnlockExperimentalVMOptions -XX:+UnlockDiagnosticVMOptions -XX:+AlwaysActAsServerClassMachine -XX:+AlwaysPreTouch -XX:+DisableExplicitGC -XX:+UseNUMA -XX:NmethodSweepActivity=1 -XX:ReservedCodeCacheSize=400M -XX:NonNMethodCodeHeapSize=12M -XX:ProfiledCodeHeapSize=194M -XX:NonProfiledCodeHeapSize=194M -XX:-DontCompileHugeMethods -XX:MaxNodeLimit=240000 -XX:NodeLimitFudgeFactor=8000 -XX:+UseVectorCmov -XX:+PerfDisableSharedMem -XX:+UseFastUnorderedTimeStamps -XX:+UseCriticalJavaThreadPriority -XX:ThreadPriorityPolicy=1 -XX:AllocatePrefetchStyle=3 -XX:+UseG1GC -XX:MaxGCPauseMillis=20 -XX:+PerfDisableSharedMem -XX:G1HeapRegionSize=16M -XX:G1NewSizePercent=23 -XX:G1ReservePercent=20 -XX:SurvivorRatio=32 -XX:G1MixedGCCountTarget=1 -XX:G1HeapWastePercent=30 -XX:InitiatingHeapOccupancyPercent=15 -XX:G1RSetUpdatingPauseTimePercent=0 -XX:MaxTenuringThreshold=1 -XX:G1SATBBufferEnqueueingThresholdPercent=30 -XX:G1ConcMarkStepDurationMillis=5.0 -XX:G1ConcRSHotCardLimit=16 -XX:G1ConcRefinementServiceIntervalMillis=150 -XX:GCTimeRatio=99```

</details>

<details>
    <summary>If we were to use Java 8 with only aggressive G1GC, client, it would look like this</summary>

```-Xmx8G -Xms8G -XX:+UnlockExperimentalVMOptions -XX:+UnlockDiagnosticVMOptions -XX:+AlwaysActAsServerClassMachine -XX:+ParallelRefProcEnabled -XX:+DisableExplicitGC -XX:+AlwaysPreTouch -XX:+PerfDisableSharedMem -XX:+AggressiveOpts -XX:+UseFastAccessorMethods -XX:MaxInlineLevel=15 -XX:MaxVectorSize=32 -XX:+UseCompressedOops -XX:ThreadPriorityPolicy=1 -XX:+UseNUMA -XX:+UseDynamicNumberOfGCThreads -XX:NmethodSweepActivity=1 -XX:ReservedCodeCacheSize=350M -XX:-DontCompileHugeMethods -XX:MaxNodeLimit=240000 -XX:NodeLimitFudgeFactor=8000 -XX:+UseFPUForSpilling -Dgraal.CompilerConfiguration=community -XX:+UseG1GC -XX:MaxGCPauseMillis=20 -XX:+PerfDisableSharedMem -XX:G1HeapRegionSize=16M -XX:G1NewSizePercent=23 -XX:G1ReservePercent=20 -XX:SurvivorRatio=32 -XX:G1MixedGCCountTarget=1 -XX:G1HeapWastePercent=30 -XX:InitiatingHeapOccupancyPercent=15 -XX:G1RSetUpdatingPauseTimePercent=0 -XX:MaxTenuringThreshold=1 -XX:G1SATBBufferEnqueueingThresholdPercent=30 -XX:G1ConcMarkStepDurationMillis=5.0 -XX:G1ConcRSHotCardLimit=16 -XX:G1ConcRefinementServiceIntervalMillis=150 -XX:GCTimeRatio=99```

</details>

<details>
    <summary>If we were to use Java >8 with only aggressive G1GC, server, it would look like this</summary>

```-Xmx8G -Xms8G -XX:+UnlockExperimentalVMOptions -XX:+UnlockDiagnosticVMOptions -XX:+AlwaysActAsServerClassMachine -XX:+AlwaysPreTouch -XX:+DisableExplicitGC -XX:+UseNUMA -XX:NmethodSweepActivity=1 -XX:ReservedCodeCacheSize=400M -XX:NonNMethodCodeHeapSize=12M -XX:ProfiledCodeHeapSize=194M -XX:NonProfiledCodeHeapSize=194M -XX:-DontCompileHugeMethods -XX:MaxNodeLimit=240000 -XX:NodeLimitFudgeFactor=8000 -XX:+UseVectorCmov -XX:+PerfDisableSharedMem -XX:+UseFastUnorderedTimeStamps -XX:+UseCriticalJavaThreadPriority -XX:ThreadPriorityPolicy=1 -XX:AllocatePrefetchStyle=3 -XX:+UseG1GC -XX:MaxGCPauseMillis=20 -XX:+PerfDisableSharedMem -XX:G1HeapRegionSize=16M -XX:G1NewSizePercent=23 -XX:G1ReservePercent=20 -XX:SurvivorRatio=32 -XX:G1MixedGCCountTarget=1 -XX:G1HeapWastePercent=30 -XX:InitiatingHeapOccupancyPercent=15 -XX:G1RSetUpdatingPauseTimePercent=0 -XX:MaxTenuringThreshold=1 -XX:G1SATBBufferEnqueueingThresholdPercent=30 -XX:G1ConcMarkStepDurationMillis=5.0 -XX:G1ConcRSHotCardLimit=16 -XX:G1ConcRefinementServiceIntervalMillis=150 -XX:GCTimeRatio=99```

</details>

<details>
    <summary>If we were to use Java 8 with only aggressive G1GC, server, it would look like this</summary>

```-Xmx8G -Xms8G -XX:+UnlockExperimentalVMOptions -XX:+UnlockDiagnosticVMOptions -XX:+AlwaysActAsServerClassMachine -XX:+ParallelRefProcEnabled -XX:+DisableExplicitGC -XX:+AlwaysPreTouch -XX:+PerfDisableSharedMem -XX:+AggressiveOpts -XX:+UseFastAccessorMethods -XX:MaxInlineLevel=15 -XX:MaxVectorSize=32 -XX:+UseCompressedOops -XX:ThreadPriorityPolicy=1 -XX:+UseNUMA -XX:+UseDynamicNumberOfGCThreads -XX:NmethodSweepActivity=1 -XX:ReservedCodeCacheSize=350M -XX:-DontCompileHugeMethods -XX:MaxNodeLimit=240000 -XX:NodeLimitFudgeFactor=8000 -XX:+UseFPUForSpilling -Dgraal.CompilerConfiguration=community -XX:+UseG1GC -XX:MaxGCPauseMillis=20 -XX:+PerfDisableSharedMem -XX:G1HeapRegionSize=16M -XX:G1NewSizePercent=23 -XX:G1ReservePercent=20 -XX:SurvivorRatio=32 -XX:G1MixedGCCountTarget=1 -XX:G1HeapWastePercent=30 -XX:InitiatingHeapOccupancyPercent=15 -XX:G1RSetUpdatingPauseTimePercent=0 -XX:MaxTenuringThreshold=1 -XX:G1SATBBufferEnqueueingThresholdPercent=30 -XX:G1ConcMarkStepDurationMillis=5.0 -XX:G1ConcRSHotCardLimit=16 -XX:G1ConcRefinementServiceIntervalMillis=150 -XX:GCTimeRatio=99```

</details>

> Note: If you are using Java 20, it does not need the `-XX:G1ConcRefinementServiceIntervalMillis=150` flag and will only print a warning with the flag

<br>

### Garbage Collection Threading

`-XX:ConcGCThreads=[Some Number]` controls the [*maximum number*](https://github.com/openjdk/jdk/blob/dd34a4c28da73c798e021c7473ac57ead56c9903/src/hotspot/share/gc/z/zHeuristics.cpp#L96-L104) of background threads the garbage collector is allowed to use, and defaults to the calculation `logical (hyperthreaded) cores / 4`. Recent versions of Java will [reduce the number of garbage collection threads, if needed](https://wiki.openjdk.org/display/zgc/Main#Main-SettingConcurrentGCThreads).

In some cases (especially with ZGC or Shenandoh garbage collection) you want to increase this thread cap past the default. I recommend "2" on CPUs with 4 threads, and `[number of real cores - 2]` on most other CPUs, but you may need to change and test around with this parameter. If it's too low, garbage collection will not keep up with Minecraft, and the game will stutter and/or start eating large amounts of RAM and crash. If it's too high, it might slow the game down, especially if you are running Java 8.

No other "threading" flags like `ParallelGCThreads` or `JVMCIThreads` are necessary, as they are enabled by default with good automatic settings in Java 8+.

<br>

GraalVM (Enterprise Edition)
======

GraalVM is a new Java VM from Oracle that can improve the performance of (modded and vanilla) Minecraft. While client FPS gains are modest, server-side workloads like chunk generation can get a 20%+ boost.

All new versions of GraalVM come with the full set of optimizations rather than previously it being limited to only the Enterprise Edition versions. ~~Only GraalVM Enterprise Edition comes with the full set of optimizations~~.

Download it from these direct links from Oracle:

*Most up-to-date Enterprise Edition downloads, no account needed*
<details>
  <summary>Java 17</summary>

- Windows AMD64 (64-bit): https://oca.opensource.oracle.com/gds/GRAALVM_EE_JAVA17_22_3_2/graalvm-ee-java17-windows-amd64-22.3.2.zip

- Linux AMD64 (64-bit): https://oca.opensource.oracle.com/gds/GRAALVM_EE_JAVA17_22_3_2/graalvm-ee-java17-linux-amd64-22.3.2.tar.gz

- Linux AARCH64 (ARM 64-bit): https://oca.opensource.oracle.com/gds/GRAALVM_EE_JAVA17_22_3_2/graalvm-ee-java17-linux-aarch64-22.3.2.tar.gz

- Mac AMD64 (64-bit): https://oca.opensource.oracle.com/gds/GRAALVM_EE_JAVA17_22_3_2/graalvm-ee-java17-darwin-amd64-22.3.2.tar.gz

</details>

<details>
  <summary>Java 11</summary>

- Windows AMD64 (64-bit): https://oca.opensource.oracle.com/gds/GRAALVM_EE_JAVA11_22_3_2/graalvm-ee-java11-windows-amd64-22.3.2.zip

- Linux AMD64 (64-bit): https://oca.opensource.oracle.com/gds/GRAALVM_EE_JAVA11_22_3_2/graalvm-ee-java11-linux-amd64-22.3.2.tar.gz

- Linux AARCH64 (ARM 64-bit): https://oca.opensource.oracle.com/gds/GRAALVM_EE_JAVA11_22_3_2/graalvm-ee-java11-linux-aarch64-22.3.2.tar.gz

- Mac AMD64 (64-bit): https://oca.opensource.oracle.com/gds/GRAALVM_EE_JAVA11_22_3_2/graalvm-ee-java11-darwin-amd64-22.3.2.tar.gz

</details>

<details>
  <summary>Java 8</summary>

- Windows AMD64 (64-bit): https://oca.opensource.oracle.com/gds/GRAALVM_EE_JAVA8_21_3_6/graalvm-ee-java8-windows-amd64-21.3.6.zip

- Linux AMD64 (64-bit): https://oca.opensource.oracle.com/gds/GRAALVM_EE_JAVA8_21_3_6/graalvm-ee-java8-linux-amd64-21.3.6.tar.gz

- Mac AMD64 (64-bit): https://oca.opensource.oracle.com/gds/GRAALVM_EE_JAVA8_21_3_6/graalvm-ee-java8-darwin-amd64-21.3.6.tar.gz

</details>

<br>

Select GraalVM EE versions are also available on the AUR and on Oracle Linux's repositories

*Most up-to-date non-Enterprise Edition downloads, no account needed*
<details>
  <summary>Java 20</summary>

- Windows AMD64 (64-bit): https://download.oracle.com/graalvm/20/latest/graalvm-jdk-20_windows-x64_bin.zip

- Linux AMD64 (64-bit): https://download.oracle.com/graalvm/20/latest/graalvm-jdk-20_linux-x64_bin.tar.gz

- Linux AARCH64 (ARM 64-bit): https://download.oracle.com/graalvm/20/latest/graalvm-jdk-20_linux-aarch64_bin.tar.gz

- Mac AMD64 (64-bit): https://download.oracle.com/graalvm/20/latest/graalvm-jdk-20_macos-x64_bin.tar.gz

- Mac AARCH64 (ARM 64-bit): https://download.oracle.com/graalvm/20/latest/graalvm-jdk-20_macos-aarch64_bin.tar.gz

</details>

<details>
  <summary>Java 17</summary>

- Windows AMD64 (64-bit): https://download.oracle.com/graalvm/17/latest/graalvm-jdk-17_windows-x64_bin.zip

- Linux AMD64 (64-bit): https://download.oracle.com/graalvm/17/latest/graalvm-jdk-17_linux-x64_bin.tar.gz

- Linux AARCH64 (ARM 64-bit): https://download.oracle.com/graalvm/17/latest/graalvm-jdk-17_linux-aarch64_bin.tar.gz

- Mac AMD64 (64-bit): https://download.oracle.com/graalvm/17/latest/graalvm-jdk-17_macos-x64_bin.tar.gz

- Mac AARCH64 (ARM 64-bit): https://download.oracle.com/graalvm/17/latest/graalvm-jdk-17_macos-aarch64_bin.tar.gz


</details>

<br>

These releases are not Java installers. You need to manually replace your launcher's version of Java, or use a Minecraft launcher that supports specifying your Java path. I recommend ATLauncher, Prism Launcher or GDLauncher. When specifying a java path, navigate to the "bin" folder in the GraalVM download and use `javaw.exe` or `java.exe` (`javaw.exe` is typically the most recommended as it will not have an additional console window/command promot while `java.exe` will).

Alternatively, you can install it system-wide by following [Oracle's guide](https://www.graalvm.org/latest/docs/getting-started/)

You can also look for current and archived versions of GraalVM (EE) on [Oracle's website](https://www.oracle.com/downloads/graalvm-downloads.html)

<br>

For servers, you need to replace the "java" command in your server start sh/bat file with the full path to Graalvm (EE) java, in quotes.

<br>

## GraalVM (EE) Java Arguments

Be sure to set `-Dgraal.VectorizeSIMD` to `false` if you run shaders.
Arguments for GraalVM (EE) 11, 17, & 20:

```-XX:+UnlockExperimentalVMOptions -XX:+UnlockDiagnosticVMOptions -XX:+AlwaysActAsServerClassMachine -XX:+AlwaysPreTouch -XX:+DisableExplicitGC -XX:+UseNUMA -XX:AllocatePrefetchStyle=3 -XX:NmethodSweepActivity=1 -XX:ReservedCodeCacheSize=400M -XX:NonNMethodCodeHeapSize=12M -XX:ProfiledCodeHeapSize=194M -XX:NonProfiledCodeHeapSize=194M -XX:-DontCompileHugeMethods -XX:+PerfDisableSharedMem -XX:+UseFastUnorderedTimeStamps -XX:+UseCriticalJavaThreadPriority -XX:+EagerJVMCI -Dgraal.TuneInlinerExploration=1 -Dgraal.CompilerConfiguration=enterprise```

**You must use G1GC or ZGC with these arguments.** GraalVM currently doesn't work with Shenandoah's garbage collector.

<details>
    <summary>If we were to use Java >8 with GraalVM (EE's) Java Arguments and G1GC, it would look like this (Client)</summary>

```-Xmx8G -Xms8G -XX:+UnlockExperimentalVMOptions -XX:+UnlockDiagnosticVMOptions -XX:+AlwaysActAsServerClassMachine -XX:+AlwaysPreTouch -XX:+DisableExplicitGC -XX:+UseNUMA -XX:NmethodSweepActivity=1 -XX:ReservedCodeCacheSize=400M -XX:NonNMethodCodeHeapSize=12M -XX:ProfiledCodeHeapSize=194M -XX:NonProfiledCodeHeapSize=194M -XX:-DontCompileHugeMethods -XX:MaxNodeLimit=240000 -XX:NodeLimitFudgeFactor=8000 -XX:+UseVectorCmov -XX:+PerfDisableSharedMem -XX:+UseFastUnorderedTimeStamps -XX:+UseCriticalJavaThreadPriority -XX:ThreadPriorityPolicy=1 -XX:AllocatePrefetchStyle=3 -XX:+UseG1GC -XX:MaxGCPauseMillis=37 -XX:+PerfDisableSharedMem -XX:G1HeapRegionSize=16M -XX:G1NewSizePercent=23 -XX:G1ReservePercent=20 -XX:SurvivorRatio=32 -XX:G1MixedGCCountTarget=3 -XX:G1HeapWastePercent=20 -XX:InitiatingHeapOccupancyPercent=10 -XX:G1RSetUpdatingPauseTimePercent=0 -XX:MaxTenuringThreshold=1 -XX:G1SATBBufferEnqueueingThresholdPercent=30 -XX:G1ConcMarkStepDurationMillis=5.0 -XX:G1ConcRSHotCardLimit=16 -XX:G1ConcRefinementServiceIntervalMillis=150 -XX:GCTimeRatio=99 -XX:+UnlockExperimentalVMOptions -XX:+UnlockDiagnosticVMOptions -XX:+AlwaysActAsServerClassMachine -XX:+AlwaysPreTouch -XX:+DisableExplicitGC -XX:+UseNUMA -XX:AllocatePrefetchStyle=3 -XX:NmethodSweepActivity=1 -XX:ReservedCodeCacheSize=400M -XX:NonNMethodCodeHeapSize=12M -XX:ProfiledCodeHeapSize=194M -XX:NonProfiledCodeHeapSize=194M -XX:-DontCompileHugeMethods -XX:+PerfDisableSharedMem -XX:+UseFastUnorderedTimeStamps -XX:+UseCriticalJavaThreadPriority -XX:+EagerJVMCI -Dgraal.TuneInlinerExploration=1 -Dgraal.CompilerConfiguration=enterprise```

</details>

<details>
    <summary>If we were to use Java >8 with GraalVM (EE's) Java Arguments and G1GC, it would look like this (Server)</summary>

```-Xmx8G -Xms8G -XX:+UnlockExperimentalVMOptions -XX:+UnlockDiagnosticVMOptions -XX:+AlwaysActAsServerClassMachine -XX:+AlwaysPreTouch -XX:+DisableExplicitGC -XX:+UseNUMA -XX:NmethodSweepActivity=1 -XX:ReservedCodeCacheSize=400M -XX:NonNMethodCodeHeapSize=12M -XX:ProfiledCodeHeapSize=194M -XX:NonProfiledCodeHeapSize=194M -XX:-DontCompileHugeMethods -XX:MaxNodeLimit=240000 -XX:NodeLimitFudgeFactor=8000 -XX:+UseVectorCmov -XX:+PerfDisableSharedMem -XX:+UseFastUnorderedTimeStamps -XX:+UseCriticalJavaThreadPriority -XX:ThreadPriorityPolicy=1 -XX:AllocatePrefetchStyle=3 -XX:+UseG1GC -XX:MaxGCPauseMillis=130 -XX:+UnlockExperimentalVMOptions -XX:+DisableExplicitGC -XX:+AlwaysPreTouch -XX:G1NewSizePercent=28 -XX:G1HeapRegionSize=16M -XX:G1ReservePercent=20 -XX:G1MixedGCCountTarget=3 -XX:InitiatingHeapOccupancyPercent=10 -XX:G1MixedGCLiveThresholdPercent=90 -XX:G1RSetUpdatingPauseTimePercent=0 -XX:SurvivorRatio=32 -XX:MaxTenuringThreshold=1 -XX:G1SATBBufferEnqueueingThresholdPercent=30 -XX:G1ConcMarkStepDurationMillis=5 -XX:G1ConcRSHotCardLimit=16 -XX:G1ConcRefinementServiceIntervalMillis=150 -XX:+UnlockExperimentalVMOptions -XX:+UnlockDiagnosticVMOptions -XX:+AlwaysActAsServerClassMachine -XX:+AlwaysPreTouch -XX:+DisableExplicitGC -XX:+UseNUMA -XX:AllocatePrefetchStyle=3 -XX:NmethodSweepActivity=1 -XX:ReservedCodeCacheSize=400M -XX:NonNMethodCodeHeapSize=12M -XX:ProfiledCodeHeapSize=194M -XX:NonProfiledCodeHeapSize=194M -XX:-DontCompileHugeMethods -XX:+PerfDisableSharedMem -XX:+UseFastUnorderedTimeStamps -XX:+UseCriticalJavaThreadPriority -XX:+EagerJVMCI -Dgraal.TuneInlinerExploration=1 -Dgraal.CompilerConfiguration=enterprise```

</details>

<details>
    <summary>If we were to use Java >8 with GraalVM (EE's) Java Arguments and ZGC, it would look like this</summary>

```-Xmx8G -Xms8G -XX:+UnlockExperimentalVMOptions -XX:+UnlockDiagnosticVMOptions -XX:+AlwaysActAsServerClassMachine -XX:+AlwaysPreTouch -XX:+DisableExplicitGC -XX:+UseNUMA -XX:NmethodSweepActivity=1 -XX:ReservedCodeCacheSize=400M -XX:NonNMethodCodeHeapSize=12M -XX:ProfiledCodeHeapSize=194M -XX:NonProfiledCodeHeapSize=194M -XX:-DontCompileHugeMethods -XX:MaxNodeLimit=240000 -XX:NodeLimitFudgeFactor=8000 -XX:+UseVectorCmov -XX:+PerfDisableSharedMem -XX:+UseFastUnorderedTimeStamps -XX:+UseCriticalJavaThreadPriority -XX:ThreadPriorityPolicy=1 -XX:AllocatePrefetchStyle=3 -XX:+UseZGC -XX:AllocatePrefetchStyle=1 -XX:-ZProactive -XX:+UseZGC -XX:AllocatePrefetchStyle=1 -XX:-ZProactive```

</details>

<br>

It is also possible to get Java 8 versions of GraalVM (EE) from the [21.X section on the Oracle site](https://www.oracle.com/downloads/graalvm-downloads.html), and use these arguments:
<details>
    <summary>If we were to use Java <=8 with GraalVM (EE's) Java Arguments, it would look like this</summary>

```-Xmx8G -Xms8G -XX:+UnlockExperimentalVMOptions -XX:+UnlockDiagnosticVMOptions -XX:+AlwaysActAsServerClassMachine -XX:+ParallelRefProcEnabled -XX:+DisableExplicitGC -XX:+AlwaysPreTouch -XX:+AggressiveOpts -XX:+UseFastAccessorMethods -XX:AllocatePrefetchStyle=1 -XX:ThreadPriorityPolicy=1 -XX:+UseNUMA -XX:+UseDynamicNumberOfGCThreads -XX:NmethodSweepActivity=1 -XX:ReservedCodeCacheSize=350M -XX:-DontCompileHugeMethods -XX:MaxNodeLimit=240000 -XX:NodeLimitFudgeFactor=8000 -XX:+UseFPUForSpilling -XX:+EnableJVMCI -XX:+UseJVMCICompiler -XX:+EagerJVMCI -Dgraal.TuneInlinerExploration=1 -Dgraal.CompilerConfiguration=enterprise -Dgraal.UsePriorityInlining=true -Dgraal.Vectorization=true -Dgraal.OptDuplication=true -Dgraal.DetectInvertedLoopsAsCounted=true -Dgraal.LoopInversion=true -Dgraal.VectorizeHashes=true -Dgraal.EnterprisePartialUnroll=true -Dgraal.VectorizeSIMD=true -Dgraal.StripMineNonCountedLoops=true -Dgraal.SpeculativeGuardMovement=true -Dgraal.InfeasiblePathCorrelation=true```

</details>

<br>

## GraalVM (EE) Mod Compatibility

**GraalVM (EE) 22.3.0 fixes all known Minecraft compatibility bugs**

If you run an older, Java 8-based version of GraalVM, there are some potential issues:

- `VectorizeSIMD` turns entities invisible with shader mods like Optifine, Iris or Occulus, but only under certain conditions. This will be fixed in GraalVM EE 22.3.0. See: https://github.com/oracle/graal/issues/4849
  - Be sure to set `-Dgraal.VectorizeSIMD` to `false` if you run shaders.

- GraalVM CE and EE both break constellation rendering in 1.16.5 Astral Sorcery. This is possibly related to the shader bug. See: https://github.com/HellFirePvP/AstralSorcery/issues/1963

I have not observed any server-side bugs yet.

If you run into any other mod issues you can trace back to GraalVM, please create a Github issue. Generally, you can work around them by disabling major `dgraal` optimization flags, or by finding the right function with `Dgraal.PrintCompilation=true`, and working around it with `-Dgraal.GraalCompileOnly=~...` once you find the miscompiled function.

<br>

Performance Mods
======

This is a **fantastic** repo for finding performance mods: https://github.com/NordicGamerFE/usefulmods

Instead of Optifine, I would recommend more compatible alternatives like Sodium + Iris or Rubidium + Oculus.

<br>

Linux
======
### Kernel
When using Linux, other kernels may outperform the original/base kernels.

An example of this is using the [linux-tkg](https://github.com/Frogging-Family/linux-tkg) build system which allows you to select certain optimization patches. However, it should be noted, the actual performance gain is not tested and in reality may not show any real gains.

<br>

NUMA
======

The flag `-XX:+UseNUMA` forces the enabling of NUMA.

`-XX:+UseNUMA` can be safely removed from AMD Ryzen MCM and Threadripper CPUs. The NUMA flag ensures that CPUs are able to access RAM uniformly, however, with AMD Ryzen MCM and Threadripper CPUs the cores already perform memory access uniformly. Typically, this flag may not even be needed as the Java Virtual Machine should now automatically detect if NUMA is actually needed.

There may be slight increases or decreases in performance based upon the usage of this flag, however, with modern CPUs there should not be too much of a difference, as well as based upon RAM.

<br>

Other Performance Tips
======

- Run your Minecraft servers on the Clear Linux OS - It's by far the most optimized linux distribution out-of-the-box, and it has some other nice features (like a stateless config system). It also runs clients on AMD/Intel GPUs [quite well](https://web.archive.org/web/20220916090057/https://docs.01.org/clearlinux/latest/tutorials/multi-boot/dual-boot-win.html).

- [Oracle Linux](https://www.oracle.com/linux/) is also a good choice for servers, since its reasonably well optimized out-of-the-box and has Graalvm (EE) available via the package manager.

- For Linux clients, Arch-based distros like CachyOS or EndeavorOS are excellent, as they have wide support for most hardware.

- Make sure the Minecraft client is using your dedicated GPU if you have one! Check the F3 tab, and force Minecraft to use it in the "**Windows Graphics Settings**", *not* the AMD/Nvidia control panel (as they don't seem to work well).

- Minecraft client linux users should check out [Minecraft Wayland](https://github.com/Admicos/minecraft-wayland).

- If you are running on an older system or have a low amount of memory, close everything in the background, including Discord, game launchers and your browser. Minecraft is resource intensive, and does not like other apps generating CPU interrupts or eating disk I/O, and memory.

<br>

Frequently Asked Questions
======

- Java versions above 17 have some mod incompatibilities so I cannot at the time recommend using them. However, they now reportedly work with most modpacks, but I'm not sure if there are any performance benefits.

- Java tweaks improve server performance and client stuttering, but they don't boost average client FPS much (if at all). For that, running correct/up-to-date graphics drivers and performance mods is far more [important](https://github.com/NordicGamerFE/usefulmods)

- This guide assumes you have a decent amount of spare RAM when running Minecraft. If your setup is RAM constrained, try removing the following arguments in particular: `-XX:NmethodSweepActivity=1 -XX:ReservedCodeCacheSize=400M -XX:NonNMethodCodeHeapSize=12M -XX:ProfiledCodeHeapSize=194M -XX:NonProfiledCodeHeapSize=194M`, and try the server G1GC arguments.

- IBM's OpenJ9 does save RAM, as its reputation would suggest, but is over 30% slower at server chunkgen in my tests. If there are any flags that make it competitive with OpenJDK, please open a discussion on Github or contact my [Discord](https://discord.gg/nptv2TwaD5)

- EXCEPTION_ACCESS_VIOLATION - This may be caused by a few different things
  - Ensure Minecraft is using your dedicated graphics card if you have one
  - Try updating graphics drivers and other drivers
  - Try restarting your computer and only running Minecraft and see if it works
  - Reinstall your Java Runtime Environment
  - Try reinstalling Minecraft
  - (Weird-edge case) If you are using only vanilla try installing Forge with or without mods and test

<br>

Flag Explanations
======
- Aikar G1GC flag [explanation](https://aikar.co/2018/07/02/tuning-the-jvm-g1gc-garbage-collector-flags-for-minecraft/)
- `-XX:+UnlockExperimentalVMOptions -XX:+UnlockDiagnosticVMOptions` simply unlock more flags to be used. These can be listed with the `-XX:+PrintFlagsFinal` and `-XX:+JVMCIPrintProperties` flags, see [Flag Dumps](Flag_Dumps)
- `-XX:G1MixedGCCountTarget=3`: This is how many oldgen gc blocks to target in "mixed" gc. These mixed collections are much slower, and the Minecraft client doesn't generate oldgen very quickly, so we can lower this value to 3, 2, or even 1 for shorter GC pauses.
- `-XX:+UseNUMA` enables optimizations for multisocket systems, if applicable. Not sure if this applies to MCM CPUs like Ryzen or Epyc, but its auto disabled if not applicable.
- `-XX:-DontCompileHugeMethods` *Allows* huge methods to be compiled. Modded Minecraft has some of these, and we don't care about higher background compiler CPU usage.
- `-XX:MaxNodeLimit=240000 -XX:NodeLimitFudgeFactor=8000` Enable optimization of larger methods. See [here](https://bugs.java.com/bugdatabase/view_bug.do?bug_id=8058148)
- `-XX:ReservedCodeCacheSize=400M -XX:NonNMethodCodeHeapSize=12M -XX:ProfiledCodeHeapSize=194M -XX:NonProfiledCodeHeapSize=194M` reserves more space for compiled code. All sections must "add up" to `ReservedCodeCacheSize`. I have observed modded Minecraft run into the default 250 megabyte limit with `XX:+PrintCodeCache`, but even if its not filled, the larger size makes eviction of compiled code less aggressive.
- `-XX:NmethodSweepActivity=1` (default 10) keeps "cold" code in the cache for a longer time. There is no risk of "filling up" the code cache either, as cold code is more aggressively removed as it fills up.
- ~~`-XX:+UseStringDeduplication`~~ This is a popular option, but not used here, as it's benching slower. Maybe its useful on low memory systems?
- `-XX:+UseFastUnorderedTimeStamps` Avoid system calls for getting the time. The impact of this will vary per system, but we aren't really concerned with logging timestamp accuracy.
- `-XX:+UseCriticalJavaThreadPriority` *Nothing* should preempt the Minecraft threads. GC and Compiler threads can wait.
- `-XX:ThreadPriorityPolicy=1` Use a wider range of thread priorities. Requires sudo on linux to work. Some JDKs (like Graal) enable this by default, but some don't.
- `-XX:G1SATBBufferEnqueueingThresholdPercent=30 -XX:G1ConcMarkStepDurationMillis=5 -XX:G1ConcRSHotCardLimit=16 -XX:G1ConcRefinementServiceIntervalMillis=150`: Optimizes G1GC's concurrent collection threads, still being [tested](https://research.spec.org/icpe_proceedings/2014/p111.pdf)
- `-XX:G1RSetUpdatingPauseTimePercent=0`: We want *all* this work to be done in the G1GC concurrent threads, not the pauses.
- `-XX:G1HeapWastePercent=18` Don't bother collecting from old gen until its above this percent. This avoids triggering slower "mixed" young generation GCs, which is fine since Minecraft (with sufficient memory) doesn't fill the old gen that fast. Idea from [here](https://www.reddit.com/r/Minecraft/comments/k9zb7m/tuning_jvm_gc_for_singleplayer/)
- `-XX:GCTimeRatio=99` As a goal, 1% of CPU time should be spent on garbage collection. Default is 12, which seems way too low. The default for Java 8 was 99.
- `-XX:AllocatePrefetchStyle=3` Generate one prefetch instruction per cache line. More aggressive prefetching is generally useful on newer CPUs with large caches. It seems to break ZGC. See [Github](https://github.com/openjdk/jdk/blob/bd90c4cfa63ba2de26f7482ed5d1704f9be9629f/src/hotspot/share/opto/macro.cpp#L1806)
- `-Dgraal.LoopRotation=true` A non default optimization, will probably be default soon.
- `-Dgraal.TuneInlinerExploration=1` Spend more time making inlining decisions. For Minecraft, we want the C2 compiler to be as slow and aggressive as possible.
- Most other `-Dgraal` arguments are enabled by default, and are either there as a sanity check, for debugging or as a failsafe (if, for instance, someone unknowingly disables JVCMI with some other flag).
- Many Java 8 flags (such as `-XX:MaxInlineLevel=15 -XX:MaxVectorSize=32`) are just copied from the Java 17 defaults. Others (like `+AggressiveOpts`) are only non-default in some older Java 8 builds.

Flags Under Consideration:
======
- More aggressive inlining, via `-Dgraal.BaseTargetSpending=160` (default 120) in Graal and some other flags in OpenJDK. CPUs with larger caches might benefit from this.
- OpenJDK flags which are disabled by default: `-XX:+AlignVector -XX:+OptoBundling -XX:+OptimizeFill -XX:+AlwaysCompileLoopMethods -XX:+EnableVectorAggressiveReboxing -XX:+EnableVectorSupport -XX:+OptoScheduling -XX:+UseCharacterCompareIntrinsics -XX:+UseCopySignIntrinsic -XX:+UseVectorStubs`
- ~~`-Dgraal.LSRAOptimization=true`~~ seems to hurt performance
- `-Dgraal.OptWriteMotion=true` and `graal.WriteableCodeCache=true`, which *do not* seem stable, but may be more stable in GraalVM 22.3.0
- Extreme `G1HeapWastePercent` values.

<br>

Benchmarks
======

A modernized overhaul of benchmarking is in-progress

<br>

Too Long Didn't Read (TLDR)/Summary
======

Minecraft Version >= 1.16.5 = Java 17
Minecraft Version < 1.16.5 = Java 8

If you do not know what Java version you are using, you are likely using a version of Java which only has the G1GC, in this case copy and paste the following into your JVM arguments for your client:

<details>
    <summary>Java 17</summary>

```-Xmx8G -Xms8G -XX:+UnlockExperimentalVMOptions -XX:+UnlockDiagnosticVMOptions -XX:+AlwaysActAsServerClassMachine -XX:+AlwaysPreTouch -XX:+DisableExplicitGC -XX:+UseNUMA -XX:NmethodSweepActivity=1 -XX:ReservedCodeCacheSize=400M -XX:NonNMethodCodeHeapSize=12M -XX:ProfiledCodeHeapSize=194M -XX:NonProfiledCodeHeapSize=194M -XX:-DontCompileHugeMethods -XX:MaxNodeLimit=240000 -XX:NodeLimitFudgeFactor=8000 -XX:+UseVectorCmov -XX:+PerfDisableSharedMem -XX:+UseFastUnorderedTimeStamps -XX:+UseCriticalJavaThreadPriority -XX:ThreadPriorityPolicy=1 -XX:AllocatePrefetchStyle=3 -XX:+UseG1GC -XX:MaxGCPauseMillis=37 -XX:+PerfDisableSharedMem -XX:G1HeapRegionSize=16M -XX:G1NewSizePercent=23 -XX:G1ReservePercent=20 -XX:SurvivorRatio=32 -XX:G1MixedGCCountTarget=3 -XX:G1HeapWastePercent=20 -XX:InitiatingHeapOccupancyPercent=10 -XX:G1RSetUpdatingPauseTimePercent=0 -XX:MaxTenuringThreshold=1 -XX:G1SATBBufferEnqueueingThresholdPercent=30 -XX:G1ConcMarkStepDurationMillis=5.0 -XX:G1ConcRSHotCardLimit=16 -XX:G1ConcRefinementServiceIntervalMillis=150 -XX:GCTimeRatio=99```

</details>

<details>
    <summary>Java 8</summary>

```-Xmx8G -Xms8G -XX:+UnlockExperimentalVMOptions -XX:+UnlockDiagnosticVMOptions -XX:+AlwaysActAsServerClassMachine -XX:+ParallelRefProcEnabled -XX:+DisableExplicitGC -XX:+AlwaysPreTouch -XX:+PerfDisableSharedMem -XX:+AggressiveOpts -XX:+UseFastAccessorMethods -XX:MaxInlineLevel=15 -XX:MaxVectorSize=32 -XX:+UseCompressedOops -XX:ThreadPriorityPolicy=1 -XX:+UseNUMA -XX:+UseDynamicNumberOfGCThreads -XX:NmethodSweepActivity=1 -XX:ReservedCodeCacheSize=350M -XX:-DontCompileHugeMethods -XX:MaxNodeLimit=240000 -XX:NodeLimitFudgeFactor=8000 -XX:+UseFPUForSpilling -Dgraal.CompilerConfiguration=community -XX:+UseG1GC -XX:MaxGCPauseMillis=37 -XX:+PerfDisableSharedMem -XX:G1HeapRegionSize=16M -XX:G1NewSizePercent=23 -XX:G1ReservePercent=20 -XX:SurvivorRatio=32 -XX:G1MixedGCCountTarget=3 -XX:G1HeapWastePercent=20 -XX:InitiatingHeapOccupancyPercent=10 -XX:G1RSetUpdatingPauseTimePercent=0 -XX:MaxTenuringThreshold=1 -XX:G1SATBBufferEnqueueingThresholdPercent=30 -XX:G1ConcMarkStepDurationMillis=5.0 -XX:G1ConcRSHotCardLimit=16 -XX:G1ConcRefinementServiceIntervalMillis=150 -XX:GCTimeRatio=99```

</details>



If you do know you are using a version of Java with ZGC, Shenandoah, or GraalVM support then you should check [ZGC](#zgc), [Shenandoah](#Shenandoah), or [GraalVM](#graalvm-enterprise-edition)


> Note: See [Launchers](#launchers) and [Memory Allocation](#memory-allocation) for important information

<br>

---

### [Credits](./Sources_Credits.md)

<br>

[Logo]: ../assets/Minecraft%20Performance%20Guide%20-%20Logo.png
[Banner]: ../assets/Minecraft%20Performance%20Guide%20-%20Banner.png
