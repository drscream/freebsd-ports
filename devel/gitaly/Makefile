# $FreeBSD$

PORTNAME=	gitaly
DISTVERSION=	0.117.2
CATEGORIES=	devel

MAINTAINER=	mfechner@FreeBSD.org
COMMENT=	Smart reverse proxy for GitLab

LICENSE=	MIT
LICENSE_FILE=	${WRKSRC}/LICENSE

# define dependencies that are required for build and run under MY_DEPENDS
MY_DEPENDS=	git>=2.17:devel/git \
		rubygem-i18n>=0:devel/rubygem-i18n \
		rubygem-rugged>=0.27.4:devel/rubygem-rugged \
		rubygem-github-linguist53>=5.3.3:textproc/rubygem-github-linguist53 \
		rubygem-bundler>0:sysutils/rubygem-bundler \
		rubygem-gitlab-markup>=1.6.4:textproc/rubygem-gitlab-markup \
		rubygem-gitaly-proto>=0.107.0:net/rubygem-gitaly-proto \
		rubygem-activesupport50>=5.0.2:devel/rubygem-activesupport50 \
		rubygem-rdoc>=6.0:devel/rubygem-rdoc \
		rubygem-gitlab-gollum-lib>=4.2:www/rubygem-gitlab-gollum-lib \
		rubygem-gitlab-gollum-rugged_adapter>=0.4.4:www/rubygem-gitlab-gollum-rugged_adapter \
		rubygem-grpc>=1.11.0:net/rubygem-grpc \
		rubygem-sentry-raven>=2.7.2:devel/rubygem-sentry-raven \
		rubygem-faraday>=0.12:www/rubygem-faraday \
		rubygem-licensee8>=8.9.0:devel/rubygem-licensee8 \
		rubygem-google-protobuf351>=3.5.1:devel/rubygem-google-protobuf351

BUILD_DEPENDS=	go>=1.9:lang/go \
		gem:devel/ruby-gems \
		${MY_DEPENDS}

RUN_DEPENDS=	${MY_DEPENDS} \
		gitlab-shell>=6.0.4:devel/gitlab-shell

USES=		gmake
USE_RUBY=	yes

USE_GITLAB=	yes
GL_ACCOUNT=	gitlab-org
# Find this here: https://gitlab.com/gitlab-org/gitaly/tags
GL_COMMIT=	93cc4119d91af9644da2b748f2563fd67ee5b855

post-patch:
	${REINPLACE_CMD} -e "s|%%PREFIX%%|${PREFIX}|" ${WRKSRC}/config.toml.example
	${MV} ${WRKSRC}/config.toml.example ${WRKSRC}/config.toml.sample

do-install:
	${MKDIR} ${STAGEDIR}${DATADIR}
	${MKDIR} ${STAGEDIR}${DATADIR}/bin
	${FIND} ${WRKSRC} -name '*.orig' -delete
	${FIND} ${WRKSRC} -name "Gemfile.lock" -delete
	(cd ${WRKSRC}/_build/bin/ && ${COPYTREE_SHARE} .  ${STAGEDIR}${DATADIR}/bin && \
	cd ${WRKSRC} && ${COPYTREE_SHARE} config.toml.sample  ${STAGEDIR}${DATADIR}) && \
	cd ${WRKSRC}/ruby && ${COPYTREE_SHARE} . ${STAGEDIR}${DATADIR}/ruby

post-install:
	${STRIP_CMD} ${STAGEDIR}${DATADIR}/bin/gitaly
	${STRIP_CMD} ${STAGEDIR}${DATADIR}/bin/gitaly-ssh

.include <bsd.port.mk>
