## Customized dcraw with -O support for ImageMagick delegates
-- based on [Dave Coffin's work](http://www.cybercom.net/~dcoffin/dcraw/)

### Install
```
apt-get install libjasper-dev libjpeg8-dev liblcms2-dev gettext
chmod +x install
./install
```

### Configure ImageMagick
In /etc/ImageMagick/delegates.xml, replace

`<delegate decode="dng:decode" command="&quot;ufraw-batch&quot; --silent --create-id=also --out-type=png --out-depth=16 &quot;--output=%u.png&quot; &quot;%i&quot;"/>`

with

`<delegate decode="dng:decode" stealth="True" command="/usr/local/bin/dcraw -6 -W -O &quot;%u.ppm&quot; &quot;%i&quot;"/>`
