# Windows Registry Cheat Sheet

## Open Windows Registry 

- `Windows` `Key` `+` `R`
- `regedit`

## HKEY_CURRENT_USER

Registry key to modify if you want to enable manual BSOD functionality:
HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\kbdhid\Parameters

### Legal Banner at Login
Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon

### Hightlight and Hilight Text Regedit
Highlight 
HighlightText

## Desktop Lasso Selection Box Color
HKEY_CURRENT_USER\Control Panel\Colors
HotTrackingColor

## Enable numpad at login
HKEY_USERS\.DEFAULT\Control Panel\Keyboard
InitialKeyboardIndicators 2

## Increase the Node / Electron heap limit on Windows

| Command                                                                                      | Lifespan            | Applies to           |
|----------------------------------------------------------------------------------------------|---------------------|----------------------|
| `setx NODE_OPTIONS "--max_old_space_size=8192"`                                              | **Persistent** (stored in registry) | All **new** sessions after you run it |
| `set NODE_OPTIONS=--max_old_space_size=8192` (in **cmd.exe**)                                | Current shell only  | Lasts until you close that cmd window |
| `$env:NODE_OPTIONS="--max_old_space_size=8192"` (in **PowerShell**)                          | Current shell only  | Lasts until you close that PowerShell tab |

---

### Remove the permanent variable later

```powershell
setx NODE_OPTIONS ""
```
blanks it out

or
```powershell
reg delete "HKCU\Environment" /v NODE_OPTIONS /f
```

### Control Panel 

#### Colors 

These settings define the color settings for classic Windows UI elements. Each key controls the color of a specific part of the Windows interface.

| Key                         | Description |
|----------------------------|-------------|
| **ActiveBorder**           | Border color of the active window. |
| **ActiveTitle**            | Background color of the active window title bar. |
| **AppWorkspace**           | Background color for MDI (Multiple Document Interface) application workspace. |
| **Background**             | Desktop background color. |
| **ButtonDkShadow**         | Dark shadow used for 3D effects on buttons. |
| **ButtonFace**             | Face color of buttons (default light gray). |
| **ButtonHilight**          | Highlight color for 3D buttons (top left edge). |
| **ButtonLight**            | Light color for 3D buttons (intermediate shade). |
| **ButtonShadow**           | Shadow color for 3D buttons (bottom right edge). |
| **ButtonText**             | Text color on buttons. |
| **GradientActiveTitle**    | Gradient end color for active title bar. |
| **GradientInactiveTitle**  | Gradient end color for inactive title bar. |
| **GrayText**               | Color for disabled or grayed out text. |
| **Hilight**                | Background color for selected items (e.g., list items). |
| **HilightText**            | Text color for highlighted items. |
| **HotTrackingColor**       | Color for active or "hot-tracked" items (e.g., hyperlinks). |
| **InactiveBorder**         | Border color of the inactive window. |
| **InactiveTitle**          | Background color of the inactive window title bar. |
| **InactiveTitleText**      | Text color in the inactive window title bar. |
| **InfoText**               | Text color in tooltip balloons. |
| **InfoWindow**             | Background color of tooltip balloons. |
| **Menu**                   | Background color of menus. |
| **MenuBar**                | Color of the menu bar (newer versions of Windows). |
| **MenuHilight**            | Highlight color for selected menu items. |
| **MenuText**               | Text color of menu items. |
| **Scrollbar**              | Color of the scrollbar background. |
| **TitleText**              | Text color of the active window title bar. |
| **Window**                 | Background color of window content areas. |
| **WindowFrame**            | Border color of windows. |
| **WindowText**             | Text color inside windows. |
| **InitialKeyboardIndicators** | Enables numpad on startup |
"""

##### Change Selection Box Colors 
- Navigate to `HKEY_CURRENT_USER\Control Panel\Colors`
- Edit the `Hilight` key, it changes the color of the border of the lasso/selection box.
- Edit the `HotTrackingColor`, it changes the color of the background of the lasso/selection box.
