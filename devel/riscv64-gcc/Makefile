# $FreeBSD$

PORTNAME=	gcc
PORTVERSION=	8.1.0
CATEGORIES=	devel
PKGNAMEPREFIX=	riscv64-

MAINTAINER=	lwhsu@FreeBSD.org
COMMENT=	Cross GNU Compiler Collection for ${PKGNAMEPREFIX:C/-//g}

LICENSE=	GPLv3 GPLv3RLE
LICENSE_COMB=	multi

BUILD_DEPENDS=	${PKGNAMEPREFIX}binutils>0:devel/${PKGNAMEPREFIX}binutils
RUN_DEPENDS=	${PKGNAMEPREFIX}binutils>0:devel/${PKGNAMEPREFIX}binutils
LIB_DEPENDS=	libgmp.so:math/gmp \
		libmpfr.so:math/mpfr \
		libmpc.so:math/mpc

USES=	iconv gmake libtool makeinfo

USE_LDCONFIG=	yes

USE_GITHUB=	yes
GH_ACCOUNT=	freebsd-riscv
GH_PROJECT=	riscv-gcc
GH_TAGNAME=	7a5a908

GCC_TARGET=	${PKGNAMEPREFIX}unknown-${OPSYS:tl}${OSREL}

GNU_CONFIGURE=	yes
CONFIGURE_OUTSOURCE=	yes
CONFIGURE_ARGS=	--target=${GCC_TARGET} \
		--with-gxx-include-dir=/usr/include/c++/v1/ \
		--with-sysroot=/ \
		--without-newlib \
		--without-headers \
		--with-pkgversion="FreeBSD Ports Collection for ${PKGNAMEPREFIX:C/-//g}" \
		--with-system-zlib \
		--with-as=${LOCALBASE}/bin/${PKGNAMEPREFIX}unknown-${OPSYS:tl}${OSREL}-as \
		--with-ld=${LOCALBASE}/bin/${PKGNAMEPREFIX}unknown-${OPSYS:tl}${OSREL}-ld \
		--disable-werror \
		--enable-threads \
		--enable-tls \
		--enable-languages=c,c++ \
		--with-gmp=${LOCALBASE} \
		--with-mpfr=${LOCALBASE} \
		--with-mpc=${LOCALBASE} \
		--disable-libatomic \
		--disable-libmudflap \
		--disable-libssp \
		--disable-libquadmath \
		--disable-libgomp \
		--disable-nls \
		--disable-bootstrap \
		--disable-multilib

ALL_TARGET=	inhibit-libc=true all-gcc
INSTALL_TARGET=	inhibit-libc=true install-gcc

# Force build of a cross compiler even if the target matches the host.
CFLAGS+=	-DCROSS_DIRECTORY_STRUCTURE

PLIST_SUB=	GCC_TARGET=${GCC_TARGET} \
		GCC_VERSION=${PORTVERSION}

post-patch:
	@${REINPLACE_CMD} -e '/LIBSTDCXX/ s/stdc\+\+/c\+\+/g ' \
		${WRKSRC}//gcc/cp/g++spec.c
	@${REINPLACE_CMD} -e '/LOCAL_INCLUDE_DIR/ d ' \
		${WRKSRC}//gcc/Makefile.in

post-install:
	@if [ -d ${STAGEDIR}${PREFIX}/${INFO_PATH} ] ; then ${RM} -r ${STAGEDIR}${PREFIX}/${INFO_PATH}; fi
	@${RM} ${STAGEDIR}${PREFIX}/man/man7/*
	@${RM} -r ${STAGEDIR}${PREFIX}/lib/gcc/${GCC_TARGET}/${PORTVERSION}/include-fixed

BROKEN_aarch64=		fails to package

.include <bsd.port.mk>
