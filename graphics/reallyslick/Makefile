# Created by: David Yeske <dyeske@gmail.com>
# $FreeBSD$

PORTNAME=	reallyslick
PORTVERSION=	0.9.1
PORTREVISION=	20
CATEGORIES=	graphics
MASTER_SITES=	SF/rss-glx/rss-glx/${PORTVERSION}
DISTNAME=	rss-glx_${PORTVERSION}

MAINTAINER=	ports@FreeBSD.org
COMMENT=	OpenGL screensaver collection

LIB_DEPENDS=	libMagickWand-6.so:graphics/ImageMagick \
		libGLC.so:graphics/quesoglc

USES=		compiler gmake pathfix pkgconfig tar:bzip2 libtool
USE_GL=		glut
GNU_CONFIGURE=	yes

CXXFLAGS+=	${CXXFLAGS_${CHOSEN_COMPILER_TYPE}}
CXXFLAGS_clang=	-Wno-c++11-narrowing
CPPFLAGS+=	-I${LOCALBASE}/include
LIBS+=		-L${LOCALBASE}/lib -lXext

OPTIONS_DEFINE=	FREEALUT GLEW

FREEALUT_DESC=	Enable freealut support
FREEALUT_CONFIGURE_ENABLE=	sound
FREEALUT_USES=	openal:alut
FREEALUT_VARS=	LLD_UNSAFE=yes # cf. PR 226980

GLEW_DESC=	Enable GLEW support
GLEW_USE=	GL=glew
GLEW_CONFIGURE_ENV_OFF=	ac_cv_header_GL_glew_h=no

post-patch:
	@${REINPLACE_CMD} '/LINK.*pixelcity/s/LINK/CXXLINK/' ${WRKSRC}/src/Makefile.in

.include <bsd.port.mk>
