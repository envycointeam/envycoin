include Makefile.include

AM_CPPFLAGS += -I$(builddir)

noinst_LIBRARIES = \
  libbitcoin_server.a \
  libbitcoin_common.a \
  libbitcoin_cli.a
if ENABLE_WALLET
noinst_LIBRARIES += \
  libbitcoin_wallet.a \
  libbitcoin_server_wallet.a
endif

bin_PROGRAMS =

if BUILD_BITCOIND
  bin_PROGRAMS += envycoind
endif

if BUILD_BITCOIN_CLI
  bin_PROGRAMS += envycoin-cli
endif

SUBDIRS = . $(BUILD_QT)
DIST_SUBDIRS = . qt
.PHONY: FORCE
# bitcoin core #
BITCOIN_CORE_H = \
  addrman.h \
  alert.h \
  sendalert.h \
  allocators.h \
  base58.h bignum.h \
  bloom.h \
  chainparams.h \
  checkpoints.h \
  checkqueue.h \
  clientversion.h \
  coincontrol.h \
  coins.h \
  compat.h \
  core.h \
  crypter.h \
  db.h \
  hash.h \
  init.h \
  key.h \
  keystore.h \
  leveldbwrapper.h \
  limitedmap.h \
  main.h \
  miner.h \
  mruset.h \
  netbase.h \
  net.h \
  noui.h \
  protocol.h \
  rpcclient.h \
  rpcprotocol.h \
  rpcserver.h \
  script.h \
  sph_blake.h sph_cubehash.h sph_groestl.h sph_keccak.h sph_shavite.h sph_skein.h \
  sph_bmw.h sph_echo.h sph_jh.h sph_luffa.h sph_simd.h sph_types.h \
  hashblock.h \
  serialize.h \
  sync.h \
  threadsafety.h \
  tinyformat.h \
  txdb.h \
  txmempool.h \
  ui_interface.h \
  uint256.h \
  util.h \
  version.h \
  walletdb.h \
  wallet.h

JSON_H = \
  json/json_spirit.h \
  json/json_spirit_error_position.h \
  json/json_spirit_reader.h \
  json/json_spirit_reader_template.h \
  json/json_spirit_stream_reader.h \
  json/json_spirit_utils.h \
  json/json_spirit_value.h \
  json/json_spirit_writer.h \
  json/json_spirit_writer_template.h

obj/build.h: FORCE
	@$(MKDIR_P) $(abs_top_builddir)/src/obj
	@$(top_srcdir)/share/genbuild.sh $(abs_top_builddir)/src/obj/build.h \
	  $(abs_top_srcdir)
version.o: obj/build.h

libbitcoin_server_a_SOURCES = \
  addrman.cpp \
  alert.cpp \
  sendalert.cpp \
  rpcserver.cpp \
  bloom.cpp \
  chainparams.cpp \
  checkpoints.cpp \
  coins.cpp \
  init.cpp \
  keystore.cpp \
  leveldbwrapper.cpp \
  main.cpp \
  miner.cpp \
  net.cpp \
  noui.cpp \
  rpcblockchain.cpp \
  rpcmining.cpp \
  rpcmisc.cpp \
  rpcnet.cpp \
  rpcrawtransaction.cpp \
  txdb.cpp \
  txmempool.cpp \
  $(JSON_H) \
  $(BITCOIN_CORE_H)

libbitcoin_wallet_a_SOURCES = \
  db.cpp \
  crypter.cpp \
  wallet.cpp \
  walletdb.cpp \
  $(BITCOIN_CORE_H)

libbitcoin_server_wallet_a_SOURCES = \
  rpcdump.cpp \
  rpcwallet.cpp \
  $(BITCOIN_CORE_H)

libbitcoin_common_a_SOURCES = \
  allocators.cpp \
  chainparams.cpp \
  core.cpp \
  hash.cpp \
  key.cpp \
  netbase.cpp \
  protocol.cpp \
  rpcprotocol.cpp \
  script.cpp \
  aes_helper.c \
  blake.c \
  bmw.c \
  cubehash.c \
  echo.c \
  groestl.c \
  jh.c \
  keccak.c \
  luffa.c \
  shavite.c \
  simd.c \
  skein.c \
  sync.cpp \
  util.cpp \
  version.cpp \
  $(BITCOIN_CORE_H)

libbitcoin_cli_a_SOURCES = \
  rpcclient.cpp \
  $(BITCOIN_CORE_H)

nodist_libbitcoin_common_a_SOURCES = $(top_srcdir)/src/obj/build.h
#

# envycoind binary #
envycoind_LDADD = \
  libbitcoin_server.a \
  libbitcoin_cli.a \
  libbitcoin_common.a \
  $(LIBLEVELDB) \
  $(LIBMEMENV)
if ENABLE_WALLET
envycoind_LDADD += libbitcoin_wallet.a libbitcoin_server_wallet.a
endif
envycoind_SOURCES = envycoind.cpp
#

if TARGET_WINDOWS
envycoind_SOURCES += envycoind-res.rc
endif

AM_CPPFLAGS += $(BDB_CPPFLAGS)
envycoind_LDADD += $(BOOST_LIBS) $(BDB_LIBS)

# envycoin-cli binary #
envycoin_cli_LDADD = \
  libbitcoin_cli.a \
  libbitcoin_common.a \
  $(BOOST_LIBS)
envycoin_cli_SOURCES = envycoin-cli.cpp
#

if TARGET_WINDOWS
envycoin_cli_SOURCES += envycoin-cli-res.rc
endif

# NOTE: This dependency is not strictly necessary, but without it make may try to build both in parallel, which breaks the LevelDB build system in a race
leveldb/libleveldb.a: leveldb/libmemenv.a

leveldb/%.a:
	@echo "Building LevelDB ..." && $(MAKE) -C $(@D) $(@F) CXX="$(CXX)" \
	  CC="$(CC)" PLATFORM=$(TARGET_OS) AR="$(AR)" $(LEVELDB_TARGET_FLAGS) \
	  OPT="$(CXXFLAGS) $(CPPFLAGS)"

qt/bitcoinstrings.cpp: $(libbitcoin_server_a_SOURCES) $(libbitcoin_common_a_SOURCES) $(libbitcoin_cli_a_SOURCES)
	@test -n $(XGETTEXT) || echo "xgettext is required for updating translations"
	@cd $(top_srcdir); XGETTEXT=$(XGETTEXT) share/qt/extract_strings_qt.py

CLEANFILES = leveldb/libleveldb.a leveldb/libmemenv.a *.gcda *.gcno

DISTCLEANFILES = obj/build.h

EXTRA_DIST = leveldb Makefile.include

clean-local:
	-$(MAKE) -C leveldb clean
	rm -f leveldb/*/*.gcno leveldb/helpers/memenv/*.gcno
