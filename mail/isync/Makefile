# Created by: eivind
# $FreeBSD$

PORTNAME=	isync
PORTVERSION=	1.3.0
PORTREVISION=	1
CATEGORIES=	mail
MASTER_SITES=	SF

MAINTAINER=	ehaupt@FreeBSD.org
COMMENT=	Maintain local copies of remote IMAP folders w/synchronized flags

LICENSE=	GPLv2

BROKEN_mips=		fails to compile: util.c:523: \#pragma GCC diagnostic not allowed inside functions
BROKEN_mips64=		fails to compile: util.c:523: \#pragma GCC diagnostic not allowed inside functions
BROKEN_powerpc64=	fails to compile: util.c:523: \#pragma GCC diagnostic not allowed inside functions

LIB_DEPENDS=	libsasl2.so:security/cyrus-sasl2

USES=		alias bdb cpe perl5 ssl
USE_PERL5=	build

GNU_CONFIGURE=	yes
CPE_VENDOR=	oswald_buddenhagen

CONFIGURE_ARGS=	--with-sasl=${LOCALBASE} \
		--with-ssl=${OPENSSLLIB:H}

MAKE_ARGS+=	SSL_LIBS="-L${OPENSSLLIB} -lssl -lcrypto"

CPPFLAGS+=	-I${BDB_INCLUDE_DIR}
LDFLAGS+=	-L${BDB_LIB_DIR}

post-patch:
	@${REINPLACE_CMD} -e 's|: install-docDATA|:|g' ${WRKSRC}/Makefile.in
	@${REINPLACE_CMD} -e 's|\$$(docdir)/examples|\$$(sysconfdir)|g' \
	    ${WRKSRC}/src/Makefile.in ${WRKSRC}/src/compat/Makefile.in
	@${REINPLACE_CMD} -e 's|-ansi||g' ${WRKSRC}/${CONFIGURE_SCRIPT}

.include <bsd.port.mk>
