# HOLLYWOOD-MAL Libraries
**This is a collection of libraries I coded to help myself with my projects**

> Author  : Fabio Falcucci (Allanon)  
> Contact : info@a-mc.biz  
> License : Freeware  

If you like my work and you want to buy me a coffee you can support me on Patreon https://www.patreon.com/Allanon71  or with PayPal to mailto:hijoe@tin.it   
:D

# IMPORTANT NOTE
From now (04/08/2020) I'm putting libraries using a global include file called **+Includes.hws** where all library names are defined along with their path, in order to run the examples you need to setup the variable **#INC_PATH** with the absolute path where you have saved/cloned the libraries, if you do this you will be able to run all the examples with a double click, for example let's suppose you have cloned the entire repository into the following path : `C:/MyHollywoodStuff/Libs/`  
All you have to do is:  
+ Open the file `+Includes.hws`  
+ Edit the line `Const #INC_PATH     = ""`  
+ Putting the absolute location, in our case `C:/MyHollywoodStuff/Libs/`  
+ Save the edited file  
+ You are ready!

---

# Lib-Helpers
 **Hollywood-MAL Helpers Library**
 
 This library includes a collection of common utility functions and methods, please refer to the **helpers.html** file fo a detailed description.

CONTENTS
```plaintext
:: BUFFERED STRING OBJECT ::
HL.BufferedString:AddChar()
HL.BufferedString:AddString()
HL.BufferedString:Get()
HL.BufferedString:New()
HL.BufferedString:PrepareForRead()
HL.BufferedString:Read()
HL.BufferedString:Set()

:: COLOR OBJECT ::
HL.Color:Brighten()
HL.Color:Clone()
HL.Color:Darken()
HL.Color:New()
HL.Color:fromARGB()
HL.Color:fromValue()
HL.Color:toARGB()
HL.Color:toRGB()
HL.GetRndColor()

:: STRINGS ::
HL.Capitalize()
HL.CutBetweenLimits()
HL.CutStringLeft()
HL.CutStringRight()
HL.GetBetweenLimits()
HL.GetReversedDateTime()
HL.GetRndName()
HL.SizeString()

:: NUMBERS ::
HL.RoundBig()
HL.Value2Perc()

:: CONVERSIONS ::
HL.Convert.BytesTo()
HL.Convert.ForTextout()
HL.Convert.HTML2Hollywood()
HL.Convert.HTMLAmper2UTF8()
HL.Convert.HTMLTag2HollywoodTag()
HL.Convert.Unicode2UTF8()

:: INPUT ::
HL.Input.CheckJoystick()
HL.Input.CheckKeyboard()
HL.WaitForAction()

:: MISC ::
HL.IsNil()
HL.IsNotNil()
HL.LineHook.Enable()
HL.LineHook.Disable()
HL.NBWait()
HL.ParseRunArgs()
HL.RestartApp()
 ```
 
# Lib-Easing
 **Hollywood-MAL Easing Library**
 
 Easing library is an include file for Hollywood able to create very smooth transitions between values so you can use it to animate almost anything like: graphical objects, colors, values, and any value you  need to be smoothly changed into another value.
 For detailed informations have a look at **easing.md** file.
 
CONTENTS
```plaintext
tween.start(time, subject, target, easing, callback, ...)
tween.reset(id)
tween.resetAll()
tween.update(dt)
tween.stop(id, callback)
tween.stopAll(callback)
tween.count()
tween.TEST()
```

# Lib-Tables  
 **Hollywood-MAL Tables Library**
 
 Tables library is an include file for Hollywood with several functions to manipulate tables, including comparisons, merge, set, sort, push, shift and many others. Please have a look at the file **tables.md** for more informations.
 
 CONTENTS
 ```plaintext
 :: TABLE COMPARISONS ::
 TB.Compare()
 TB.CompareScore()
 TB.Item.Comapare()
 TB.Item.Exists()
 TB.Item.Find()
 TB.Item.IsNil()
 
 :: TABLE CONVERSIONS ::
 TB.Convert.String2Table()
 TB.Convert.Table2String()
 TB.Serialize()
 TB.Deserialize()
 
 :: TABLE HANDLING ::
 TB.Fill()
 TB.Interpolate()
 TB.Join()
 TB.Merge()
 TB.PushDown()
 TB.PushDown()
 TB.Reindex()
 TB.ReplaceChars()
 TB.Set()
 TB.ShiftDown()
 TB.ShiftUp()
 TB.Sort()
 
 :: MISC ::
 TB.Copy()
 TB.Count()
```

