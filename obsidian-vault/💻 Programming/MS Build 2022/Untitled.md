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

## MAUI Project Config

---

https://learn.microsoft.com/en-us/dotnet/maui/tutorials/notes-app/?tutorial-step=2

-   _MauiProgram.cs_
    
    This is a code file that bootstraps your app. The code in this file serves as the cross-platform entry point of the app, which configures and starts the app. The template startup code points to the `App` class defined by the _App.xaml_ file.
    
-   _App.xaml_ and _App.xaml.cs_
    
    Just to keep things simple, both of these files are referred to as a single file. There are generally two files with any XAML file, the _.xaml_ file itself, and a corresponding code file that is a child item of it in the **Solution Explorer**. The _.xaml_ file contains XAML markup and the code file contains code created by the user to interact with the XAML markup.
    
    The _App.xaml_ file contains app-wide XAML resources, such as colors, styles, or templates. The _App.xaml.cs_ file generally contains code that instantiates the Shell application. In this project, it points to the `AppShell` class.
    
-   _AppShell.xaml_ and _AppShell.xaml.cs_
    
    This file defines the `AppShell` class, which is used to define visual hierarchy of the app.
    
-   _MainPage.xaml_ and _MainPage.xaml.cs_
    
    This is the startup page displayed by the app. The _MainPage.xaml_ file defines the UI (user interface) of the page. _MainPage.xaml.cs_ contains the code-behind for the XAML, like code for a button click event.

---

Resources:

https://learn.microsoft.com/en-us/dotnet/architecture/maui/

https://learn.microsoft.com/en-us/dotnet/architecture/maui/accessing-remote-data

![[Enterprise-Application-Patterns-Using-.NET-MAUI.pdf]]