# Supported DuckyScript Commands (n3wbsWiFiDucky Enhanced Firmware)

This firmware supports a wide range of DuckyScript commands, including many from the official DuckyScript 1.0 and 3.0 specifications.

---

### `STRING` (DuckyScript v1.0)

Sends a string of text as keyboard input.

**Example:**
```
STRING Hello, world!
```

### `STRINGLN` (DuckyScript vcustom)

Sends a string of text followed by ENTER.

**Example:**
```
STRINGLN username
```

### `DELAY` (DuckyScript v1.0)

Waits a specified number of milliseconds before executing the next command.

**Example:**
```
DELAY 500
```

### `DEFAULTDELAY` (DuckyScript v1.0)

Sets the default delay between all keystrokes in milliseconds.

**Example:**
```
DEFAULTDELAY 100
```

### `KEYDELAY` (DuckyScript v3.0)

Sets delay between each individual key press.

**Example:**
```
KEYDELAY 10
```

### `REM` (DuckyScript v1.0)

Comment line ignored by the interpreter.

**Example:**
```
REM This is a comment
```

### `ENTER` (DuckyScript v1.0)

Sends the ENTER (Return) key.

**Example:**
```
ENTER
```

### `TAB` (DuckyScript v1.0)

Sends the TAB key.

**Example:**
```
TAB
```

### `ESCAPE` (DuckyScript v1.0)

Sends the Escape key.

**Example:**
```
ESCAPE
```

### `BACKSPACE` (DuckyScript v1.0)

Sends the Backspace key.

**Example:**
```
BACKSPACE
```

### `SPACE` (DuckyScript v1.0)

Sends the Space key.

**Example:**
```
SPACE
```

### `DELETE` (DuckyScript v1.0)

Sends the Delete key.

**Example:**
```
DELETE
```

### `CAPSLOCK` (DuckyScript v1.0)

Toggles the Caps Lock key.

**Example:**
```
CAPSLOCK
```

### `CTRL` (DuckyScript v1.0)

Sends the Control key. Can be combined with other keys.

**Example:**
```
CTRL ALT DELETE
```

### `ALT` (DuckyScript v1.0)

Sends the Alt key.

**Example:**
```
ALT F4
```

### `SHIFT` (DuckyScript v1.0)

Sends the Shift key.

**Example:**
```
SHIFT TAB
```

### `GUI` (DuckyScript v1.0)

Sends the Windows (GUI) key.

**Example:**
```
GUI r
```

### `F1–F24` (DuckyScript v1.0)

Sends function keys F1 through F24.

**Example:**
```
F11
```

### `KEYCODE` (DuckyScript v3.0)

Sends a raw HID keycode (numeric).

**Example:**
```
KEYCODE 0x04
```

### `RELEASE` (DuckyScript v1.0+)

Releases all held modifier keys or a specific one.

**Example:**
```
RELEASE SHIFT
```

### `LED` (DuckyScript vcustom)

Controls onboard status LED. Usage may vary by device.

**Example:**
```
LED ON
```

### `LOCALE` (DuckyScript v3.0)

Sets the keyboard layout (e.g., US, FR).

**Example:**
```
LOCALE US
```

### `RESTART` (DuckyScript vcustom)

Restarts the currently running payload script.

**Example:**
```
RESTART
```

### `REPEATKEY` (DuckyScript vcustom)

Repeats the last key sent once.

**Example:**
```
REPEATKEY
```

### `MOUSE` (DuckyScript v3.0)

Moves the mouse: MOUSE x y wheel pan.

**Example:**
```
MOUSE 10 -5 0 0
```

### `MOUSE CLICK` (DuckyScript v3.0)

Performs a mouse click (e.g., LEFT, RIGHT).

**Example:**
```
MOUSE CLICK LEFT
```

### `MOUSE PRESS` (DuckyScript v3.0)

Presses and holds a mouse button.

**Example:**
```
MOUSE PRESS RIGHT
```

### `MOUSE RELEASE` (DuckyScript v3.0)

Releases mouse buttons.

**Example:**
```
MOUSE RELEASE LEFT
```

### `MOUSE_DELAY` (DuckyScript vcustom)

Sets the default delay after mouse actions.

**Example:**
```
MOUSE_DELAY 100
```

### `DEFINE` (DuckyScript v3.0)

Defines a variable for later use in strings.

**Example:**
```
DEFINE name admin
```

### `${var}` (DuckyScript v3.0)

Substitutes a variable inside a STRING.

**Example:**
```
STRING Hello ${name}
```

### `VAR` (DuckyScript v3.0)

Types the value of a previously defined variable.

**Example:**
```
DEFINE greeting "Hello"
VAR greeting
```

### `IF` (DuckyScript v3.0)

Executes a block if a variable equals a value.

**Example:**
```
IF name == admin
```

### `ELSE` (DuckyScript v3.0)

Alternative branch when IF fails.

**Example:**
```
ELSE
```

### `ENDIF` (DuckyScript v3.0)

Closes an IF block.

**Example:**
```
ENDIF
```

### `REPEAT` (DuckyScript v3.0)

Repeats a block of commands n times.

**Example:**
```
REPEAT 3
```

### `ENDREPEAT` (DuckyScript v3.0)

Ends a REPEAT block.

**Example:**
```
ENDREPEAT
```

### `WHILE` (DuckyScript v3.0)

Repeats a block while a condition is true.

**Example:**
```
WHILE mode == active
```

### `ENDWHILE` (DuckyScript v3.0)

Ends a WHILE block.

**Example:**
```
ENDWHILE
```

### `HOLD` (DuckyScript v3.0+)

Presses and holds a modifier key until RELEASE.

**Example:**
```
HOLD SHIFT
```

### `LOAD_JPG` / `LOAD_PNG` / `LOAD_GIF`

Display an image on the TFT from the filesystem. The image stays visible until another image is drawn.

**Example:**
```
LOAD_JPG mylogo.jpg
LOAD_PNG /icons/status.png
LOAD_GIF anim.gif
```