# Lib-Debug
 **Hollywood-MAL Debug Library**
 
 Debug library is a library developed to help debugging session, it can be used to
 generate debug output to the console or to a one or more files, both debug output can use ANSI colors or plain text.
 
 Debug library can manage one or more debug channels so that you are able to switch
 on or off single channels and reduce the amount of output to analyze, this is very useful for complex programs involving several includes or libraries.
 
 If you have an ANSI capable terminal debug messages can be colored to help
 you identify errors and warning in no time.
 
 Debug library has the ability to show nested messages, this is incredibly useful
 when you have recursive functions and external library calls: without a proper
 output formatting a standard debug session could become a pain.
 
 You can output tables too, and they are formatted and idented properly to let
 you look easily at their contents.
 
CONTENTS
```plaintext
 :: CONSOLE DEBUG ::
 DBG.Console.AddChannel()
 DBG.Console.Disable()
 DBG.Console.Enable()
 DBG.Console.Out()
 DBG.Console.RemoveChannel()
 DBG.Console.SkipNormalLevel()
 
 :: FILE DEBUG ::
 DBG.Log.Disable()
 DBG.Log.Enable()
 DBG.Log.Out()
 
 :: MISC ::
 DBG.DumpTable()
```

# Lib-ANSI
 **Hollywood-MAL ANSI Library**
 
   Ansi library is an include file for Hollywood that will help you to 
 manage ANSI escape codes so you can print colored text in the console 
 of your host system.
 
   I’ve developed this library to have an invaluable help while I’m 
 debugging applications because this way I’m able to spot on the fly 
 errors and/or warning messages that are hilighted from the rest of the
 messages.
 
   Of course you need that your host system console is able to understand
 ANSI ascape codes, but almost any OS is able to do that… except 
 Windows! 
 For the Windows OS you need to install any thirdy party 
 application to accomplish the task, on my development machine, running
 Windows 10, I’m using **ansicon** program to make use of ANSI codes.

CONTENTS
```plaintext
 :: ANSI ::
 Ansi.GetClearCharacters()
 Ansi.GetCursorDown()
 Ansi.GetCursorLeft()
 Ansi.GetCursorMove()
 Ansi.GetCursorRight()
 Ansi.GetCursorUp()
 Ansi.GetDeleteCharacters()
 Ansi.GetDeleteLines()
 Ansi.GetInsertBlankLines()
 Ansi.GetRndBGColor()
 Ansi.GetRndFGColor()
 Ansi.Set()
 
 :: TERM OBJECT ::
 Term.App:ClearInfo()
 Term.App:ClearStatus()
 Term.App:ClearWarning()
 Term.App:GridView()
 Term.App:MenuAdd()
 Term.App:New()
 Term.App:Progress()
 Term.App:SetInfo()
 Term.App:SetStatus()
 Term.App:SetWarning()
 Term.App:ShowInput()
 Term.App:ShowMenu()
 Term.App:ShowMessage()
 Term.App:Start()
 Term.App:alignNumber()
 
 :: TERM FUNCTIONS ::
 Term.CTLine()
 Term.Clear()
 Term.GetSize()
 Term.Input()
 Term.Line()
 Term.Print()
 Term.PrintAt()
 Term.SetTermSize()
 
 :: TERM DRAWING ::
 Term.Draw.Box()
 Term.Draw.FBox()
 Term.Draw.HLine()
 Term.Draw.VLine()
```

# Lib-GFX
**Hollywood-MAL GFX Library**
 
  GFX library is an include file for Hollywood that helps with common
graphical-related operations. Some example are provided inside the library as functions, look at the bottom of the source code.

 **CONTENTS**
 ```plaintext
 :: BACKGROUND UTILITIES ::
 - GFX.BG.Setup()
 - GFX.BG.Show()
 - GFX.BG.Free()

 :: BRUSH UTILITIES ::
 - GFX.Brush.HShift()
 - GFX.Brush.VShift()

 :: DISPLAY UTILITIES ::
 - GFX.DisplayExists()
 - GFX.GetHostSize()
 - GFX.SafeClipRegion()
 
 :: OUTPUT DEVICE UTILITIES ::
 - GFX.OutputDevice.EndSelect()
 - GFX.OutputDevice.Select()
 - GFX.OutputDevice.GetCurrent()
 
 :: FONT OBJECT ::
 - GFX.Font:New()
 - GFX.Font:Save()
 - GFX.Font:Load()
 - GFX.Font:Apply()
 - GFX.Font:Set()
 
 :: IMAGE OBJECT ::
 - GFX.Image:Add()
 - GFX.Image:Clone()
 - GFX.Image:Draw()
 - GFX.Image:NewLayer()
 - GFX.Image:Reload()
 - GFX.Image:Remove()
 - GFX.Image:Resize()
 - GFX.Image.Get()
 - GFX.Image.List()
 
 :: IMAGE FX UTILITIES ::
 - GFX.ImageFX.AddFrame()
 - GFX.ImageFX.Reflex()
 - GFX.ImageFX.Scale()

 :: TEXT UTILITIES ::
 - GFX.Text.DeTagger()
 - GFX.Text.GetWidth()
 - GFX.Text.WordWrap()
```
# Lib-FS
**Hollywood-MAL FS Library**

  FS is a library developed to help with common file system related
 operations.

