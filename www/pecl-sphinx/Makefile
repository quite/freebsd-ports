# Created by: Max Baryshnikov <mephius@gmail.com>
# $FreeBSD$

PORTNAME=	sphinx
DISTVERSION=	1.3.3
PORTREVISION=	1
CATEGORIES=	www

MAINTAINER=	mephius@gmail.com
COMMENT=	Sphinx search engine php client

LICENSE=	PHP301

IGNORE_WITH_PHP=	70 71 72 73

LIB_DEPENDS=	libsphinxclient.so:textproc/libsphinxclient

USES=		php:pecl

SUB_FILES=	pkg-message

CFLAGS+=	-I${LOCALBASE}/include

.include <bsd.port.mk>
