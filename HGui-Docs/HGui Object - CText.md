# HGUI : CTEXT OBJECT



## INTRODUCTION
An **CText Object** is an internal structure used to store and draw text, it is associated with an **Area Object** to define where the text should be rendered.


## WHAT IS A CTEXT OBJECT?

**CText** stands for Custom Text an it’s an object used to represent and draw text using several effects. A **CText object** is a building block of any gadget but can be used freely by the programmer for its own purposes or to build custom gadgets.

## CTEXT OBJECT STRUCTURE
Below there is the Area Object structure with its default values.
```plaintext
HGui.CText = { }                                Main CText class
  .Name = Nil                                   Object name
  .First_Line = 1                               First line to display
  .Caption = {}                                 Text contents as a table of lines
  .Wordwrap = False                             Enable/Disable wordwrap
  .Window = Nil                                 Parent window object or name
  .Interline = 0                                Additional interline in pixels
  .Angle = 0                                    Text rotation angle
  .Encoding = HGui.TextEncoding                 Text encoding
  .Vert_Adjust = 0                              Vertical adjustment in pixels
  .Font = { }                                   Table that describes the text font
    .Name = #SANS                               Font name or Hollywood font constant
    .Size = 16                                  Font size
    .Style = #ANTIALIAS                         Font style, one or more Hollywood constants
    .Color = $000000                            Font color
    .Align = #HGUI_ALIGN_CENTER                 Font alignment (one or more HGui contants)
  .Effects = { }                                Table with text effect to apply
    .Edge = { }                                 Table describing the edge effect
      .Type = #NONE                             Constant definining the edge type
      .Size = 1                                 Edge size in pixel(s)
      .Color1 = $44444444                       Edge color 1
      .Color2 = $44FFFFFF                       Edge color 2
    .Shadow = { }                               Table describing the shadow effect
      .Type = #NONE                             Shadow type constant
      .Distance = 2                             Shadow distance in pixel(s)
      .Color = $55000000                        Shadow color
  .Margins = { }                                Table describing text margins
    .Top = 0                                    Top margin in pixel(s)
    .Bottom = 0                                 Bottom margin in pixel(s)
    .Left = 0                                   Left margin in pixel(s)
    .Right = 0                                  Right margin in pixel(s)
  .Area = Nil                                   Associated Area Object
```

For Alignment, Edge Type amd Shadow Type see HGui Constants document.


## CTEXT OBJECT METHODS

Here is a list of the available methods to manage the **CText objects**.
```plaintext
CTextObj = HGui.CText:New(options)
CTextObj:Free()
CTextObj:Render()
CTextObj:Set(options, object, offset)
```

#### HGui.CText:New(options)
Creates a new CText object with the given options, this object is tied to an Area object that you can specify or not, in the second case a new Area object will be created for you. Returns the created CText object.
All fields are optional.

```plaintext
INPUT
 options                A table with the the required options, basically it follow the structure
                        of the area object and you can selectively specify which item/value you 
                        want to ovveride.
   name                 Object name, must be unique or Nil to let the system assign one for you.
   caption              The text to display, can be a string or a table of strings
   first_line           First line to be display
   interline            Additional interline value, can be negative too, expressed in pixels.
   vert_adjust          Vertical adjustment for the rendering
   wordwrap             Wordwrap switch, TRUE to enable word wrapping.
   angle                Text rotation angle in degrees.
   font                 Font description table
     name               Font name, it can be also a font constant
     size               Font size in pixels
     style              Font style (Hollywood style constants)
     color              Text color
     align              Text alignment, one or a combination of the following constants:
                        #HGUI_ALIGN_LEFT, #HGUI_ALIGN_RIGHT, #HGUI_ALIGN_TOP, #HGUI_ALIGN_BOTTOM,
                        #HGUI_ALIGN_HCENTER, #HGUI_ALIGN_VCENTER, #HGUI_ALIGN_CENTER
   effects              Text effects definition
     edge               Edge effect
       type             Effect type, can be one of the following constants:
                          #NONE : Switch off the effect
                          #HGUI_TEXTEDGE_FLAT : Flat edge around the text
                          #HGUI_TEXTEDGE_RAISED : Raised effect
                          #HGUI_TEXTEDGE_RECESSED : Recessed effect
       size             Border's size in pixels
       color1           Color1 is used for:
                          Border color of the FLAT fx
                          Light edges for the RAISED fx
                          Dark edges for the RECESSED fx
       color2           Color2 is used for:
                          Dark edges for the RAISED fx
                          Light edges for the RECESSED fx
   shadow               Text shadow effect
     type               Shadow type/direction, can be one of the following constants:
                          #NONE : Switch off the effect
                          #SHDWNORTH, #SHDWNORTHEAST, #SHDWEAST, #SHDWSOUTHEAST, #SHDWSOUTH,
                          #SHDWSOUTHWEST, #SHDWWEST, #SHDWNORTHWEST
     distance           Shadow distance in pixels
     color              Shadow color
   margins              Text margins table
     top                Top margin in pixels
     bottom             Bottom margin in pixels
     left               Left margin in pixels
     right              Right margin in pixels
   window               The window this CText belongs to, can be the window's name or a window object,
                        if not specified the area will be linked to the currently active window.
   area                 An HGui.Area object where the CText will be rendered. You can specify an
                        existing Area object or a new one will be built for you. You have to specify
                        in the options the <position> table nad the <size> table to allow the system
                        to build the HGui.Area for you. <position> must have the <x> and <y> fields,
                        and <size> must have the <w> and <h> fields.
OUTPUT
 CTextObject            The created object

EXAMPLE
-------
 not yet
```


*** CONTINUARE DA QUA ***


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
