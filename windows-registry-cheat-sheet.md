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

### How to add "Open here with ..." entries to the context menu

#### Example of open here with Cursor, VSCode Insiders etc.

<img width="315" height="551" alt="image" src="https://github.com/user-attachments/assets/5a839df7-4411-4fea-b16c-b4351e07c80e" />

Go to 
```cmd
Computer\HKEY_CLASSES_ROOT\Directory\background\shell\
```

1. Create a new key in `shell`\
<img width="685" height="943" alt="image" src="https://github.com/user-attachments/assets/c95eff29-df01-433b-ba91-99610924a16f" />

2. Add new string to the key, call it `Icon`\
<img width="1028" height="889" alt="image" src="https://github.com/user-attachments/assets/9fd4ca26-cdb5-4321-8b4a-8727322e7fdb" />

3. Find the path executable for the software you want to add, and wrap it in `""`-quotes\
<img width="739" height="969" alt="image" src="https://github.com/user-attachments/assets/336fa6a2-6fd0-4b8b-9b98-f5c371a8e8f0" />


4. Add a subkey to the main key and call it `command`\
<img width="960" height="923" alt="image" src="https://github.com/user-attachments/assets/e69d0400-c632-42c5-88e9-cf57046e4fa1" />

5. Add the same path to the executable and append `"%V"` to it\
<img width="619" height="730" alt="image" src="https://github.com/user-attachments/assets/4424039f-490d-4449-ba1d-24c484ecb641" />

6. Your new custom key should show up in the context menu without need for reboot:\
<img width="314" height="580" alt="image" src="https://github.com/user-attachments/assets/b1c569b8-ee7c-4db2-8bab-53652bc064f4" />


