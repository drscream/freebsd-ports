# Created by: Artyom Mirgorodskiy <artyom.mirgorodsky@gmail.com>
# $FreeBSD$

PORTNAME=	qt47-webkit
PORTVERSION=	4.7.2
PORTREVISION=	4
CATEGORIES=	www linux
MASTER_SITES=	LOCAL/tijl/atrpms:amd64,i386
SRC_DISTFILES=	# unavailable
DIST_SUBDIR=	atrpms

MAINTAINER=	emulation@FreeBSD.org
COMMENT=	Qt WebKit implementation (Linux CentOS ${LINUX_DIST_VER})

BROKEN=		uses non existing qt47 qt47-x11

DESCR=		${.CURDIR}/../../devel/qt4/pkg-descr
RPMVERSION=	1_18.el6
USES=		linux:c6
USE_LDCONFIG=	yes
USE_LINUX=	fontconfig png xorglibs sqlite3 qt47 qt47-x11
USE_LINUX_RPM=	yes

.include <bsd.port.mk>
