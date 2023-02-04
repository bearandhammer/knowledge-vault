
Maui.UITesting repo: https://github.com/Redth/Maui.UITesting

Forked this repo and then cloned, just to experiment.

Solution loaded: Microsoft.Maui.Automation.sln:

![[Pasted image 20230204132721.png]]

Just using this to confirm compilation/explore - will switch to VS Code after the fact.

![[Pasted image 20230204133044.png]]

VS updated - to get new SDKs.

C# Interactive Notebook preview - VS Code: https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.dotnet-interactive-vscode

.NET Interactive Notebooks -> Polyglot Notebooks.

https://andrewlock.net/exploring-dotnet-interactive-notebooks/

![[Pasted image 20230204134906.png]]

---

Jupyter Notebooks:

![[Pasted image 20230204142007.png]]


![[Pasted image 20230204142656.png]]


Solution -> Clean and rebuild (in release mode)...

C:\Program Files\dotnet\sdk\7.0.102\Sdks\Microsoft.NET.Sdk\targets\Microsoft.NET.Publish.targets(299,5): error NETSDK1094: Unable to optimize assemblies for performance: a valid runtime package was not found. Either set the PublishReadyToRun property to false, or use a supported runtime identifier when publishing. When targeting .NET 6 or higher, make sure to restore packages with the PublishReadyToRun property set to true

warning NU1701: Package 'Microsoft.WinAppDriver.Appium.WebDriver 1.0.1-Preview' was restored using '.NETFramework,Version=v4.6.1, .NETFramework,Version=v4.6.2, .NETFramework,Version=v4.7, .NETFramework,Version=v4.7.1, .NETFramework,Version=v4.7.2, .NETFramework,Version=v4.8, .NETFramework,Version=v4.8.1' instead of the project target framework 'net6.0'.

https://learn.microsoft.com/en-us/dotnet/core/compatibility/sdk/6.0/publish-readytorun-requires-restore-change

![[Pasted image 20230204151301.png]]

![[Pasted image 20230204151341.png]]

![[Pasted image 20230204152059.png]]

https://www.youtube.com/embed/9LxQwpjKxhE

![[Pasted image 20230204152317.png]]


`await driver.Start();` ->

![[Pasted image 20230204152800.png]]

API 33???

![[Pasted image 20230204152625.png]]

![[Pasted image 20230204154020.png]]


![[Pasted image 20230204161830.png]]

dib -> https://github.com/dotnet/interactive/issues/467

