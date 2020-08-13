## Configuring Openbox on Lubuntu

Openbox is a window manager that comes installed with Lubuntu/LXDE.

To configure it, open `~/.config/openbox/lubuntu-rc.xml` in a text editor.

Change the relevant section to this:

```xml

<!-- Keybindings for window tiling -->
<keybind key="W-Left">    
  <action name="UnmaximizeFull"/>
  <action name="MoveResizeTo">
    <x>0</x>
    <y>0</y>
    <height>100%</height>
    <width>50%</width>
  </action>
</keybind>
<keybind key="W-Right">  
  <action name="UnmaximizeFull"/>
  <action name="MoveResizeTo">
    <x>-0</x>
    <y>0</y>
    <height>100%</height>
    <width>50%</width>
  </action>
</keybind>
<keybind key="W-Up">        
  <action name="ToggleMaximizeFull"/>
</keybind>
<keybind key="W-Down">     
  <action name="UnmaximizeFull"/>
  <action name="MoveResizeTo">
    <x>0</x>
    <y>-0</y>
    <width>100%</width>
    <height>50%</height>
  </action>
</keybind>


<keybind key="W-j">        
  <action name="UnmaximizeFull"/>
  <action name="MoveResizeTo">
    <x>0</x>
    <y>0</y>
    <height>50%</height>
    <width>50%</width>
  </action>
</keybind>

<keybind key="W-k">        
  <action name="UnmaximizeFull"/>
  <action name="MoveResizeTo">
    <x>-0</x>
    <y>0</y>
    <height>50%</height>
    <width>50%</width>
  </action>
</keybind>
<keybind key="W-n">        
  <action name="UnmaximizeFull"/>
  <action name="MoveResizeTo">
    <x>0</x>
    <y>-0</y>
    <height>50%</height>
    <width>50%</width>
  </action>
</keybind>
<keybind key="W-m">        
  <action name="UnmaximizeFull"/>
  <action name="MoveResizeTo">
    <x>-0</x>
    <y>-0</y>
    <height>50%</height>
    <width>50%</width>
  </action>
</keybind>


```



And here's the default section on moving to desktops


```xml

<!-- Keybindings for desktop switching -->
<keybind key="C-A-Left">
  <action name="GoToDesktop">
    <to>left</to>
    <wrap>no</wrap>
  </action>
</keybind>
<keybind key="C-A-Right">
  <action name="GoToDesktop">
    <to>right</to>
    <wrap>no</wrap>
  </action>
</keybind>
<keybind key="C-A-Up">
  <action name="GoToDesktop">
    <to>up</to>
    <wrap>no</wrap>
  </action>
</keybind>
<keybind key="C-A-Down">
  <action name="GoToDesktop">
    <to>down</to>
    <wrap>no</wrap>
  </action>
</keybind>
<keybind key="S-A-Left">
  <action name="SendToDesktop">
    <to>left</to>
    <wrap>no</wrap>
  </action>
</keybind>
<keybind key="S-A-Right">
  <action name="SendToDesktop">
    <to>right</to>
    <wrap>no</wrap>
  </action>
</keybind>
<keybind key="S-A-Up">
  <action name="SendToDesktop">
    <to>up</to>
    <wrap>no</wrap>
  </action>
</keybind>
<keybind key="S-A-Down">
  <action name="SendToDesktop">
    <to>down</to>
    <wrap>no</wrap>
  </action>
</keybind>
```