**CONTENTS**
```plaintext
 :: MISC ::
 FS.AppDataLocation()
 FS.CutLastFolder()
 FS.OpenFolder()
 FS.ParseFilename()
 
 :: TASKS ::
 FS.Task.IsRunning()
 FS.Task.Kill()
 
 :: SCRIPTS ::
 FS.Build_Script()
 FS.ExecuteSynch_SCript()
 FS:Execute_Script()
 
 :: CONFIG FILES ::
 FS.Config.Add()
 FS.Config.Load()
 FS.Config.Remove()
 FS.Config.Set()
 FS.Config.Write()
 
 :: FILES ::
 FS.Files.ChangeExistingName()
 FS.Files.CheckLastChar()
 FS.Files.ClearCache()
 FS.Files.Delete()
 FS.Files.ExtractFromZip()
 FS.Files.Find()
 FS.Files.FindByCRC32()
 FS.Files.GetDirectories()
 FS.Files.GetExtention()
 FS.Files.GetLastLine()
 FS.Files.GoDirectoryUp()
 FS.Files.IsAvailable()
 FS.Files.IsPathRelative()
 FS.Files.LoadToTable()
 FS.Files.Open()
 FS.Files.ReadFloat()
 FS.Files.ReadString()
 FS.Files.ReadTable()
 FS.Files.RemoveExtention()
 FS.Files.SaveFromTable()
 FS.Files.Script_Build()
 FS.Files.Search()
 FS.Files.ToTable()
 FS.Files.Validate()
 FS.Files.WriteInt()
 FS.Files.WriteString()
 FS.Files.WriteTable()
 FS.Files.applyQuotes()
 
 :: INI FILES ::
 FS.Ini.ReadValue()
 
 :: TEXT FILES ::
 FS.TxtFiles.InsertBefore()
 
 :: VOLUMES ::
 FS.Volumes.ClearCache()
 FS.Volumes.Get()
 FS.Volumes.GetPart()
 FS.Volumes.IsAvailable()
 FS.Volumes.Monitor_Check()
 FS.Volumes.Monitor_Start()
 FS.Volumes.Monitor_Stop()
```
 
# Lib-G2D
 **Hollywood-MAL G2D Library**
 
 G2D Library is an include file for Hollywood that helps with graphics
 related objects and functions, it also has a full-featured skinning 
 system.
 
CONTENTS
```plaintext
 :: POINT 2D OBJECT ::
 G2D.Point:New()
 G2D.Point:Distance()
 G2D.Point:DotProduct()
 G2D.Point:MidPoint()
 G2D.Point:Normal2D()
 G2D.Point:Normalize()
 G2D.Point:Rotate()
 G2D.Point:Scale()
 
 :: POLYGON OBJECT ::
 G2D.Poly:New()
 G2D.Poly:Collide()
 G2D.Poly:Draw()
 G2D.Poly:Project()
 G2D.Poly:SetAnchor()
 G2D.Poly:SetAngle()
 G2D.Poly:SetScale()
 G2D.Poly:Translate()
 
 :: AREA OBJECT ::
 G2D.Area:New()
 G2D.Area:Box()
 G2D.Area:FillColor()
 G2D.Area:FillPattern()
 G2D.Area:Move()
 G2D.Area:Scale()
 G2D.Area:SkinBevel()
 G2D.Area:SkinColor()
 G2D.Area:SkinFitMax()
 G2D.Area:SkinFitMin()
 G2D.Area:SkinGradient()
 G2D.Area:SkinHPattern()
 G2D.Area:SkinHPattern3S()
 G2D.Area:SkinMulti()
 G2D.Area:SkinPattern()
 G2D.Area:SkinPattern9S()
 G2D.Area:SkinQuick()
 G2D.Area:SkinShades()
 G2D.Area:SkinStretch()
 G2D.Area:SkinVPattern()
 G2D.Area:SkinVPattern3S()
 G2D.Area:Snapshot()
 
 :: BG Picture ::
 G2D.BGPic.CreateSkinned()
``` 

 ---
 Latest update: 11/08/2020
 ---