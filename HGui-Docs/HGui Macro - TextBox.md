# HGUI MACRO : TEXTBOX

A **TextBox** is a window with a scrollable text content and an 'ok' and 'cancel' buttons. You can use it as you wish, it supports all the window's flags, actions and parameters so you can tune it freely to your taste.

Here is the documentation extracted from the source code:

```plaintext
-----------------------------------------------------------
winObj = HGui.Window:textBoxNew(params)

Creates a new text box window to allow user to read a text and optionally make
choices.
-----------------------------------------------------------
INPUT
  params                        A table that defines the window, see :New() method for details.
                                Also these additional tags are supported:
    caption                     Optional string to preload the text box with some text caption
                                can also be a file, you can specify the text file name using this
                                format:   ::file::<filename>
    caption_tags                it's an optional table with pairs (tag, replacer) you can use
                                to replace custom tags with the given text in the specified caption,
                                it works also with text files.
                                Example : { { "$name", "Jhon" }, { "$surname", "Doe" } }
    ok                          Text to put into the 'ok' button
    cancel                      Text to put into the 'cancel' button
    callbackOk                  Callback function called when the 'ok' button is pressed
    callbackCancel              Callback function called when the 'cancel' button is pressed
    callbackClose               Callback function called when the window is closed
    labellook                   Optional field you can use to override the label(s) look.

OUTPUT
  winObj                        The created window object
```

##### NOTES

The callback functions will receive a table with the button object that has   been pressed, the button object will have the 'result' additional field:
```plaintext
result = 
    { ok       = True if the OK button has been pressed
      cancel   = True if the CANCEL button has been pressed
      window   = textBox window's structure }
```
If the window is closed the 'result' field is missing, however you will get the window's structure
as the second parameter so you can close the window by yourself.
  
If callback functions are not specified the window will be closed automatically otherwise you have
to include the :free() method in your callback function.

OnClose event is not supported because used internally.
  
##### ADDITIONAL METHODS
```plaintext
:AppendLine(text)               Used to append 'text' to the TextBox contents and to automatically
                                scroll down the contents.
```

##### EXAMPLE
```plaintext
Local winObj = HGui.Window:textBoxNew(
   { title = "TEXTBOX TEST",
     name = "tb",
     caption =  { [[This is a text you can freely format as you wish since it is enclosed in
     double square brackets
     You can easily setup new lines in this way]], "This is another line of text, but you can also pass a single string instead of a table of text lines." } ,
     })

Repeat
  WaitEvent()
Forever 
```

##### INTERNALS
```plaintext
  win.boxLabel     : The label gadget used to display the text
  win.pwGrpButtons : Box to group 'ok' and 'cancel' buttons
  win.pwGrpTop     : Box to group label gadget and the scrollbar
  win.scrollBar    : The text scrollbar
  win._isTextBox   : Marker to recognize the TextBox window
  win._sourceText  : The non-processed/wrapped text
```