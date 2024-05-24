
# Arch Linux Configs


If you have a high DPI screen, you must adjust your `~/.Xresources` and add `Xft.dpi: 192`. If one does not exist already, create one inside your home directory at `/~`.

**~/.Xresources**
```
Xft.dpi: 192
```
Make sure to merge `xrdb` with your `.Xresources` file:
```
xrdb -merge ~/.Xresources
```

You also need to adjust the GRUB bootloader DPI by creating a new grub font with `grub mk-font`

Use the following command template as an example to generate a new font.
```
sudo grub-mkfont --output=/boot/grub/fonts/DejaVuSansMono24.pf2 
  --size=24 /usr/share/fonts/truetype/dejavu/DejaVuSansMono.ttf
```
You must also go into your grub config file at `/etc/default/grub` and add:
`GRUB_FONT=/boot/grub/fonts/DejaVuSansMono24.pf2`

Now update grub with:
`sudo grub-mkconfig -o /boot/grub/grub.cfg`
