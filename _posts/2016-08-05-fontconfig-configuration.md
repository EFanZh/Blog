# EFanZh’s Fontconfig configuration

Global configuration file is: `/etc/fonts/local.conf`. User configuration file is: `$HOME/.config/fontconfig/fonts.conf`.

```xml
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
    <alias>
        <family>sans-serif</family>
        <prefer>
            <family>Source Sans Pro</family>
            <family>Source Han Sans SC</family>
        </prefer>
    </alias>
    <alias>
        <family>monospace</family>
        <prefer>
            <family>Source Code Pro</family>
            <family>Source Han Sans SC</family>
        </prefer>
    </alias>
    <match target="font">
        <edit name="lcdfilter" mode="assign"><const>lcddefault</const></edit>
        <edit name="rgba" mode="assign"><const>rgb</const></edit>
    </match>
</fontconfig>
```
