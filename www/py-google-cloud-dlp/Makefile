# $FreeBSD$

PORTNAME=	google-cloud-dlp
PORTVERSION=	0.8.0
CATEGORIES=	www python
MASTER_SITES=	CHEESESHOP
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}

MAINTAINER=	jpaetzel@FreeBSD.org
COMMENT=	Python Client for Google Cloud Data Loss Prevention

LICENSE=	APACHE20
LICENSE_FILE=	${WRKSRC}/LICENSE

RUN_DEPENDS=	${PYTHON_PKGNAMEPREFIX}google-api-core>=0.1.1:www/py-google-api-core@${PY_FLAVOR}

USES=		python
USE_PYTHON=	distutils autoplist

NO_ARCH=	yes

.include <bsd.port.mk>
