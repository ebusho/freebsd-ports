# Created by: Jose Alonso Cardenas Marquez <acardenas@bsd.org.pe>
# $FreeBSD$

PORTNAME=	django
PORTVERSION=	1.11.26
CATEGORIES=	www python
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}

MAINTAINER=	python@FreeBSD.org
COMMENT=	High-level Python Web Framework (meta port)

LICENSE=	BSD3CLAUSE

OPTIONS_SINGLE=	DJANGO
OPTIONS_SINGLE_DJANGO=	DJANGO111 DJANGO22
OPTIONS_DEFAULT=DJANGO111
DJANGO111_DESC=	Use Django 1.11.x
DJANGO22_DESC=	USe Django 2.2.x

PORTSCOUT=	ignore:1

USES=		cpe metaport python:run
USE_PYTHON=	flavors

CPE_VENDOR=	djangoproject

DJANGO111_RUN_DEPENDS=	${PYTHON_PKGNAMEPREFIX}django111>=0:www/py-django111@${PY_FLAVOR}
DJANGO22_RUN_DEPENDS=	${PYTHON_PKGNAMEPREFIX}django22>=0:www/py-django22@${PY_FLAVOR}

.include <bsd.port.mk>
