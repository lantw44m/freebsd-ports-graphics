# $FreeBSD$

PORTNAME=	eternalterminal
DISTVERSIONPREFIX=	et-v
DISTVERSION=	4.2.1
CATEGORIES=	net

MAINTAINER=	trevis@silencedpoet.com
COMMENT=	Remote shell that reconnects without interrupting session

LICENSE=	APACHE20
LICENSE_FILE=	${WRKSRC}/LICENSE

LIB_DEPENDS=	libgflags.so:devel/gflags \
		libglog.so:devel/glog \
		libprotobuf.so:devel/protobuf \
		libsodium.so:security/libsodium

USES=		cmake:outsource ncurses
USE_GITHUB=	yes
GH_ACCOUNT=	MisterTea
GH_PROJECT=	EternalTerminal

PLIST_FILES=	bin/et bin/etserver

.include <bsd.port.mk>
