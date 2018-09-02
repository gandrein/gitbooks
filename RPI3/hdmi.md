# Changing HDMI Resolution

## Switching screen on/off

Use

* `tvservice -o | --off`\) turns off the display
* `tvservice -p | --preferred`\) turns on the display \(no command prompt will be visible\)

Most likely what will happen is that the TV/Screen won't display anything when switched on via the last command above and needs refreshed.

According to this forum [link](https://www.raspberrypi.org/forums/viewtopic.php?t=52309)\)

> When changing the resolution of the framebuffer device \(console\), you can use the fbset command to force a refresh of the screen and to change resolution. First do a dummy sudo fbset -depth 8 to make it realise something has changed, then sudo fbset -g X Y X Y D where X and Y are the resolution of your screen, and D is the bits-per-pixel value you are using \(probably 16 unless you have changed it\).

Hence doing this commands one after the other, should do the trick

```text
tvservice -o
tvservice -p 
fbset -depth 8
fbset -g 1280 720 1280 720 16
```

For alternative methods to switch on/off \(not tried\)

* see this [link](https://www.screenly.io/blog/2017/07/02/how-to-automatically-turn-off-and-on-your-monitor-from-your-raspberry-pi/)
* or this [link](https://raspberrypi.stackexchange.com/questions/52042/turning-tvservice-on-and-off-leaves-screen-blank/53267) which says

  > tvservice is not the best to turn off and on the screen. Much better way to do this \(found after a day of searching\) is using vcgencmd command \(more on this here\).
  >
  > ```text
  > vcgencmd display_power 0 turns off the screen
  > vcgencmd display_power 1 turns on the screen
  > ```
  >
  > This allows the Qt application to be visible on the screen after turning it off and back on.

## Changing resolution

Changing TV screen resolution with `tvservice` and `fbset`.

* `tvservice -e | --explicit` sets the resolution and aspect ratio, e.g. `tvservice --explicit="CEA 16 HDMI"`

However, this is not sufficient and one needs to force a refresh of the screen. Using the suggestion mentioned above [link](https://www.raspberrypi.org/forums/viewtopic.php?t=52309), do the following

> First do a dummy sudo fbset -depth 8 to make it realise something has changed, then sudo fbset -g X Y X Y D where X and Y are the resolution of your screen, and D is the bits-per-pixel value you are using \(probably 16 unless you have changed it\).

```text
fbset -depth 8
fbset -g 1280 720 1280 720 16
```

So, to manipulate the TV/Screen resolution of my old LG TV I need to do this

```text
tvservice --explicit="CEA 16 HDMI"   # sets the TV to 1080p
fbset -depth 8          # dummy fbset as rpdom advised
fbset -g 1366 768 1366 768 16
```

since I have such a [weird resolution](http://www.backoffice.be/prod_uk/LG_Electronics/32lc25r_lg_32lc25r_32_dquote_lcd_tv_widescreen_720p_hd_rea.asp)

