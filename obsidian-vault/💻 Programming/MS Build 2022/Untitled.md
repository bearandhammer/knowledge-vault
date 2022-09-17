# .NET MAUI
---

https://learn.microsoft.com/en-us/dotnet/maui/

---

- Create the sample Notes app as a guide.
- https://doumer.me/improve-http-request-performance-in-dotnet-maui-xamarin/

---

Quickstart followed:

https://learn.microsoft.com/en-us/dotnet/maui/get-started/first-app?tabs=vswin&pivots=devices-android

- Install workload.
- Create project.
- Installer emulator.
- And away!

---

Hardware acceleration (a must):

https://learn.microsoft.com/en-us/dotnet/maui/android/emulator/hardware-acceleration

For windows:

https://github.com/intel/haxm/releases

To check installation

```cmd
sc query intelhaxm
```

Stuck emulator:

```cmd
taskkill /F /IM "qemu-system-x86_64.exe" /T
```

---

Resources:

https://learn.microsoft.com/en-us/dotnet/architecture/maui/

https://learn.microsoft.com/en-us/dotnet/architecture/maui/accessing-remote-data

![[Enterprise-Application-Patterns-Using-.NET-MAUI.pdf]]