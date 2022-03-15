```
                
 _ __ ___   ___ 
| '_ ` _ \ / __|
| | | | | | (__ 
|_| |_| |_|\___|
                
```
**Package:** mc  
**Version:** 3:4.8.26-1.1  
**Priority:** optional  
**Section:** universe/utils  
**Origin:** Ubuntu  
**Maintainer:** Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>  
**Original-Maintainer:** Dmitry Smirnov <onlyjob@debian.org>  
**Bugs:** https://bugs.launchpad.net/ubuntu/+filebug  
**Installed-Size:** 1 573 kB  
**Provides:** mcedit  
**Depends:** libc6 (>= 2.33), libext2fs2 (>= 1.37), libglib2.0-0 (>= 2.59.2), libgpm2 (>= 1.20.7), libslang2 (>= 2.2.4), libssh2-1 (>= 1.2.8), mc-data (= 3:4.8.26-1.1)  
**Recommends:** mime-support, perl, unzip, sensible-utils  
**Suggests:** arj, bzip2, catdvi | texlive-binaries, dbview, djvulibre-bin, epub-utils, file, genisoimage, gv, imagemagick, libaspell-dev, links | w3m | lynx, odt2txt, poppler-utils, python, python-boto, python-tz, unar, wimtools, xpdf | pdf-viewer, zip  
**Homepage:** https://www.midnight-commander.org  
**Download-Size:** 507 kB  
**APT-Manual-Installed:** yes  
**APT-Sources:** http://archive.ubuntu.com/ubuntu impish/universe amd64 Packages  
**Description:** Midnight Commander - многофункциональный диспетчер файлов  
 GNU Midnight Commander – полноэкранный текстовый файловый менеджер. В нём  
 используется двухпанельный интерфейс и встроенная командная оболочка.  
 Также имеется встроенный редактор с подсветкой синтаксиса и просмотрщик,  
 поддерживающий двоичные файлы. Программа поддерживает виртуальную файловую  
 систему (VFS), что позволяет работать с файлами на удалённых машинах  
 (например, на серверах FTP, SSH) и с файлами внутри архивов, как с  
 обычными файлами.  
  

## Файл Preinst

```
#!/bin/sh
set -e
# Automatically added by dh_installdeb/13.3.4ubuntu1
dpkg-maintscript-helper rm_conffile /etc/mc/edit.spell.rc 3:4.8.5-1 -- "$@"
dpkg-maintscript-helper rm_conffile /etc/mc/mc.charsets 3:4.8-1 -- "$@"
dpkg-maintscript-helper rm_conffile /etc/mc/mc.lib 3:4.8-1 -- "$@"
dpkg-maintscript-helper rm_conffile /etc/mc/Syntax 3:4.8-1 -- "$@"
dpkg-maintscript-helper rm_conffile /etc/mc/mc.menu.sr 3:4.8.17-0 -- "$@"
dpkg-maintscript-helper mv_conffile /etc/mc/cedit.menu /etc/mc/mcedit.menu 3:4.8-1 -- "$@"
dpkg-maintscript-helper mv_conffile /etc/mc/mc.keymap.emacs /etc/mc/mc.emacs.keymap 3:4.8.8-0 -- "$@"
dpkg-maintscript-helper mv_conffile /etc/mc/mc.keymap.default /etc/mc/mc.default.keymap 3:4.8.8-0 -- "$@"
# End automatically added section
```

## Файл Postinst

```
#!/bin/sh
set -e

case "$1" in
	configure|abort-upgrade)
		update-alternatives --install /usr/bin/view view /usr/bin/mcview 25 \
			--slave /usr/share/man/man1/view.1.gz view.1.gz /usr/share/man/man1/mcview.1.gz
		update-alternatives --install /usr/bin/editor editor /usr/bin/mcedit 25 \
			--slave /usr/share/man/man1/editor.1.gz editor.1.gz /usr/share/man/man1/mcedit.1.gz
	;;
esac

