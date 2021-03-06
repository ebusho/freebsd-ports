# $FreeBSD$

PORTNAME=	pdf-tools
DISTVERSIONPREFIX=	v
DISTVERSION=	0.90-34
DISTVERSIONSUFFIX=	-g29d9f4f
PORTREVISION=	3
CATEGORIES=	print elisp
PKGNAMESUFFIX=	${EMACS_PKGNAMESUFFIX}

MAINTAINER=	jrm@FreeBSD.org
COMMENT=	Emacs support library for PDF files

LICENSE=	GPLv3+
LICENSE_FILE=	${WRKSRC}/COPYING

BROKEN_powerpc64=	fails to configure: cannot find necessary poppler-private header (see README.org)

BUILD_DEPENDS=	cask${EMACS_PKGNAMESUFFIX}>0:devel/cask@${EMACS_FLAVOR} \
		tablist${EMACS_PKGNAMESUFFIX}>=0.70.4:devel/tablist@${EMACS_FLAVOR}
LIB_DEPENDS=	libMagickCore-6.so:graphics/ImageMagick6 \
		libpng.so:graphics/png \
		libpoppler-glib.so:graphics/poppler-glib \
		libpoppler.so:graphics/poppler
RUN_DEPENDS=	tablist${EMACS_PKGNAMESUFFIX}>=0.70:devel/tablist@${EMACS_FLAVOR}

USES=		autoreconf:build emacs gettext-runtime gmake gnome
USE_GITHUB=	yes
GH_ACCOUNT=	politza
USE_GNOME=	cairo glib20

EMACS_FLAVORS_EXCLUDE=	devel_nox nox

do-build:
	cd ${WRKSRC}/server && ./autogen.sh && ./configure -q && make
	${EMACS_CMD} -q --batch -L ${WRKSRC}/lisp -f batch-byte-compile \
		${WRKSRC}/lisp/*.el
	${EMACS_CMD} -q --batch \
		--eval "(setq generated-autoload-file \
			\"${WRKSRC}/lisp/${PORTNAME}-loaddefs.el\" \
			backup-inhibited t)" \
		-f batch-update-autoloads ${WRKSRC}/lisp

do-install:
	@${MKDIR} ${STAGEDIR}${PREFIX}/${EMACS_SITE_LISPDIR}/${PORTNAME}
	${INSTALL_PROGRAM} ${WRKSRC}/server/epdfinfo ${STAGEDIR}${PREFIX}/bin
	${INSTALL_DATA} ${WRKSRC}/lisp/* ${FILESDIR}/${PORTNAME}-init.el \
		${STAGEDIR}${PREFIX}/${EMACS_SITE_LISPDIR}/${PORTNAME}

.include <bsd.port.mk>
