# HGUI : AREA OBJECT

<!-- Start Document Outline -->

* [INTRODUCTION](#introduction)
* [WHAT IS AN AREA OBJECT?](#what-is-an-area-object)
* [AREA OBJECT STRUCTURE](#area-object-structure)
* [ABOUT CALLBACK FUNCTIONS](#about-callback-functions)
* [AREA OBJECT METHODS](#area-object-methods)
	* [HGui.Area:New(options, object, userdata)](#hguiareanewoptions-object-userdata)
	* [AreaObj:Free()](#areaobjfree)
	* [AreaObj:Render()](#areaobjrender)
	* [AreaObj:Set(options, object, offset)](#areaobjsetoptions-object-offset)
* [AREA OBJECT FUNCTIONS](#area-object-functions)
	* [HGui.Area_FindByName(area_name)](#hguiarea_findbynamearea_name)

<!-- End Document Outline -->

## INTRODUCTION
An **Area Object** is an internal structure used to define and store window’s portions. These areas can react to user's input (active areas) or not (passive areas). Areas are also used to apply skins to the defined zone.

## WHAT IS AN AREA OBJECT?

An **Area Object** is a portion of a HGui window that can react (or not) to the user's input or events like a mouse click. It's also used to skin the area that the object defines. 
The **Area Object** is a building block of any gadget but can be used freely by the programmer for its own purposes, event to build custom gadgets.

## AREA OBJECT STRUCTURE
Below there is the Area Object structure with its default values.
```plaintext
HGui.Area = { }                                 Main Area class
  .Position = { }                               Area position table
    .x = 0                                      Area's horizontal position
    .y = 0                                      Area's vertical position
  .Size = { }                                   Area size table
    .w = 64                                     Area's width
    .h = 64                                     Area's height
  .Skin = { }                                   Area's skin definition table
  .Active = False                               Defines if it’s an active area (an area that reacts
                                                to events) or not
  .Window = Nil                                 Parent window object or window name, if this
                                                arguments is not specified the active window will be 
                                                used
  .Events = { }                                 Area's events (callback functions) table.
    .OnMouseOver = Function() EndFunction       Callback func. for Mouse Over events
    .OnMouseDown = Function() EndFunction       Callback func. for Left Mouse Click events
    .OnMouseUp   = Function() EndFunction       Callback func. for Left Mouse Release events
    .OnMouseOut  = Function() EndFunction       Callback func. for Mouse Out events
    .OnRightMouseUp = Function() EndFunction    Callback func. for Right Mouse Click events
  .Userdata = { }                               Userdata to pass to the callback functions, can be of
                                                any type
  .Object = Nil                                 Linked object (for example a gadget)
  .Private = { }                                Private data table
    .Button = Nil                               Attached button's id for active areas
    .Name = Nil                                 Attached button's name for active areas
```

Of course events are only processed for active areas.

## ABOUT CALLBACK FUNCTIONS

When you setup an **Active Area** with callback functions attached to one or more events, the callback function will be called with the following parameters:
```plaintext
msg
  .action                       Standard Hollywood event name (OnMouseUp, OnMouseOver, etc...)
  .ID                           Button id that triggered the event
  .x                            Horizontal position of the button
  .y                            Vertical position of the button
  .width                        Button’s width
  .height                       Button’s heigth
  .MouseDown                    True if the left mouse button is still down
  .RightMouseDown               True if the right mouse button is still down
  .MidMouseDown                 True if the middle mouse button is still down
  .TimeStamp                    TimeStamp of the triggered event
  .UserData                     Data relevant to the defined Area
    .ObjType                    HGui object type, in this case #HGUI_AREA
    .Object                     Area’s parent object
    .Area                       Area Object, if you have passed the userdata field when you have
                                created the Area, it will be stored here, don’t get confused with
                                the UserData passed by Hollywood!
```

To access **Area's userdata** you have to read : 
`msg.UserData.Area.userdata`

## AREA OBJECT METHODS

Here is a list of the available methods to manage the **Area objects**.
```plaintext
AreaObj = HGui.Area:New(options, object, userdata)
AreaObj:Free()
AreaObj:Render()
AreaObj:Set(options, object, offset)
```

#### HGui.Area:New(options, object, userdata)
Creates a new area with the given options, attached to the given object and with the specified userdata. Returns the created Area object.
All fields are optional.

```plaintext
INPUT
 options                A table with the the required options, basically it follow the structure
                        of the area object and you can selectively specify which item/value you 
                        want to ovveride.
 object                 An optional object (table pointer) you want to link to this area, generally
                        used to link the area with a parent gadget.
 userdata               An optional field (can be anything) to pass to the callback functons as
                        additional data

OUTPUT
 areaObject             A new area object

EXAMPLE
-------
Local myArea = HGui.Area:new(
     { position = { x = 10, y = 10 }, 
       size = { w = 100, h = 40 }, 
       active = True, 
       events = { onmousedown = Function() 
                                  DebugPrint("HELLO!") 
                                EndFunction}
       },
     Nil, 
     Nil) 
```
The example shows how to setup an area with no skin (invisible area) that reacts to left mouse clicks and print the “HELLO!” string everytime the left mouse button is pressend in the defined area.
Since we have not specified a window where the area must be created the currently active window will be used.


#### AreaObj:Free()
Free the AreaObj and its associated resources.

```plaintext
INPUT
 

OUTPUT
 result                 TRUE if the Area object was successfully free

EXAMPLE
-------
; Let's create a new Area object
Local myArea = HGui.Area:new(
     { position = { x = 10, y = 10 }, 
       size = { w = 100, h = 40 }, 
       active = True, 
       events = { onmousedown = Function() DebugPrint("HELLO!") EndFunction}
       },
     Nil, 
     Nil) 

; Free the created Area
myArea:Free()
```

#### AreaObj:Render()
Renders the AreaObj in the window it belogs applying the given skin if any.

```plaintext
INPUT


OUTPUT
 result                 TRUE if the Area was rendered without errors.

EXAMPLE
-------
; Create an Area object
Local myArea = HGui.Area:new(
     { position = { x = 10, y = 10 }, 
       size = { w = 100, h = 40 }, 
       active = True, 
       events = { onmousedown = Function() DebugPrint("HELLO!") EndFunction}
       },
     Nil, 
     Nil) 

; Render it
myArea:Render()
```

#### AreaObj:Set(options, object, offset)
Modify the Area object with the given **options** which can be any of the Area structure fields plus some more fields specified below. 
Object is used to change the linked parent object, while offset is to move the Area specifying coordinate offsets.

```plaintext
INPUT
 options                You have to pass a table here with all the structure fields you want to
                       modify, here is a list of supported arguments:
   recurse              True to recursively modify all parent object childs objects.
   position             A table with the new area position (absolute)
   x                    Horizontal position
   y                    Vertical position
   size                 A table with the new area size
   w                    Area width
   h                    Area height
   skin                 A table with the skin definition
   active               TRUE let the Area to react to events
   events               A table with the events to respond to (see the :new() method for more details).
     onMouseOver        Callback function
     onMouseOut         Callback function
     onMouseDown        Callback function
     onMouseUp          Callback function
     onRightMouseUp     Callback function
 object                 Parent object
 offset                 A table with the relative offsets
   x                    Horizontal offset
   y                    Vertical offset

OUTPUT
 result                 TRUE if there was no errors.

EXAMPLE
-------
; Create an Area object
Local myArea = HGui.Area:new(
     { position = { x = 10, y = 10 }, 
       size = { w = 100, h = 40 }, 
       active = True, 
       events = { onmousedown = Function() DebugPrint("HELLO!") EndFunction}
       },
     Nil, 
     Nil) 

; Move the area changing the horizontal coordinate adding 100 pixels
myArea:Set(
  { position =
    { x = 100 }
    })
```

## AREA OBJECT FUNCTIONS
There are also some utility functions suited for several tasks:

#### HGui.Area_FindByName(area_name)
This function is used to find an Area by its name, the name that is stored in `AreaObj.private.name` field, and it returns the Area object and its index in the global **HGui.Areas** table where all defined areas are gathered.
Names are unique random strings assigned at creation time, you can redefine them or read the assigned value in the field `AreaObj.Private.Name`

```plaintext
INPUT
 area_name              Specify here the Area name you want to find.

OUTPUT
 AreaObj                FALSE if the object was not found, otherwise the Area object will be
                        returned.
 AreaIndex              If the Area object was found its index in the global HGui.Areas table
                        will be also returned.

EXAMPLE
-------
; Create an Area object
Local myArea = HGui.Area:new(
     { position = { x = 10, y = 10 }, 
       size = { w = 100, h = 40 }, 
       active = True, 
       events = { onmousedown = Function() DebugPrint("HELLO!") EndFunction}
       },
     Nil, 
     Nil) 

; Retrieve the area name
Local areaName = myArea.Private.Name

; Retrieve the Area object & Index
Local foundObject, foundIndex = HGui.Area_FindByName(areaName)
```
The above example  is not really useful but if you rename your areas overwriting the `myArea.private.name` field for your own purposes you could find this function useful, the important thing is to have unique names!
