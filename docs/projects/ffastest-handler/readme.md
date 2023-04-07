# The One minifilter to rule them all! Acts like a Windows file operation handler.
  
  - Do you know copy handlers? It's way much better than that.  
    except you need to insall a `driver` rather than a `software`.
  - One thing you need to know is that this minifilter driver isn't 
    implemented with its own file operation technology. It uses `windows 
    command line utilities` to achieve the goals. 
> ..., That's my idea. Shamefully.

## Why do I(we) need this?

1. Windows file operation is way too slow. Hence,
   there are a lot of copy handlers out there.
2. I don’t want to use those copy handlers without an appropriate license.
3. I tried commercial software, freeware, open-source software. But none of 
   them satisfies me.

## What I tried?(I don’t remember well)

1. [Ultracopier](https://ultracopier.herman-brule.com/),
   [GitHub](https://github.com/alphaonex86/Ultracopier). I liked it with the 
   adjusted options. But no delete handler.
2. [FastCopy](https://fastcopy.jp/). It’s good also. But this doesn't
   replace Windows default behavior.
3. [TeraCopy](https://www.codesector.com/teracopy). It works. but 
   doesn't have adjustable options, that means no 
   further performance gain. It's commercial 
   for enterprise use but not good as much as it is known as one of the best 
   tools in this category.

## Candidates to implement.

1. [Shell Extensions](https://learn.microsoft.com/en-us/windows/win32/shell/shell-exts)
2. [API Hooking](https://learn.microsoft.com/en-us/windows/win32/winmsg/hooks)
3. [Detours](https://github.com/microsoft/detours)
4. [Windows minifilter Driver](https://learn.microsoft.com/en-us/windows-hardware/drivers/ifs/filter-manager-concepts)

## Techniques needed to be implemented the fastest file operation, I guess.

- I don't know much about this, and I didn't research a lot about it because
    I'll just utilize Windows command line tools.

1. [I/O Programming Techniques](https://learn.microsoft.com/en-us/windows-hardware/drivers/kernel/i-o-programming-techniques)
2. ??? ekjasll;sdfjl;skadjfklasdkl;jf;lkasdf


## What am I going to start with?

- [Windows minifilter Driver](https://learn.microsoft.com/en-us/windows-hardware/drivers/ifs/filter-manager-concepts)
- [Detours](https://www.microsoft.com/en-us/research/project/detours/?from=https://research.microsoft.com/sn/detours&type=exact)
- [frida](https://github.com/frida/frida)
- [Working with Shell Extensions](https://learn.microsoft.com/en-us/windows/win32/shell/shell-exts): cannot be used to monitor file 
  operations.

## Which APIs to hook

- NtQueryInformationFile: for a single file operation.
- NtQueryDirectoryFileEx: for a directory operation.
- 

## Which commands to utilize: a list of candidates.

- diskusage.exe: not generally available yet.
- robocopy.exe: [robocopy](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/robocopy)
- xcopy.exe: [xcopy](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/xcopy)
- [move.exe](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/move)
- [del.exe](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/del)
- [rmdir.exe](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/rmdir)
- [rd.exe](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/rd)

## References

[MSDN Samples](https://learn.microsoft.com/en-us/samples/browse/?redirectedfrom=MSDN-samples)
[Code Example on the GitHub](https://github.com/microsoftarchive/msdn-code-gallery-microsoft/tree/master/OneCodeTeam/C%2B%2B%20Windows%20Shell%20copy%20hook%20handler%20%28CppShellExtCopyHookHandler%29/%5BC%2B%2B%5D-C%2B%2B%20Windows%20Shell%20copy%20hook%20handler%20%28CppShellExtCopyHookHandler%29/C%2B%2B)