---
layout: post
title: yaourt -Syua error
comments: true
---

在archlinux 中使用yaourt -Syua 更新系统，出现下列错误:

    error: failed to commit transaction (conflicting files)
    initscripts: /etc/profile.d/locale.sh exists in filesystem
    Errors occurred, no packages were upgraded.

可以使用
    sudo mv /etc/profile.d/locale.sh{,-backup}
然后重新执行yaourt -Syua 更新系统。 <!-- more -->
