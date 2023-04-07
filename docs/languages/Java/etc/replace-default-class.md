# drop-in replacement

## 

## Low Level Bytecode Intrusion/Manipulation
There's no way to accomplish this feature with default Java.

- [ASM and Javassist](https://newrelic.com/blog/best-practices/diving-bytecode-manipulation-creating-audit-log-asm-javassist)
- [Low intrusion](https://segmentfault.com/a/1190000039949038/en)

I'm trying to accomplish this with javaagent + byte-buddy/javassist.

### javaagent
[Java Agent](https://catsbi.oopy.io/6136946a-9139-4541-b2af-2af93bb634a5)  
[ClassLoadingStrategy.UsingLookup](https://stackoverflow.com/questions/72364303/redefining-an-unloaded-class-with-bytebuddy)
[redefine or rebase](https://stackoverflow.com/questions/42787286/redefine-a-class-using-byte-buddy)

#### premain

#### MANIFEST.MF