# Automatically added by dh_installdeb/13.3.4ubuntu1
dpkg-maintscript-helper rm_conffile /etc/mc/edit.spell.rc 3:4.8.5-1 -- "$@"
dpkg-maintscript-helper rm_conffile /etc/mc/mc.charsets 3:4.8-1 -- "$@"
dpkg-maintscript-helper rm_conffile /etc/mc/mc.lib 3:4.8-1 -- "$@"
dpkg-maintscript-helper rm_conffile /etc/mc/Syntax 3:4.8-1 -- "$@"
dpkg-maintscript-helper rm_conffile /etc/mc/mc.menu.sr 3:4.8.17-0 -- "$@"
dpkg-maintscript-helper mv_conffile /etc/mc/cedit.menu /etc/mc/mcedit.menu 3:4.8-1 -- "$@"
dpkg-maintscript-helper mv_conffile /etc/mc/mc.keymap.emacs /etc/mc/mc.emacs.keymap 3:4.8.8-0 -- "$@"
dpkg-maintscript-helper mv_conffile /etc/mc/mc.keymap.default /etc/mc/mc.default.keymap 3:4.8.8-0 -- "$@"
# End automatically added section
```

## Файл Prerm

```
#!/bin/sh
set -e

case "$1" in
	remove)
		update-alternatives --remove editor /usr/bin/mcedit
		update-alternatives --remove view /usr/bin/mcview
	;;
esac

# Automatically added by dh_installdeb/13.3.4ubuntu1
dpkg-maintscript-helper rm_conffile /etc/mc/edit.spell.rc 3:4.8.5-1 -- "$@"
dpkg-maintscript-helper rm_conffile /etc/mc/mc.charsets 3:4.8-1 -- "$@"
dpkg-maintscript-helper rm_conffile /etc/mc/mc.lib 3:4.8-1 -- "$@"
dpkg-maintscript-helper rm_conffile /etc/mc/Syntax 3:4.8-1 -- "$@"
dpkg-maintscript-helper rm_conffile /etc/mc/mc.menu.sr 3:4.8.17-0 -- "$@"
dpkg-maintscript-helper mv_conffile /etc/mc/cedit.menu /etc/mc/mcedit.menu 3:4.8-1 -- "$@"
dpkg-maintscript-helper mv_conffile /etc/mc/mc.keymap.emacs /etc/mc/mc.emacs.keymap 3:4.8.8-0 -- "$@"
dpkg-maintscript-helper mv_conffile /etc/mc/mc.keymap.default /etc/mc/mc.default.keymap 3:4.8.8-0 -- "$@"
# End automatically added section
```

## Файл Postrm

```
#!/bin/sh
set -e

case "$1" in
	purge)

		rm -f \
			/etc/mc/cedit.menu \
			/etc/mc/*.ini \
			/etc/mc/mc.* \
			/etc/mc/*.rc \
			/etc/mc/Syntax

		rmdir /etc/mc 2>/dev/null || true

	;;
esac

# Automatically added by dh_installdeb/13.3.4ubuntu1
dpkg-maintscript-helper rm_conffile /etc/mc/edit.spell.rc 3:4.8.5-1 -- "$@"
dpkg-maintscript-helper rm_conffile /etc/mc/mc.charsets 3:4.8-1 -- "$@"
dpkg-maintscript-helper rm_conffile /etc/mc/mc.lib 3:4.8-1 -- "$@"
dpkg-maintscript-helper rm_conffile /etc/mc/Syntax 3:4.8-1 -- "$@"
dpkg-maintscript-helper rm_conffile /etc/mc/mc.menu.sr 3:4.8.17-0 -- "$@"
dpkg-maintscript-helper mv_conffile /etc/mc/cedit.menu /etc/mc/mcedit.menu 3:4.8-1 -- "$@"
dpkg-maintscript-helper mv_conffile /etc/mc/mc.keymap.emacs /etc/mc/mc.emacs.keymap 3:4.8.8-0 -- "$@"
dpkg-maintscript-helper mv_conffile /etc/mc/mc.keymap.default /etc/mc/mc.default.keymap 3:4.8.8-0 -- "$@"
# End automatically added section
```
