# Open a floating terminal app

This opens a CLI program (`htop` in this example) in a floating terminal with a set size. You might add a `set $term urxvt` at the beginning of your i3 config or just replace it with your favorite terminal:

    # open task manager
    bindsym --release $mod+Escape exec $term -name systaskmanager -geometry 150x50 -e htop
    for_window [instance="systaskmanager"] floating enable
