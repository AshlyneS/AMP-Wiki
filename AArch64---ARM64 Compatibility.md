AMP itself runs natively on AArch64 / ARM64 systems - but most applications do not. Below are those that we have tested and got working in AMP in AArch64. AMP only supports ARM on Linux, there are no plans to introduce a native Windows ARM version at this moment in time.

Applications that only run using Cross-Platform eXecution (CPx) have a large performance overhead, and are not recommended on low-power ARM systems such as the Raspberry Pi and generally perform best on server-class hardware.

As a general rule, applications that run via Java or Mono can be made to run on ARM hardware without significant work.

|Application|Native|Emulated|Notes|
|-|-|-|-|
|Minecraft - Java Edition|✅|❌|Runs normally using standard Java packages|
|Minecraft - Bedrock Edition|❌|✅|Runs using AMP CPx emulation|
|Factorio|❌|✅|Runs using AMP CPx emulation|
|Valheim|❌|✅|Runs using AMP CPx emulation (CPx2 required)|