# Unit of Measurement

## Pixel

Symbol is `px`

Corresponds to actual pixels on the screen

## Scale Independent Pixel

Symbol is `sp`

This is like the dp unit, but it is also scaled by the user's font size preference. It is recommend you use this unit when specifying font sizes, so they will be adjusted for both the screen density and user's preference.

Use for Font Size only

## Density Independent Pixel

Symbol is `dip`

An abstract unit that is based on the physical density of the screen. These units are relative to a 160 dpi screen, so one dp is one pixel on a 160 dpi screen. The ratio of dp-to-pixel will change with the screen density, but not necessarily in direct proportion. Note: The compiler accepts both "dip" and "dp", though "dp" is more consistent with "sp".

Use for everything else