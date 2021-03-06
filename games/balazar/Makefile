# Created by: Jose Alonso Cardenas Marquez <acardenas@bsd.org.pe>
# $FreeBSD$

PORTNAME=	balazar
PORTVERSION=	0.3.4
PORTREVISION=	9
CATEGORIES=	games python
MASTER_SITES=	http://download.gna.org/balazar/
DISTNAME=	Balazar-${PORTVERSION}

MAINTAINER=	ports@FreeBSD.org
COMMENT=	3D adventure and roleplaying game

LICENSE=	GPLv2+

LIB_DEPENDS=	libcal3d.so:graphics/cal3d \
		libfreetype.so:print/freetype2
RUN_DEPENDS=	${PYTHON_PKGNAMEPREFIX}soya3d>0:graphics/py-soya3d@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}openal>0:audio/py-openal@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}vorbis>0:audio/py-vorbis@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}tofu>0:net/py-tofu@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}cerealizer>0:security/py-cerealizer@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}twisted>=0:devel/py-twisted@${PY_FLAVOR}

NO_ARCH=	yes

USES=		gettext python:2.7 tar:bzip2
USE_GL=		glew
USE_SDL=	mixer sdl
USE_PYTHON=	autoplist distutils

PYDISTUTILS_PKGNAME=	Balazar
PYDISTUTILS_EGGINFODIR=	${PREFIX}/share

PORTDOCS=	README

DESKTOP_ENTRIES="Balazar" "" "" "balazar" "" ""

OPTIONS_DEFINE=	DOCS

post-patch:
	@${REINPLACE_CMD} -e \
		'/^install-purelib/s|=.*|= ${PREFIX}/share| ; \
		 /^install-scripts/s|=.*|= ${PREFIX}/bin| ; \
		 /^install-data/s|=.*|= ${PREFIX}/share|' ${WRKSRC}/setup.cfg
	@${REINPLACE_CMD} -e \
		'/LC_MESSAGES/s|".",||' ${WRKSRC}/setup.py

post-install:
	@${MKDIR} ${STAGEDIR}${DOCSDIR}
	(cd ${WRKSRC} && ${INSTALL_DATA} ${PORTDOCS} ${STAGEDIR}${DOCSDIR})

.include <bsd.port.mk>
