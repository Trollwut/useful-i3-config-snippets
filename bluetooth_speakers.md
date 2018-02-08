Creates an i3 mode to toggle connection with your Bluetooth device (e.g. speakers, Airpods, …)

Get your MAC address for your device and replace it in the following code (bind `c` and `d`):

    bindsym $mod+Home mode "$mode_btspeakers"
    set $mode_btspeakers Bluetooth Speakers: [c]onnect [d]isconnect [k]volumeup [j]volumedown
    mode "$mode_btspeakers" {
        bindsym Return mode "default"
        bindsym Escape mode "default"
    
        bindsym c exec dbus-send --system --type=method_call --dest=org.bluez "/org/bluez/hci0/dev_<MAC ADDRESS>" "org.bluez.Device1.Connect"; mode "default"
        bindsym d exec dbus-send --system --type=method_call --dest=org.bluez "/org/bluez/hci0/dev_<MAC ADDRESS>" "org.bluez.Device1.Disconnect"; mode "default"
        bindsym k exec pactl set-sink-volume bluez_sink.<MAC ADDRESS> +5%
        bindsym j exec pactl set-sink-volume bluez_sink.<MAC ADDRESS> -5%
    }
