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


*** UNFINISHED DOC ***


