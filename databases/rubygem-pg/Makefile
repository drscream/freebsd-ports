# Created by: Wen Heping <wenheping@gmail.com>
# $FreeBSD$

PORTNAME=	pg
PORTVERSION=	1.1.2
CATEGORIES=	databases rubygems
MASTER_SITES=	RG

MAINTAINER=	ruby@FreeBSD.org
COMMENT=	Ruby interface to PostgreSQL library

LICENSE=	BSD2CLAUSE RUBY
LICENSE_COMB=	dual
LICENSE_FILE_BSD2CLAUSE	=${WRKSRC}/BSDL
LICENSE_FILE_RUBY	=${WRKSRC}/LICENSE

CONFIGURE_ARGS=	--with-pgsql-include-dir=`${PG_CONFIG} --includedir` \
		--with-pgsql-lib-dir=`${PG_CONFIG} --libdir`
PG_CONFIG=	${LOCALBASE}/bin/pg_config
USE_RUBY=	yes
USES=		gem pgsql

.include <bsd.port.mk>
