set $mod Mod4

# Fonts
font pango: UbuntuMono Nerd Font  14
# Use Mouse+$mod to drag floating windows to their wanted position

# Launch terminal
bindsym $mod+Return exec alacritty
# kill focused window
bindsym $mod+x kill

# Rofi menu launcher
set $rofi_theme "/home/fer/.i3/nord.rasi"
bindsym $mod+p exec rofi -show run -config $rofi_theme
bindsym $mod+Shift+p exec rofi -show window -config $rofi_theme

# change focus
bindsym $mod+h focus left
bindsym $mod+j focus down
bindsym $mod+k focus up
bindsym $mod+l focus right

# move focused window
bindsym $mod+Shift+j move left
bindsym $mod+Shift+k move down
bindsym $mod+Shift+l move up
bindsym $mod+Shift+ntilde move right
bindsym $mod+Shift+Left move left
bindsym $mod+Shift+Down move down
bindsym $mod+Shift+Up move up
bindsym $mod+Shift+Right move right

# Split horizontal and vertical orientation
bindsym $mod+c split h
bindsym $mod+v split v

# Fullscreen mode
bindsym $mod+f fullscreen toggle

# change container layout (stacked, tabbed, toggle split)
bindsym $mod+s layout stacking
bindsym $mod+w layout tabbed
bindsym $mod+e layout toggle split



# focus the parent container
bindsym $mod+a focus parent

# Workspace naming
set $workspace1 "1: Code  ❯" 
set $workspace2 "2: Term 󰆍 ❯"
set $workspace3 "3: Net  ❯"
set $workspace4 "4: Music 󰎆 ❯"
set $workspace5 "5: DB  ❯"
set $workspace6 "6 ❯"
set $workspace7 "7 ❯"
set $workspace8 "8 ❯"
set $workspace9 "9 ❯"





# switch to workspace

bindsym $mod+space     exec --no-startup-id i3-msg workspace back_and_forth


bindsym $mod+1 workspace $workspace1
bindsym $mod+2 workspace $workspace2
bindsym $mod+3 workspace $workspace3
bindsym $mod+4 workspace $workspace4
bindsym $mod+5 workspace $workspace5
bindsym $mod+6 workspace $workspace6
bindsym $mod+7 workspace $workspace7
bindsym $mod+8 workspace $workspace8
bindsym $mod+9 workspace $workspace9
bindsym $mod+0 workspace $workspace10

# move focused container to workspace
bindsym $mod+Shift+1 move container to workspace $workspace1
bindsym $mod+Shift+2 move container to workspace $workspace2
bindsym $mod+Shift+3 move container to workspace $workspace3
bindsym $mod+Shift+4 move container to workspace $workspace4
bindsym $mod+Shift+5 move container to workspace $workspace5
bindsym $mod+Shift+6 move container to workspace $workspace6
bindsym $mod+Shift+7 move container to workspace $workspace7
bindsym $mod+Shift+8 move container to workspace $workspace8
bindsym $mod+Shift+9 move container to workspace $workspace9
bindsym $mod+Shift+0 move container to workspace $workspace10


# reload the configuration file
bindsym $mod+Shift+c reload

# restart i3 inplace (preserves your layout/session, can be used to upgrade i3)
bindsym $mod+Shift+r restart

# exit i3 (logs you out of your X session)
bindsym $mod+Shift+e exec "i3-nagbar -t warning -m 'You pressed the exit shortcut. Do you really want to exit i3? This will end your X session.' -b 'Yes, exit i3' 'i3-msg exit'"

# Resize windows
mode "resize" {

        # Arrow bindings
        bindsym Left resize shrink width 10 px or 10 ppt
        bindsym Down resize grow height 10 px or 10 ppt
        bindsym Up resize shrink height 10 px or 10 ppt
        bindsym Right resize grow width 10 px or 10 ppt

        # back to normal: Enter or Escape
        bindsym Return mode "default"
        bindsym Escape mode "default"
}

# Resize binding
bindsym $mod+r mode "resize"

# Color config
set $bg-color 	         #2f343f
set $inactive-bg-color   #2f343f
set $text-color          #c4c4c4
set $inactive-text-color #676E7D
set $urgent-bg-color     #E53935
set $blue-color          #5DA8F4

# Window colors
client.focused          $bg-color           $bg-color          $text-color #2F353E          
client.unfocused        $inactive-bg-color $inactive-bg-color $inactive-text-color #2F353E
client.focused_inactive $inactive-bg-color $inactive-bg-color $inactive-text-color #2F353E 
client.urgent           $blue-color    $blue-color   $text-color #2F353E          

# i3wm bar
bar {
        # Bar program
        status_command i3blocks -c ~/.i3/i3blocks.conf
        

        # Position of the bar
        position top

        # Bar colors
        colors {
		      background #1f222d
	    	  separator #1f222d
		      #                  border             background         text
		      focused_workspace  #1f222d          #1f222d          $text-color
		      inactive_workspace #1f222d          #1f222d $inactive-text-color
	        urgent_workspace   #1f222d          #1f222d   $text-color
        }
}


# Remove green border on the left

for_window [class="^.*"] border pixel 2
#Lock
# Apps on start

exec --no-startup-id feh --bg-scale /home/fer/Imágenes/bg.jpg
