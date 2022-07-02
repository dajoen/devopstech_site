---
slug: fixes
title: Fixing QNAP Antivirus failure!
authors:
  - name: Jeroen Verhoeven
    title: Devopstech Site maintainer
    url: https://devopstech.site
    image_url: https://github.com/dajoen.png
tags: [fixes]
---

# Antivirus update failes on QNAP NAS

The Antivirus update job fails with the following error message

'[Antivirus] Failed to update virus definitions. No storage volume detected. Create a new volume'

## Fixing this

It seems that the config doesn´t know about the default system volume. When this response is empty:

```Shell
getcfg SHARE_DEF defVolMP -f /etc/config/def_share.info
```

To fix it, all you need to do is set the config to use a default volume. In most cases this will be be "/share/CACHEDEV1_DATA".

```Shell
sudo setcfg SHARE_DEF defVolMP -f /etc/config/def_share.info /share/CACHEDEV1_DATA
``` 

