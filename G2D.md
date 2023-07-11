# G2D LIBRARY for HOLLYWOOD-MAL

```plain
Author  : Fabio Falcucci (Allanon)
Contact : info@a-mc.biz
License : Freeware
Support : PayPal (hijoe@tin.it), Patreon (https://www.patreon.com/Allanon71)
Website : a-mc.biz
Github  : Github.com/Allanon71
Links   : https://linksta.cc/@Allanon
Dependancies : Helpers, Easing, Tables, Gfx
```

If you like my work and you want to buy me a coffee you can support me on Patreon https://www.patreon.com/Allanon71  or with PayPal to hijoe@tin.it


---

# G2D Library introduction

I developed this library mainly because I needed a skin system for my bigger project HGui.
I started coding the Area Object, a simple object used to define a square area into the screen but the power of this simple object are in its methods.
I included many methods you can use to skin, fill and manipulate area objects.
The skin system is very powerful, it supports single skin types but also multi-layered skins allowing you to create very complex textures.
I'm' really satistied about the skin system, HGui can mimic almost any system with the right skin and you can use this library for your very own purposes.

But it's not all about the skin system because this library also includes very handy objects to handle 2d points and polygons. 

Polygon objects have some nice collision detection methods I used in my GLFX Engine.


---

# INDEX
## POINT 2D OBJECT
- [G2D.Point:New(x, y)](#g2dpointnewx-y)
- [G2D.Point:Distance(point2D)](#g2dpointdistancepoint2d)
- [G2D.Point:DotProduct(point2D)](#g2dpointdotproductpoint2d)
- [G2D.Point:MidPoint(point2D, newObject)](#g2dpointmidpointpoint2d-newobject)
- [G2D.Point:Normal2D(point2D, s)](#g2dpointnormal2dpoint2d-s)
- [G2D.Point:Normalize()](#g2dpointnormalize)
- [G2D.Point:Rotate(point, angle)](#g2dpointrotatepoint-angle)
- [G2D.Point:Scale(point, scaleW, scaleH)](#g2dpointscalepoint-scalew-scaleh)
 
## POLYGON OBJECT
- [G2D.Poly:New(params)](#g2dpolynewparams)
- [G2D.Poly:Collide(poly2)](#g2dpolycollidepoly2)
- [G2D.Poly:CollideDot(dot)](#g2dpolycollidedotdot)
- [G2D.Poly:Draw()](#g2dpolydraw)
- [G2D.Poly:Project(axis)](#g2dpolyprojectaxis)
- [G2D.Poly:SetAnchor(anchorX, anchorY)](#g2dpolysetanchoranchorx-anchory)
- [G2D.Poly:SetAngle(angle)](#g2dpolysetangleangle)
- [G2D.Poly:SetScale(scaleWidth, scaleHeight)](#g2dpolysetscalescalewidth-scaleheight)
- [G2D.Poly:Translate(x, y)](#g2dpolytranslatex-y)
- [G2D.TEST_Poly()](#g2dtest_poly)
 
## AREA OBJECT
- [G2D.Area:New(x, y, w, h)](#g2dareanewx-y-w-h)
- [G2D.Area:Box(color, offset)](#g2dareaboxcolor-offset)
- [G2D.Area:FillColor(color)](#g2dareafillcolorcolor)
- [G2D.Area:FillPattern(brushID)](#g2dareafillpatternbrushid)
- [G2D.Area:Move(x, y, absolute)](#g2dareamovex-y-absolute)
- [G2D.Area:Scale(WFactor, HFactor)](#g2dareascalewfactor-hfactor)
- [G2D.Area:SkinBevel(colors, aspect)](#g2dareaskinbevelcolors-aspect)
- [G2D.Area:SkinColor(color, alpha)](#g2dareaskincolorcolor-alpha)
- [G2D.Area:SkinFitMax(brush, offset, alpha, align)](#g2dareaskinfitmaxbrush-offset-alpha-align)
- [G2D.Area:SkinFitMin(brush, offset, alpha, align, border)](#g2dareaskinfitminbrush-offset-alpha-align-border)
- [G2D.Area:SkinGradient(col1, col2, alpha, angle)](#g2dareaskingradientcol1-col2-alpha-angle)
- [G2D.Area:SkinHPattern(brush, offset, alpha)](#g2dareaskinhpatternbrush-offset-alpha)
- [G2D.Area:SkinHPattern3S(brush, sectors, alpha, vadapt)](#g2dareaskinhpattern3sbrush-sectors-alpha-vadapt)
- [G2D.Area:SkinMulti(levels, offset)](#g2dareaskinmultilevels-offset)
- [G2D.Area:SkinPattern(brush, offset, alpha, size)](#g2dareaskinpatternbrush-offset-alpha-size)
- [G2D.Area:SkinPattern9S(brush, sectors, alpha, vadapt)](#g2dareaskinpattern9sbrush-sectors-alpha-vadapt)
- [G2D.Area:SkinQuick(skinBrush, Mode)](#g2dareaskinquickskinbrush-mode)
- [G2D.Area:SkinShades(colList, angle)](#g2dareaskinshadescollist-angle)
- [G2D.Area:SkinStretch(brush, offset, alpha, stretch_fix)](#g2dareaskinstretchbrush-offset-alpha-stretch_fix)
- [G2D.Area:SkinVPattern(brush, offset, alpha)](#g2dareaskinvpatternbrush-offset-alpha)
- [G2D.Area:SkinVPattern3S(brush, sectors, alpha, vadapt)](#g2dareaskinvpattern3sbrush-sectors-alpha-vadapt)
- [G2D.Area:Snapshot(BGPic)](#g2dareasnapshotbgpic)
 
# MISC
- [G2D.BGPic.CreateSkinned(width, height, skin_struct)](#g2dbgpiccreateskinnedwidth-height-skin_struct)



---

# HISTORY
```plain

11/07/2023 : Docs refreshed as G2D.md
--/07/2023 : Optimizations & Documentation
12/08/2020 : Fixed a bug in G2D.Area:SkinFitMin() method

```


---

# CLASSES

---

## Class G2D.Area
```plain
G2D.Area =  {}
G2D.Area.x = 0
G2D.Area.y = 0
G2D.Area.w = 50
G2D.Area.h = 50

```

---

## G2D.Area methods

---

### G2D.Area:SkinMulti(levels, offset)
```plain
result = G2D.Area:SkinMulti(levels, offset)

This method is used to skin the area object using one or more skin layers
defined in the 'levels' table.
With this method you can apply multiple skin layers to an area object.

INPUT
  levels : [TBL] Table describing each skin layer to apply to the area, each
           entry must have the following fields:
             area : [TBL] This table represent a sub-area to adjust the level's
                    position and size, values specified here will be added to
                    the corresponding areaObj fields we have to skin.
                    This parameter is optional. If specified, the table, must
                    have the fields : x, y, w, h
             type : [NUM] This field is used to specify what skin mode must
                    be used for this layer, it can be one of the following:
                      GFX.SkinType_Stretch
                      GFX.SkinType_Pattern
                      GFX.SkinType_FitMax
                      GFX.SkinType_FitMin
                      GFX.SkinType_Color
                      GFX.SkinType_Gradient
                      GFX.SkinType_Shades         
                      GFX.SkinType_VPattern
                      GFX.SkinType_HPattern
                      GFX.SkinType_VPattern3S
                      GFX.SkinType_HPattern3S
                      GFX.SkinType_Pattern9S
                      GFX.SkinType_Bevel
             params : [TBL] This is a table with further values needed by each
                      skin mode, below, for each skin type, will be listed all
                      the fields that must be provided in this table:
                       
                       ** GFX.SkinType_Stretch **
                       brush : Brush id or brush filename
                       offset : Skin offset, must have:
                         x : Offset X
                         y : Offset Y
                         alpha : Transparency or #NONE
                        stretch_fix : See notes at the top of this module

                       ** GFX.SkinType_Pattern **
                       brush : Brush id or brush filename
                       offset : Skin offset, must have:
                         x : Offset X
                         y : Offset Y
                       alpha : Transparency or #NONE or any positive value to override
                               brush's alpha channel.
                       size : Optional size of the single tile, is specified, must have:
                         w : Horizontal size
                         h : Vertical size

                       ** GFX.SkinType_FitMax **
                       brush : Brush id or brush filename
                       offset : Skin offset, must have:
                         x : Offset X
                         y : Offset Y
                       alpha : Transparency or #NONE or any positive value to override
                               brush's alpha channel.
                       align : Horizontal skin alignment, can be #LEFT, #CENTER, #RIGHT

                       ** GFX.SkinType_FitMin **
                       brush : Brush id or brush filename
                       offset : Skin offset, must have:
                         x : Offset X
                         y : Offset Y
                       alpha : Transparency or #NONE or any positive value to override
                               brush's alpha channel.
                       align : Horizontal skin alignment, can be #LEFT, #CENTER, #RIGHT
                       border : Borders color

                       ** GFX.SkinType_Color **
                       color : Solid color to use
                       alpha : Transparency or #NONE or any positive value.

                       ** GFX.SkinType_Gradient **
                       color1 : Gradient's starting color
                       color2 : Gradient's ending color
                       alpha : Transparency or #NONE or any positive value.
                       angle : Gradient's angle

                       ** GFX.SkinType_Shades ***
                       ColorList : Table used to define the shades, each entry
                                   must have the following fields:
                                     Color : Color in RRGGBB notation
                                     Weight : Band ColorN <-> ColorN+1                                                  weight
                                     Alpha : Color transparency level
                       angle : Shades's angle. Actually only 0, 90, 180, 270, ... 
                               are rendered correctly.
  
                       ** GFX.SkinType_VPattern **
                       brush : Brush id or brush filename
                       offset : Skin offset, must have:
                         x : Offset X
                         y : Offset Y
                       alpha : Transparency or #NONE or any positive value to override
                               brush's alpha channel.

                       ** GFX.SkinType_HPattern **
                       brush : Brush id or brush filename
                       offset : Skin offset, must have:
                         x : Offset X
                         y : Offset Y
                       alpha : Transparency or #NONE or any positive value to override
                               brush's alpha channel.

                       ** GFX.SkinType_VPattern3S **
                       brush : Brush id or brush filename            
                       sectors : Table describing skin sectors:        
                         top : Top sector                           
                           start : Starting y coordinate           
                           height   sector's height                 
                         middle : Middle sector                        
                           start : Starting y coordinate           
                           height : sector's height                 
                         bottom : Bottom sector                        
                           start : Starting y coordinate           
                           height : sector's height                 
                       alpha : Transparency or #NONE or any positive value to override
                               brush's alpha channel.            
                       vadapt : Adapt the brush size vertically       

                       ** GFX.SkinType_HPattern3S **
                       brush : Brush id or brush filename            
                       sectors : Table describing skin sectors:        
                         left : Left sector                           
                           start : Starting y coordinate           
                           height   sector's height                 
                         middle : Middle sector                        
                           start : Starting y coordinate           
                           height : sector's height                 
                         right : Right sector                        
                           start : Starting y coordinate           
                           height : sector's height                 
                       alpha : Transparency or #NONE or any positive value to override
                               brush's alpha channel.            
                       vadapt : Adapt the brush size horizontally       

                       ** GFX.SkinType_Pattern9S **
                       brush : Brush id or brush filename            
                       sectors : Table describing skin sectors:        
                         left : Left sector                           
                           start : Starting y coordinate           
                           height   sector's height                 
                         hmiddle : Horizontal/Middle sector                        
                           start : Starting y coordinate           
                           height : sector's height                 
                         right : Right sector                        
                           start : Starting y coordinate           
                           height : sector's height                 
                         top : Top sector                           
                           start : Starting y coordinate           
                           height   sector's height                 
                         vmiddle : Vertical/Middle sector                        
                           start : Starting y coordinate           
                           height : sector's height                 
                         bottom : Bottom sector                        
                           start : Starting y coordinate           
                           height : sector's height                 
                       alpha : Transparency or #NONE or any positive value to override
                               brush's alpha channel.            
                       vadapt : Adapt the brush size

                       ** GFX.SkinType_Bevel **
                       colors : Colors table                          
                         Light : Light color                          
                         Dark : Dark color                           
                         Middle : Middle color (NIL for empty bevels)  
                       aspect : Further aspect options                
                         fx : Can be one of the following: GFX.BevelFx_Raised. GFX.BevelFx_Recessed, GFX.BevelFx_Flat
                         height : Border's height                      
                         type : Bevel type, one of the following: GFX.BevelType_Standard, GFX.BevelType_Sunken
  offset : [TBL] Optional table with the global skin offset for all layers
           that needs it. It must hold the fields 'x' and 'y'.

OUTPUT
  result : [BLN] Returns TRUE if the operation has been completed without errors.

```

---

### G2D.Area:SkinHPattern3S(brush, sectors, alpha, vadapt)
```plain
result = G2D.Area:SkinHPattern3S(brush, sectors, alpha, vadapt)

This method is used to skin the area object using 'brush'. 
The brush should be an horizontal strip subdivided in three sectors,
described by the 'sectors' table).
The left side and right sides are fixed sized while the middle part will
be used to fill the area width repeating the middle part, or, if 'vadapt'
is set to TRUE, the middle part will be stretched.
You can control transparency with 'alpha' overriding the brush alpha channel,
if defined.

INPUT
  brush   : [ID|STR] The brush to use to skin the area. It can be a brush
            id or a filename, in the last case the brush will be loaded, used
            and finally removed from memory.
  sectors : [TBL] It's a table describing the three brush's areas as following:
    left : [TBL] Left sector's description:
      start : [NUM] Sector's vertical position start
      size  : [NUM] Sector's height
    middle : [TBL] Middle sector's description:
      start : [NUM] Sector's vertical position start
      size  : [NUM] Sector's height
    right : [NUM] Right sector's description:
      start : [NUM] Sector's vertical position start
      size  : [NUM] Sector's height
  alpha   : [NUM] With this parameter you can override the brush's alpha channel,
            if defined, with a custom transparency value. Set this parameter
            to #NONE to leave untouched the brush's alpha channel.
  vadapt  : [BLN] If set to TRUE, the midlle part will be stretched instead of
            being used as a fill pattern.

OUTPUT
  result : [BLN] Returns TRUE if the operation has been completed without errors.

```

---

### G2D.Area:SkinGradient(col1, col2, alpha, angle)
```plain
result = G2D.Area:SkinGradient(col1, col2, alpha, angle)

This method is able to skin an area object using a linear color gradient
defined by 'col1' and 'col2' colors. You can control the transparency using
'alpha' and you can also rotate the gradient using the parameter 'angle'.

INPUT
  col1  : [NUM] Fill color 1 in RRGGBB format, any alpha channel informations
         will be ignored.
  col2  : [NUM] Fill color 2 in RRGGBB format, any alpha channel informations
         will be ignored.
  alpha : [NUM] Use this parameter to control the gradient transparency, set
          it to #NONE to have the gradient fully opaque.
  angle : [NUM] Rotation angle of the gradient.

OUTPUT
  result : [BLN] Returns TRUE if the operation reported no errors.

```

---

### G2D.Area:Box(color, offset)
```plain
G2D.Area:Box(color, offset)

Draw a border around the area, offset will be used to make an inner box
or an outer box depending if the offset value is negative or positive.

INPUT
  color  : [NUM] Border color
  offset : [NUM] Offset value to make the box smaller or bigger than the actual area
           size.

```

---

### G2D.Area:SkinPattern(brush, offset, alpha, size)
```plain
result = G2D.Area:FkinPattern(Brush, Offset, Alpha, Size)

Skin the area object with the 'Brush' pattern. 
The brush can be shifted using the 'Offset' table, you can control 
transparency with 'Alpha' argument.

INPUT
  Brush  : [ID|STR] The brush to use to skin the area. It can be a brush id
           or a filename, in the last case the brush will be loaded, used and
           and removed from memory just after the rendering.
  Offset : [TBL] This table is used to shift horizontally, vertically or in both
            directions the brush. It must have the following fields:
    x : [NUM] Horizontal shift in pixels
    y : [NUM] Vertical shift in pixels
  Alpha  : [NUM] With this parameter you can override the brush's alpha channel 
           (if defined) with a custom transparency value. Set this parameter to
           #NONE to leave untouched the brush's alpha channel.
  Size   : [TBL] Optional brush tile size, it must have the fields:
    w : [NUM] Tile width in pixels
    h : [NUM] Tile height in pixels

OUTPUT
  result : [BLN] True if all gone fine.

```

---

### G2D.Area:FillPattern(BrushID)
```plain
G2D.Area:FillPattern(brushID)

Fill the area object using the given brush as a pattern.

INPUT
  BrushID : [ID] A valid Hollywood brush id

```

---

### G2D.Area:Move(x, y, absolute)
```plain
G2D.Area:Move(x, y, absolute)

Move the area object to another position or by a given amount, depending on the
'absolute' switch state.

INPUT
  x : [NUM] Optional horizontal position or relative horizontal movement.
  y : [NUM] Optional vertical position or relative vertical movement.
  absolute : [BLN] Optional True to use the horizontal and vertical values as a new 
             absolute position, or False to use these values as relative position.
             Default = False.

NOTE
  If absolute = True than x and y default values are current area values
  If absolute = False that x and y default values are 0

```

---

### G2D.Area:SkinQuick(SkinBrush, Mode)
```plain
G2D.Area:SkinQuick(SkinBrush, Mode)

Method used to fill the area object with a skin without the need to specify
too much parameters.

INPUT
  SkinBrush : [ID] A valid Hollywood brush id to use as a fill base.
  Mode      : [NUM] Ones skinning mode from the following:
    GFX.SkinMode_Pattern : The brush will be used as a tile
    GFX.SkinMode_Image   : The brush will be stretched to cover the area
    GFX.SkinMode_Skin9S  : The brush will be splitted into nine sectors (3x3),
                           each one will be used to skin the area this way:
                           +---+---+---+   A: Top-left edge
                           | A | B | C |   B: Top-middle (horizontal pattern)
                           +---+---+---+   C: Top-right edge
                           | D | E | F |   D: Left-middle (vertical pattern)
                           +---+---+---+   E: middle (area pattern)
                           | G | H | I |   F: Right-middle (vertical pattern)
                           +---+---+---+   and so on...
NOTE
  To have perfect pixel skins with the 'GFX.SkinMode_Skin9S' mode your brush size
  should be a multiple of 3

```

---

### G2D.Area:SkinFitMin(brush, offset, alpha, align, border)
```plain
result = G2D.Area:SkinFitMin(brush, offset, alpha, align, border)

Skin the area object with a scaled brush keeping its aspect ratio.
The brush can be shifted using the table <offset> and you can control
transparency with 'alpha' argument to override the existing one if defined.
Using this function the image will be maximized to cover the entire area but
without letting the image go out of the area boundaries so you could have
visible borders.

INPUT
  brush  : [ID|STR] The brush to use to skin the area. It can be a brush id
           or a filename, in the last case the brush will be loaded, used
           and removed from memory.
  offset : [TBL] This table is used to shift horizontally, vertically or in
           both directions the brush. It must have the following fields:
    x : [NUM] Horizontal shift in pixels
    y : [NUM] Vertical shift in pixels
  alpha  : [NUM] With this parameter you can override the brush's alpha channel
           (if defined) with a custom one. Set this parameter to #NONE to leave
           untouched the brush's alpha channel.
  align  : [NUM] Image alignment within the area object, it can be #CENTER,
           #LEFT, #RIGHT, #TOP, #BOTTOM, default value is #CENTER.
  border : [NUM] Border color.

OUTPUT
  result : [BLN] Returns True if no error was raised-

```

---

### G2D.Area:SkinVPattern(brush, offset, alpha)
```plain
result = G2D.Area:SkinVPattern(brush, offset, alpha)

This method is used to skin the area object using 'brush', the brush will be
first stretched to cover the area width and then the area will be filled with the
stretched brush vertically.
You can control transparency with 'alpha' to override the brush alpha channel,
if defined.

INPUT
  brush  : [ID|STR] The brush to use to skin the area. It can be a brush
           id or a filename, in the last case the brush will be loaded, used
           and finally removed from memory.
  offset : [TBL] This table is used to shift the brush horizontally, vertically
           or in both directions. It must have the following fields:
    x : [NUM] Horizontal shift in pixels
    y : [NUM] Vertical shift in pixels
  alpha  : [NUM] With this parameter you can override the brush's alpha channel,
           if defined, with a custom transparency value. Set this parameter
           to #NONE to leave untouched the brush's alpha channel.

OUTPUT
  result : [BLN] Returns TRUE if the operation has been completed without errors.

```

---

### G2D.Area:FillColor(color)
```plain
G2D.Area:FillColor(Color)

Fill the area object with the specified 'Color'.

INPUT
  Color : [NUM] The fill color

```

---

### G2D.Area:SkinFitMax(brush, offset, alpha, align)
```plain
result = G2D.Area:SkinFitMax(brush, offset, alpha, align)

Skin the area object with a scaled brush keeping its aspect ratio. The brush
can be shifted using the 'offset' table and you can control transparency 
with 'alpha' that allows yout to ovverride the existing one if defined.
Using this function the image will be maximized to cover the entire area, it
may be possible that the image cannot be completely visible because some part
go outside the visible area because of the maximization and the aspect ratio.

INPUT
  brush  : [ID|STR] The brush to use to skin the area. It can be a brush id
           or a filename, in the last case the brush will be loaded, used and
           removed from memory.
  offset : [TBL] This table is used to shift horizontally, vertically or in both
           directions the brush. It must have the following fields:
    x : [NUM] Horizontal shift in pixels
    y : [NUM] Vertical shift in pixels
  alpha  : [NUM] With this parameter you can override the brush's alpha channel
           (if defined) with a custom one. Set this parameter to #NONE to leave
           untouched the brush's alpha channel.
  align  : [NUM] Image alignment, can be #CENTER, #LEFT, #RIGHT, #TOP,
           or #BOTTOM, default value is #CENTER.

OUTPUT
  result : [BLN] Returns True if no error was raised-

```

---

### G2D.Area:Snapshot(BGPic)
```plain
brush = G2D.Area:snapshot(BGPic)

This method returns a brush with the content 'seen' by the object area.
'BGPic' is the currently active background picture, if you don't specify it
BGPic 1 will be selected.

INPUT
  BGPic : [ID] Optional BGPic, default = 1
  
OUTPUT
  brush : [ID] Brush id of the captured area

```

---

### G2D.Area:SkinPattern9S(brush, sectors, alpha, vadapt)
```plain
result = G2D.Area:SkinPattern9S(brush, sectors, alpha, vadapt)

This method is used to skin the area object using the specified brush'brush'.
This method needs a brush subdivided in 9 sectors that will be described
using the 'sectors' table.

INPUT
  brush   : [ID|STR] The brush to use to skin the area. It can be a brush
            id or a filename, in the last case the brush will be loaded, used
            and finally removed from memory.
  sectors : [TBL] It's a table describing the three brush's areas as following:
    top : [TBL] Top sector's description:
      start : [NUM] Sector's vertical position start
      size  : [NUM] Sector's height
    vmiddle : [TBL] Vertical/Middle sector's description:
      start : [NUM] Sector's vertical position start
      size  : [NUM] Sector's height
    bottom : [NUM] Bottom sector's description:
      start : [NUM] Sector's vertical position start
      size  : [NUM] Sector's height
    left : [TBL] Left sector's description:
      start : [NUM] Sector's vertical position start
      size  : [NUM] Sector's height
    hmiddle : [TBL] Horizontal/Middle sector's description:
      start : [NUM] Sector's vertical position start
      size  : [NUM] Sector's height
    right : [NUM] Right sector's description:
      start : [NUM] Sector's vertical position start
      size  : [NUM] Sector's heighth      
  alpha   : [NUM] With this parameter you can override the brush's alpha channel,
            if defined, with a custom transparency value. Set this parameter
            to #NONE to leave untouched the brush's alpha channel.
  vadapt  : [BLN] If set to TRUE, the midlle part will be stretched instead of
            being used as a fill pattern.

OUTPUT
  result : [BLN] Returns TRUE if the operation has been completed without errors.

```

---

### G2D.Area:SkinStretch(brush, offset, alpha, stretch_fix)
```plain
result = G2D.Area:SkinStretch(Brush, Offset, Alpha, Stretch_Fix)

Skins the area object stretching the image 'brush' (a filename or a brush id).
The 'brush' can be shifted using the table 'offset', you can also adjust
the transparency with the 'alpha' parameter.

INPUT
  brush  : [ID|STR] A valid Hollywood brush id or an image filename. In the last case
           the brush will be loaded, used and removed from memory just after
           the rendering.
  offset : [TBL] This table is used to shift horizontally, vertically or in both 
           directions the brush image. It must have the following fields:
    x : [NUM] Horizontal shift
    y : [NUM] Vertical shift 
  alpha  : [NUM] With this parameter you can override the brush's alpha channel (if
           defined) with a custom one. Set this parameter with #NONE to leave
           untouched the brush's alpha channel. Defaults to #NONE.
  stretch_fix : [NUM] I've introduced this fix because when I stretch a brush using
                smoothness I get an image that is bigger then the same image stretched 
                without smooth, the difference seems to be a single pixel.
                This argument can handle 1, 2 or 3 as value to fix the width, the height
                or both.
                
OUTPUT
  result : [BLN] Returns 'True' if there was no errors.

```

---

### G2D.Area:SkinVPattern3S(brush, sectors, alpha, vadapt)
```plain
result = G2D.Area:SkinVPattern3S(brush, sectors, alpha, vadapt)

This method is used to skin the area object using 'brush'. 
The brush should be a vertical strip subdivided into three sectors defined
using the 'sectors' table.
The top side and bottom side are fixed sized while the middle part will be used
to fill the area height repeating the middle part, or, if 'vadapt' is set to
TRUE, the middle part will be stretched.
You can control transparency with 'alpha' to override the brush alpha channel,
if defined.

INPUT
  brush   : [ID|STR] The brush to use to skin the area. It can be a brush
            id or a filename, in the last case the brush will be loaded, used
            and finally removed from memory.
  sectors : [TBL] It's a table describing the three brush's areas as following:
    top : [TBL] Top sector's description:
      start : [NUM] Sector's vertical position start
      size  : [NUM] Sector's height
    middle : [TBL] Middle sector's description:
      start : [NUM] Sector's vertical position start
      size  : [NUM] Sector's height
    bottom : [NUM] Bottom sector's description:
      start : [NUM] Sector's vertical position start
      size  : [NUM] Sector's height
  alpha   : [NUM] With this parameter you can override the brush's alpha channel,
            if defined, with a custom transparency value. Set this parameter
            to #NONE to leave untouched the brush's alpha channel.
  vadapt  : [BLN] If set to TRUE, the midlle part will be stretched instead of
            being used as a fill pattern.

OUTPUT
  result : [BLN] Returns TRUE if the operation has been completed without errors.

```

---

### G2D.Area:SkinHPattern(brush, offset, alpha)
```plain
result = G2D.Area:SkinHPattern(brush, offset, alpha)

This method is used to skin the area object using 'brush'. The brush will be
first stretched to cover the area height and then the area will be filled
with the stretched brush.
You can control transparency with 'alpha' overriding the brush alpha channel,
if defined.

INPUT
  brush  : [ID|STR] The brush to use to skin the area. It can be a brush
           id or a filename, in the last case the brush will be loaded, used
           and finally removed from memory.
  offset : [TBL] This table is used to shift the brush horizontally, vertically
           or in both directions. It must have the following fields:
    x : [NUM] Horizontal shift in pixels
    y : [NUM] Vertical shift in pixels
  alpha  : [NUM] With this parameter you can override the brush's alpha channel,
           if defined, with a custom transparency value. Set this parameter
           to #NONE to leave untouched the brush's alpha channel.

OUTPUT
  result : [BLN] Returns TRUE if the operation has been completed without errors.

```

---

### G2D.Area:SkinShades(colList, angle)
```plain
result = G2D.Area:SkinShades(colList, angle)

This method is able to skin the area object using a parametric gradient
you have to provide with the table 'colList' where the color shades are
defined.
You can also rotate the color gradient but remember that only multiple of
90 degrees will be correctly rendered at this time.

INPUT
  colList : [TBL] Color table used to define the shades with thisg format:
            collist = { { step_1 }, { step_2 }, { step_2 }, ... }
            Where:
              step_n = { Color = RRGGBBC, Weight = n, Alpha = n }
            Color  : [NUM] Is a color in RRGGBB notation.
            Weight : [NUM] The last item must have Weight = 0, and the sum
                     of all entries must be 100. This parameter is used to
                     define the color bands width, infact the Weight of the
                     first item, for example, defines the width of the shade
                     composed by the first and the second color entries.
            Alpha  : [NUM] Is a value between 0 and 255 and will be faded
                     along the colors during the gradient creation.
  angle   : [NUM] Rotation angle of the gradient. Actually only multiple of 90
                 degrees will be rendered correctly.

OUTPUT
  result : [BLN] Returns TRUE if the operation has been completed without errors.

```

---

### G2D.Area:SkinBevel(colors, aspect)
```plain
result = G2D.Area:SkinBevel(colors, aspect)

Use this method to skin the specified 'area'. 
'colors' is a table used to define the colors that must be used to render
the bevel box.

INPUT
  colors : [TBL] A table with the color to use, must have the following fields:
    light  : [NUM] Light Edges (top and left)
    dark   : [NUM] Dark Edges (bottom and right)
    middle : [NUM] Internal color (set to nil to not fill this space)
  aspect : [TBL] It is a table with further parameters with the following fields:
    fx : [NUM] Can be one of the following effect : 
           GFX.BevelFx_Raised     Raised look
           GFX.BevelFx_Recessed   Recessed look (inverted light & dark colors)
           GFX.BevelFx_Flat       Flat look (no 3d borders)
    height : [NUM] Border's height in pixels
    type : [NUM] Bevel box type :
             GFX.BevelType_Standard
             GFX.BevelType_Sunken

OUTPUT
  result : [BLN] Returns True if no error was raised

```

---

### G2D.Area:New(x, y, w, h)
```plain
areaObj = G2D.Area:New(x, y, w, h)

Creates and returns a new Area object.

INPUT
  x : [NUM] Optional horizontal coordinate, default = 0
  y : [NUM] Optional vertical coordinate, default = 0
  w : [NUM] Optional width in pixels, default = 50
  h : [NUM] Optional height in pixels, default = 50
  
OUTPUT
  areaObj : [NUM] New, initialized Area object

```

---

### G2D.Area:Scale(WFactor, HFactor)
```plain
G2D.Area:Scale(wFactor, hFactor)

Scales the area using the given horizontal and vertical factors.

INPUT
  wFactor : [NUM] Horizontal scaling factor, default 1
  hFactor : [NUM] Vertical scaling factor, default 1

```

---

### G2D.Area:SkinColor(color, alpha)
```plain
result = G2D.Area:SkinColor(color, alpha)

Use this function to skin the area object, color can be in RRGGBB format or in
AARRGGBB format. 'alpha' is the transparency level, but remember that if you
are using a color in AARRGGBB format the alpha channel will be replaced by the
'alpha' value.

INPUT
  color : [NUM] The color you want to use to fill the area with.
  alpha : [NUM] With this parameter you can override the color's alpha channel
          (if specified) with a custom one. Set this parameter with #NONE to leave
          untouched the color's alpha channel.

OUTPUT
  result : [BLN] Returns True if no error was raised

```

---


---


---

## Class G2D.Poly
```plain
G2D.Poly = {}
G2D.Poly.Vertices = {}
G2D.Poly.Normals  = {}
G2D.Poly.VCount   = 0
G2D.Poly.Color    = { 1.0, 1.0, 1.0, 0.5 } ; RGBA
G2D.Poly.Fillmode = #FILLCOLOR
G2D.Poly.x        = 0
G2D.Poly.y        = 0
G2D.Poly.ScaleW   = 1
G2D.Poly.ScaleH   = 1
G2D.Poly.AnchorX  = 0
G2D.Poly.AnchorY  = 0
G2D.Poly.Angle    = 0

```

---

## G2D.Poly methods

---

### G2D.Poly:SetAngle(angle)
```plain
G2D.Poly:SetAngle(angle)

Change the rotation angle of the polygon updating all the vertices positions.

INPUT
  angle : [NUM] The rotation angle in degrees

```

---

### G2D.Poly:CollideDot(dot)
```plain
Unfinished method

```

---

### G2D.Poly:SetAnchor(anchorX, anchorY)
```plain
G2D.Poly:SetAnchor(anchorX, anchorY)

Changes the current anchor point.

INPUT
  anchorX : [NUM] Optional horizontal anchor point
  anchorY : [NUM] Optional vertical anchor point

```

---

### G2D.Poly:Draw()
```plain
G2D.Poly:Draw()

Renders the polygon.

```

---

### G2D.Poly:Translate(x, y)
```plain
G2D.Poly:Translate(x, y)

Translate the polygon object.

INPUT
  x : [NUM] Horizontal translate value
  y : [NUM] Vertical translate value

```

---

### G2D.Poly:New(params)
```plain
polyObj = G2D.Poly:New(params)

Returns a new polygon object.

INPUT
  params : [TBL] A table filled with one or more of the following parameters:
    vertices : [TBL] A table of vertices, in { x, y } format
    color    : [NUM] A table with 4 items in RGBA sequence, default { 1.0, 1.0, 1.0, 0.5 }
    fillMode : [CNS] Rendering fillmode, default #FILLCOLOR
    x        : [NUM] Horizontal coordinate, default 0
    y        : [NUM] Vertical coordinate, default 0
    scaleW   : [NUM] Horizontal scaling factor, default 1
    scaleH   : [NUM] Vertical scaling factor, default 1
    anchorX  : [NUM] Horizontal anchor point, default 0
    anchorY  : [NUM] Vertical anchor point, default 0
    angle    : [NUM]Rotation angle, default 0
    
OUTPUT
  polyObject : [TBL] An initialized polygon object
  
NOTES
  You need to provide a valide sequence of vertices.

```

---

### G2D.Poly:Project(Axis)
```plain
result = G2D.Poly:Project(Axis)

Project the source point on the given 'Axis', a point object.
Returns the 'min' and 'max' values projected on the 'Axis'.

INPUT
  Axis : A point object representing the projection axis.

OUTPUT
  result : [TBL] A table with the following fields:
    min : [NUM] The minimum value on the axis
    max : [NUM] The maximum value on the axis

```

---

### G2D.Poly:Collide(Poly2)
```plain
result = G2D.Poly:Collide(Poly2)

Check if the source polygon object collides with the 'Poly2' polygon object.

INPUT
  Poly2 : [TBL] Polygon object to check for collisions
  
OUTPUT
  result : [BLN] True if the source polygon and 'Poly2' polygon are colliding
  
NOTES
  Note that only convex polygon can be checked using this technic.

```

---

### G2D.Poly:SetScale(scaleWidth, scaleHeight)
```plain
G2D.Poly:SetScale(scaleWidth, scaleHeight)

Changes the current scaling factors.

INPUT
  scaleWidth  : [NUM] New horizontal scale value
  scaleHeight : [NUM] Optional new vertical scale value
NOTES
  If you don't pass a 'scaleHeight' value this function will use the
  'scaleWidth' to hold the aspect ratio.

```

---


---


---

## Class G2D.Point
```plain
G2D.Point = {}
G2D.Point.x = 0
G2D.Point.y = 0

```

---

## G2D.Point methods

---

### G2D.Point:Normal2D(Point2D, s)
```plain
normalized = G2D.Point:Normal2D(pointObj)

Returns a new object with normalized coordinates.

INPUT
  point2D : [TBL] Reference point object
  s       : [BLN] True : Invert horizontal, False : Invert vertical
  
OUTPUT
  normalized : [TBL] Normalized point object

```

---

### G2D.Point:Distance(point2D)
```plain
value = G2D.Point:Distance(point)

Returns the distance in pixels between the object and the given
'point' object.

INPUT
  point : [TBL] The point object used for the distance calculation
  
OUTPUT
  value : [NUM] The distance between the two points in pixels

```

---

### G2D.Point:New(x, y)
```plain
pointObj = G2D.Point:New(x, y)

Creates an object to represent a 2d point.
'x' and 'y' are the optional initial coordinates, default values are (0, 0)

INPUT
  x : [NUM] Optional horizontal coordinate, default = 0
  y : [NUM] Optional vertical coordinate, default = 0

OUTPUT
  pointObj : [TBL] New point object

```

---

### G2D.Point:Scale(point, scaleW, scaleH)
```plain
G2D.Point:Scale(point, scaleW, scaleH)

Scales the distance between the source object and the given point.

INPUT
  point : [TBL] Point object used as a reference for the distance calculation
  scaleW : [NUM] Horizontal scaling factor
  scaleH : [NUM] Vertical scaling factor

```

---

### G2D.Point:Normalize()
```plain
G2D.Point:Normalize()

Normalize the point object's coordinates

```

---

### G2D.Point:MidPoint(point2D, NewObject)
```plain
result = G2D.Point:MidPoint(pointObj, NewObject)

Returns a table with the mid point coordinates or a new initialized object
representing the middle point between the source point and the given 'point2D'.

INPUT
  point2D   : [TBL] Reference point object
  NewObject : [BLN] True : returns a new initialized point object
              False : returns a table with the 'x' and 'y' members. 
              Default = False.
OUTPUT
  result : [TBL] Depending on 'NewObject' you can have a table with 'x' and 'y'
           members or a new initialized point object.

```

---

### G2D.Point:Rotate(point, angle)
```plain
G2D.Point:Rotate(point, angle)

Rotates a point around the given anchor point

INPUT
  point : [TBL] The rotation anchor pointObj
  angle : [NUM] Rotation angle in degrees

```

---

### G2D.Point:DotProduct(point2D)
```plain
value = G2D.Point:DotProduct(point2D)

Returns the sum of the two point's coordinates products

INPUT
  point2D : [TBL] Reference point object
  
OUTPUT
  value : [NUM] Calculated product

```

---


---


---

# MISC FUNCTIONS

---

## G2D.TEST_Poly()
```plain
G2D.TEST_Poly()

Show how to use the Poly object and test some methods.

```

---

## G2D.BGPic.CreateSkinned(width, height, skin_struct)
```plain
BGId = G2DBGPic.CreateSkinned(width, height, skin)

Returns a BGPic of the desired sizes ('width' and 'height') skinned with the
the skin layers defined by 'skin'.

INPUT
  width  : [NUM] BGPic width
  height : [NUM] BGPic height
  skin   : [TBL] Multi Skin definition (see skinning functions)
  
OUTPUT
  BGId : [ID] BGPic id

```

---


---


---

Generated with sourcedoc2md version 1.0, 11-Jul-2023 17:15:44
