# Created by: MANTANI Nobutaka <nobutaka@nobutaka.com>
# $FreeBSD$

PORTNAME=	wanderlust
PORTVERSION=	2.15.9.b.${SNAPDATE}
CATEGORIES=	mail elisp
PKGNAMESUFFIX=	${EMACS_PKGNAMESUFFIX}

MAINTAINER=	nobutaka@FreeBSD.org
COMMENT=	Mail and news system for Emacs

LICENSE=	GPLv2
LICENSE_FILE=	${WRKSRC}/COPYING

BUILD_DEPENDS=	emacs-w3m${EMACS_PKGNAMESUFFIX}>0:www/emacs-w3m@${EMACS_FLAVOR} \
		semi${EMACS_PKGNAMESUFFIX}>0:editors/semi@${EMACS_FLAVOR} \
		x-face-e21${EMACS_PKGNAMESUFFIX}>0:mail/x-face-e21@${EMACS_FLAVOR}
RUN_DEPENDS=	emacs-w3m${EMACS_PKGNAMESUFFIX}>0:www/emacs-w3m@${EMACS_FLAVOR} \
		semi${EMACS_PKGNAMESUFFIX}>0:editors/semi@${EMACS_FLAVOR}

USES=		emacs
EMACS_FLAVORS_EXCLUDE=	devel_full devel_nox # www/emacs-w3m fails to configure
USE_GITHUB=	yes
GH_TAGNAME=	f0c8c4e

NO_ARCH=	yes
SNAPDATE=	20180317

MAKE_ARGS+=	EMACS=${EMACS_CMD} \
		FLAGS="-batch -q -no-site-file" \
		LISPDIR=${STAGEDIR}${PREFIX}/${EMACS_SITE_LISPDIR} \
		INFODIR=${STAGEDIR}${PREFIX}/${INFO_PATH} \
		PIXMAPDIR=${STAGEDIR}${PREFIX}/${EMACS_LIBDIR}/etc/wl/icons

INFO=		wl wl-ja
PORTDATA=	ja.Emacs
PORTDOCS=	*
PORTEXAMPLES=	*

OPTIONS_DEFINE=	DOCS EXAMPLES

post-extract:
	@${CP} ${FILESDIR}/WL-CFG ${WRKSRC}

post-install:
	${INSTALL} -d ${STAGEDIR}${PREFIX}/${EMACS_SITE_LISPDIR}/wl \
		${STAGEDIR}${DATADIR}
	${INSTALL_DATA} ${FILESDIR}/wanderlust-startup.el \
		${STAGEDIR}${PREFIX}/${EMACS_SITE_LISPDIR}
	${INSTALL_DATA} \
		${WRKSRC}/elmo/elmo-shimbun.el \
		${WRKSRC}/utils/bbdb-wl.el \
		${STAGEDIR}${PREFIX}/${EMACS_SITE_LISPDIR}/wl
	${INSTALL_DATA} ${WRKSRC}/etc/ja.Emacs ${STAGEDIR}${DATADIR}

post-install-DOCS-on:
	${INSTALL} -d ${STAGEDIR}/${DOCSDIR}
.for f in README* NEWS* doc/wl*.texi
	${INSTALL_DATA} ${WRKSRC}/${f} ${STAGEDIR}${DOCSDIR}
.endfor

post-install-EXAMPLES-on:
	${INSTALL} -d ${STAGEDIR}/${EXAMPLESDIR}
	(cd ${WRKSRC}/samples && ${COPYTREE_SHARE} "en ja" \
		${STAGEDIR}${EXAMPLESDIR})
	${RM} ${STAGEDIR}${EXAMPLESDIR}/en/*.orig \
		${STAGEDIR}${EXAMPLESDIR}/ja/*.orig

.include <bsd.port.mk>
