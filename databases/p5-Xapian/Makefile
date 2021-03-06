# Created by: Po-Chuan Hsieh <sunpoet@FreeBSD.org>
# $FreeBSD$

PORTNAME=	Xapian
PORTVERSION=	1.4.7.0
CATEGORIES=	databases perl5
MASTER_SITES=	https://oligarchy.co.uk/xapian/${PORTVERSION:R}/ \
		LOCAL/sunpoet
PKGNAMEPREFIX=	p5-
DISTNAME=	xapian-bindings-${PORTVERSION:R}

MAINTAINER=	sunpoet@FreeBSD.org
COMMENT=	Perl binding for Xapian

LICENSE=	GPLv2
LICENSE_FILE=	${WRKSRC}/COPYING

BUILD_DEPENDS=	xapian-core>=${PORTVERSION:R}:databases/xapian-core
LIB_DEPENDS=	libxapian.so:databases/xapian-core

OPTIONS_DEFINE=	DOCS

PORTSCOUT=	limitw:1,even

CONFIGURE_ARGS=	--datarootdir=${DATADIR} --docdir=${DOCSDIR} \
		--enable-static \
		--with-perl \
		--without-csharp --without-java --without-lua --without-php \
		--without-python --without-python3 --without-ruby --without-tcl
GNU_CONFIGURE=	yes
INSTALL_TARGET=	install-strip
LDFLAGS+=	-L${LOCALBASE}/lib/perl5/${PERL_VER}/mach/CORE -lperl
USES=		compiler:c++11-lang libtool perl5 tar:xz

PORTDOCS=	*

post-patch:
	@${REINPLACE_CMD} -e 's|-lstdc++||g' ${WRKSRC}/configure

post-patch-DOCS-off:
	@${REINPLACE_CMD} -e 's| install-dist_exampledataDATA install-docdataDATA||' ${WRKSRC}/perl/Makefile.in

post-install:
	${STRIP_CMD} ${STAGEDIR}${PREFIX}/${SITE_ARCH_REL}/auto/Xapian/Xapian.so

.include <bsd.port.mk>
