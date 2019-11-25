INCLUDE(CMakeForceCompiler)

# CROSS COMPILER SETTING
SET(CMAKE_SYSTEM_NAME Generic)
CMAKE_MINIMUM_REQUIRED (VERSION 2.6)

include_directories(system)
include_directories(system/OS) 
include_directories(system/arch) 
include_directories(src)
include_directories(src/include)
include_directories(src/include/lwip)
include_directories(src/include/lwip/prot)
include_directories(src/include/lwip/priv)
include_directories(src/include/netif)
include_directories(src/include/netif/ppp)
include_directories(src/include/posix)
include_directories(src/include/posix/sys)
include_directories(src/netif)
include_directories(src/netif/ppp)
include_directories(port)

SET(LWIP_SOURCE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/src)
SET(LWIP_SYSTEM_DIR ${CMAKE_CURRENT_SOURCE_DIR}/system)
SET(LWIP_PORT_DIR ${CMAKE_CURRENT_SOURCE_DIR}/port)

add_definitions(-DLWIP_NETIF_LOOPBACK=1)
add_definitions(-DSO_REUSE=1)
add_definitions(-DLWIP_SOCKET=1)
add_definitions(-DLWIP_NETCONN=1)

SET(LWIP_SRCS
        ${LWIP_SOURCE_DIR}/api/api_lib.c
        ${LWIP_SOURCE_DIR}/api/api_msg.c
        ${LWIP_SOURCE_DIR}/api/err.c
        ${LWIP_SOURCE_DIR}/api/netbuf.c
        ${LWIP_SOURCE_DIR}/api/netdb.c
        ${LWIP_SOURCE_DIR}/api/netifapi.c
        ${LWIP_SOURCE_DIR}/api/sockets.c
        ${LWIP_SOURCE_DIR}/api/tcpip.c
        ${LWIP_SOURCE_DIR}/include/lwip/api.h
        ${LWIP_SOURCE_DIR}/include/lwip/arch.h
        ${LWIP_SOURCE_DIR}/include/lwip/debug.h
        ${LWIP_SOURCE_DIR}/include/lwip/def.h
        ${LWIP_SOURCE_DIR}/include/lwip/dhcp.h
        ${LWIP_SOURCE_DIR}/include/lwip/dns.h
        ${LWIP_SOURCE_DIR}/include/lwip/err.h
        ${LWIP_SOURCE_DIR}/include/lwip/init.h
        ${LWIP_SOURCE_DIR}/include/lwip/mem.h
        ${LWIP_SOURCE_DIR}/include/lwip/memp.h
        ${LWIP_SOURCE_DIR}/include/lwip/netdb.h
        ${LWIP_SOURCE_DIR}/include/lwip/netif.h
        ${LWIP_SOURCE_DIR}/include/lwip/netifapi.h
        ${LWIP_SOURCE_DIR}/include/lwip/opt.h
        ${LWIP_SOURCE_DIR}/include/lwip/pbuf.h
        ${LWIP_SOURCE_DIR}/include/lwip/raw.h
        ${LWIP_SOURCE_DIR}/include/lwip/sio.h
        ${LWIP_SOURCE_DIR}/include/lwip/snmp.h
        ${LWIP_SOURCE_DIR}/include/lwip/sockets.h
        ${LWIP_SOURCE_DIR}/include/lwip/stats.h
        ${LWIP_SOURCE_DIR}/include/lwip/sys.h
        ${LWIP_SOURCE_DIR}/include/lwip/tcp.h
        ${LWIP_SOURCE_DIR}/include/lwip/tcpip.h
        ${LWIP_SOURCE_DIR}/include/lwip/udp.h
        ${LWIP_SOURCE_DIR}/include/netif/etharp.h
        ${LWIP_SOURCE_DIR}/include/netif/slipif.h
        ${LWIP_SOURCE_DIR}/include/posix/netdb.h
        ${LWIP_SOURCE_DIR}/include/posix/sys/socket.h
        ${LWIP_SOURCE_DIR}/core/def.c
        ${LWIP_SOURCE_DIR}/core/dns.c
        ${LWIP_SOURCE_DIR}/core/inet_chksum.c
        ${LWIP_SOURCE_DIR}/core/init.c
        ${LWIP_SOURCE_DIR}/core/ip.c
        ${LWIP_SOURCE_DIR}/core/mem.c
        ${LWIP_SOURCE_DIR}/core/memp.c
        ${LWIP_SOURCE_DIR}/core/netif.c
        ${LWIP_SOURCE_DIR}/core/pbuf.c
        ${LWIP_SOURCE_DIR}/core/raw.c
        ${LWIP_SOURCE_DIR}/core/stats.c
        ${LWIP_SOURCE_DIR}/core/sys.c
        ${LWIP_SOURCE_DIR}/core/tcp.c
        ${LWIP_SOURCE_DIR}/core/tcp_in.c
        ${LWIP_SOURCE_DIR}/core/tcp_out.c
        ${LWIP_SOURCE_DIR}/core/timeouts.c
        ${LWIP_SOURCE_DIR}/core/udp.c
        ${LWIP_SOURCE_DIR}/core/ipv4/autoip.c
        ${LWIP_SOURCE_DIR}/core/ipv4/dhcp.c
        ${LWIP_SOURCE_DIR}/core/ipv4/etharp.c
        ${LWIP_SOURCE_DIR}/core/ipv4/icmp.c
        ${LWIP_SOURCE_DIR}/core/ipv4/igmp.c
        ${LWIP_SOURCE_DIR}/core/ipv4/ip4.c
        ${LWIP_SOURCE_DIR}/core/ipv4/ip4_addr.c
        ${LWIP_SOURCE_DIR}/core/ipv4/ip4_frag.c
        ${LWIP_SOURCE_DIR}/netif/ethernet.c
        ${LWIP_SOURCE_DIR}/netif/slipif.c
        ${LWIP_SOURCE_DIR}/netif/lowpan6.c
        ${LWIP_SOURCE_DIR}/netif/ppp/auth.c
        ${LWIP_SOURCE_DIR}/netif/ppp/ccp.c
        ${LWIP_SOURCE_DIR}/netif/ppp/chap_ms.c
        ${LWIP_SOURCE_DIR}/netif/ppp/chap-md5.c
        ${LWIP_SOURCE_DIR}/netif/ppp/chap-new.c
        ${LWIP_SOURCE_DIR}/netif/ppp/demand.c
        ${LWIP_SOURCE_DIR}/netif/ppp/eap.c
        ${LWIP_SOURCE_DIR}/netif/ppp/ecp.c
        ${LWIP_SOURCE_DIR}/netif/ppp/eui64.c
        ${LWIP_SOURCE_DIR}/netif/ppp/fsm.c
        ${LWIP_SOURCE_DIR}/netif/ppp/ipcp.c
        ${LWIP_SOURCE_DIR}/netif/ppp/ipv6cp.c
        ${LWIP_SOURCE_DIR}/netif/ppp/lcp.c
        ${LWIP_SOURCE_DIR}/netif/ppp/magic.c
        ${LWIP_SOURCE_DIR}/netif/ppp/mppe.c
        ${LWIP_SOURCE_DIR}/netif/ppp/multilink.c
        ${LWIP_SOURCE_DIR}/netif/ppp/ppp.c
        ${LWIP_SOURCE_DIR}/netif/ppp/pppapi.c
        ${LWIP_SOURCE_DIR}/netif/ppp/pppcrypt.c
        ${LWIP_SOURCE_DIR}/netif/ppp/pppoe.c
        ${LWIP_SOURCE_DIR}/netif/ppp/pppol2tp.c
        ${LWIP_SOURCE_DIR}/netif/ppp/pppos.c
        ${LWIP_SOURCE_DIR}/netif/ppp/upap.c
        ${LWIP_SOURCE_DIR}/netif/ppp/utils.c
        ${LWIP_SOURCE_DIR}/netif/ppp/vj.c
        ${LWIP_SYSTEM_DIR}/OS/sys_arch.c
        ${LWIP_PORT_DIR}/ethernetif.c
)

add_library(LwIP_2.0.3 STATIC ${LWIP_SRCS})
