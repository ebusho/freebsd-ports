# Created by: Jean-Sébastien Pédron <dumbbell@FreeBSD.org>
# $FreeBSD$

PORTVERSION=	1.42.0.${NIGHTLY_DATE:C,-,,g}
# Always set PORTREVISION explicitly as otherwise it is inherited from lang/rust
PORTREVISION=	0
PKGNAMESUFFIX=	-nightly
DISTNAME=	rustc-nightly-src

MASTERDIR=	${.CURDIR}/../rust
PATCHDIR=	${.CURDIR}/files
DISTINFO_FILE=	${.CURDIR}/distinfo

CONFLICTS_INSTALL=	rust

# Which source to pull:
#   https://static.rust-lang.org/dist/${NIGHTLY_DATE}/rustc-nightly-src.tar.gz
#   https://static.rust-lang.org/dist/channel-rust-nightly.toml
NIGHTLY_DATE=			2020-01-24
NIGHTLY_SUBDIR=			${NIGHTLY_DATE}/

# See WRKSRC/src/stage0.txt for this date
# XXX: Keep on nightly after 2020-01-24 for 13.0 i386 until beta has
# https://github.com/rust-lang/rust/commit/de388032555b697d1b0ef197241886ab90ac39b2
BOOTSTRAPS_DATE=		${NIGHTLY_DATE}
RUST_BOOTSTRAP_VERSION=		nightly
CARGO_BOOTSTRAP_VERSION=	nightly

CARGO_VENDOR_DIR=	${WRKSRC}/vendor

# Other bootstraps aren't provided by upstream yet
ONLY_FOR_ARCHS=			amd64 i386

post-configure:
# Don't abort if optional tools fail to build
# https://github.com/rust-lang/rust/commit/53254a888b42
	@${ECHO_CMD} 'missing-tools = true' >>${WRKSRC}/config.toml

.include "${MASTERDIR}/Makefile"
