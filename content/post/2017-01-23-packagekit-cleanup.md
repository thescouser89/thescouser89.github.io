---
date: 2017-01-23T00:00:00Z
title: PackageKit Memory Cleanup
url: /2017/01/23/packagekit-cleanup/
---

I've been using Fedora for a while now and have upgraded from Fedora 24 to
Fedora 25 without any issues. I've noticed that my root partition (I also have
a separate one for `/home`) kept getting filled up and I wasn't really sure
why. I have finally run `du -sh` like a madman trying to figure out which
folder was eating all my precious HD space. It turns out it was PackageKit's
fault...

Apparently PackageKit heavily caches all the rpms it downloads and does not
clean up after its mess. To help PackageKit clean up, run this command:

```bash
cd /var/cache/PackageKit/metadata/updates/packages
sudo rm -rf *
```
