# HGUI : SPLASH SCREEN MACROS



## INTRODUCTION
An **Splash Screen** is an image with an optional text with informations, that is showed when your application is loading, so that the user can see what's appening during the loading time instead of thinking the app is crashed or freezed.
**HGui** provides a set of macro methods to easily manage a Splash Screen for your application.



## SPLASH SCREEN FUNCTIONS & METHODS


#### HGui.ShowSplashScreen(imageFile, size, setDisplaySize)
Open a window on display 1, to show the loading progress of the application.
You have to use it before any new HGui window.

```plaintext
INPUT
  imageFile                     Image file to show in the splash screen
  size                          Can be a string or a table
                                  STRING : set to 'image' to use the original
                                           image's size
                                  TABLE : a table with the 'w' and 'h' fields used
                                          to specify the splash image width & the height
  setDisplaySize                Overwrite the splash screen size with the one
                                you have specified in the 'size' argument.

OUTPUT

NOTES
  This function is used to show a nice splash screen during the startup of you
  applications, the image will fade in and you can also print a text and show
  a progress bar while loading your app using these fuctions:
    HGui.MsgSplashScreen(txt)
    HGui.AnimSplashScreen(txt)
  You can remove the splash screen with a fade out effect with:
    HGui.HideSplashScreen(color)
    
  The animation is a moving bar on the bottom of the image with optionally
  an optional text message.

INTERNALS
  All informations about the splash screen are stored in the table
  'HGui.Splash', it has the following fields:
    .w          Splash screen width
    .h          Splash screen height
    .image      Splash screen image brush (removed as soon as it is displayed)
  The following fields are hardcoded:
    .animWidth  Animation width
    .animStep   Animation step
    .animColor  Animation color
    .animX      Animation negative width (for left entering fx)
```

#### HGui.AnimSplashScreen(txt)
Animate the splash screen updating the text if 'txt' has been provided.
The standard animation is a bar moving under the text, at the bottom
of the splash screen.

```plaintext
INPUT
  txt           Text to update (optional)
  
OUTPUT

NOTE
  This function is pretty rude, not much customization is available
  even if it's pretty simple to change the code to your taste.
```

#### HGui.HideSplashScreen(color)
Hide the splash screen using a crossfade effect and the given 'color',
the display is not closed because will be reused by HGui when the first
window will be opened.

```plaintext
INPUT
  color             Color to use for the crossfade effect
  
OUTPUT

```