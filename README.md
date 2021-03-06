# Ubic

[![Maintainers Wanted](https://img.shields.io/badge/maintainers-wanted-red.svg)](https://github.com/pickhardt/maintainers-wanted)

> **My priorities have changed and I can't promise the proper maintainence of this software anymore. The codebase is solid enough to be used without any significant issues, though. Feel free to ask me for a commit bit if you want to fix something or take over completely.**
>
> -- [@berekuk](https://github.com/berekuk)

Ubic is a polymorphic service manager.

"Polymorphic" means that Ubic can use various pluggable backends for managing services, for configuring services and even for describing a list of all services.
Don't panic, it offers easy-to-use default solutions for the common tasks out-of-the-box too!

## 1 minute intro

Put this code in file `/etc/ubic/service/example.ini`:

    [options]
    bin = sleep 100

Start it:

    $ ubic start example
    Starting example... started (pid 41209)

Check its status:

    $ ubic status
    example running (pid 41209)
    ubic
        ubic.ping   off
        ubic.update off
        ubic.watchdog   running (pid 93226)

Or:

    $ ubic status example
    example running (pid 41209)

Now let's see how watchdog works by killing the process (don't forget to change pid with the pid you got in status command above):

    $ kill 41209

    $ ubic status example
    example not running

    $ ubic-watchdog
    [Thu May 26 20:20:54 2011]  example is broken, restarting

You don't have to run ubic-watchdog manually; it will do its work in background in a minute.

Read [Ubic::Manual::Intro](https://metacpan.org/module/Ubic::Manual::Intro) and [Ubic::Manual::Overview](https://metacpan.org/module/Ubic::Manual::Overview) for more.

## Installation

Run 'cpan -i Ubic && ubic-admin setup' to install Ubic.

We also provide .deb packages for Debian/Ubuntu. Latest .deb package can be downloaded from ppa:berekuk/ubic (see <https://launchpad.net/~berekuk/+archive/ubic> for details).

Debian package build can be reproduced with this command:
    dzil build && cd Ubic* && cp -r ../debian . && debuild

Rpm package can be created with this command:
    rpmbuild -ba redhat/perl-Ubic.spec

If you'll write an ebuild for Gentoo, please contribute it back :)

## Documentation

After installing, you can find documentation for this module using perldoc
and man commands.

    man ubic
    perldoc Ubic

You can also look for information at:

* [Github Wiki](http://github.com/berekuk/Ubic/wiki)
* [CPAN](https://metacpan.org/release/Ubic)

## Support

There is also a low-volume mailing list is <ubic-perl@googlegroups.com>. Send an empty message to <ubic-perl+subscribe@googlegroups.com> to subscribe.


## Copyright and licence

Copyright (c) 2009-2012 Yandex LTD. All rights reserved.

This program is free software; you can redistribute it and/or modify it under the same terms as Perl itself.

See <http://www.perl.com/perl/misc/Artistic.html>
