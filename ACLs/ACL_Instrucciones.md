# ACLs
Practica de ACLs
## ACL Estándar
Realizar las siguientes actividades

- Realizar la configuración de los Routers y la red acorde a los requerimientos indicados en la tabla 1.
Para empezar a configurar es necesario ejecutar dentro del **CLI del Router**:

        enable
        configure terminal
Nombre del Host

        hostname nombre
Clave del administrador

        enable password mat
Clave de consola

        line con 0 
        password consola
        exit
Clave vty

        line vty 0 4
        password mat
        exit
Configurar interfaces

1. Debe acceder a la interfaz a configurar

        interface ax/x/x
2. Para agragar la dirección IP debe usar el comando _ip address_ seguido de la **Dirección IP** y **máscara de red**

        ip address 0.0.0.0 0.0.0.0
Por tanto:

        interface g0/0/0
        ip address 172.16.0.0 255.255.254.0
        exit
        interface g0/0/1
        ip address ip address 10.10.10.0 255.255.255.0
        exit

- Configurar los enlaces seriales; las respectivas direcciones se encuentran en la topología.

Secuencia de pasos para configurar seriales

        router(config)# interface serial <slot/puerto>
        router(config-if)# ip address <dirección_IP> <máscara>
        router(config-if)# clock rate <ratio>
        router(config-if)# no shutdown
        router(config-if)# exit
        router(config)# exit
Aplicandolo

        interface serial 
- Aplicar el Protocolo RIP para enrutamiento.
- ACL Estándar:
    - Bloquear el tráfico del pc0 a la red 192.16.5.0
    - Bloquear el tráfico de la red 172.16.4.0 hacia la red 10.10.10.0
    - Permitir que sólo la red 10.10.11.0 se comunique con la red 172.16.2.0
    - Permitir el acceso 172.16.3.32 a la vty del router cuenca
## ACL Extendida
- Bloquear el tráfico de todas las redes hacia la PCMACHALA02(10.10.11.3).
- Bloquear el tráfico ICMP de todas las redes al Server Mail – DNS (172.16.0.3).
- Permitir que el tráfico http del WEB SERVER FTP (172.16.0.4) sólo se pueda acceder desde
la PCG01(172.16.2.3)
- Bloquear el tráfico http sólo entre la red 172.16.4.0 y el WEB SERVER FTP
## ACL Nombradas Estandar
- Bloquear el tráfico del PC3_WS_Cuenca(172.16.0.5) a la red 192.16.5.0 -(nombre de ACL: BT_PC3C_A_RZAMORA)
- Bloquear el tráfico de la red 172.16.4.0 hacia la red 10.10.10.0 - (nombre de ACL: BT_RLOJA_A_SRCUENCA)
- Permitir que sólo la red 10.10.11.0 se comunique con la red 172.16.2.0 - (nombre ACL: PT_ENTRE_RMACHALA_Y_RGUAYAQUIL)
- Permitir el acceso 172.16.3.32 a la vty del router CUENCA - (nombre ACL: PA_ENTRE_SRQUITO32_Y_VTYCUENCA)
## ACL Nombradas Extendidas
- Bloquear el tráfico de todas las redes hacia PC_WS_Machala(10.10.11.3)- (nombre ACL: BT_TODASREDES_A_PCWSMACHALA)
- Bloquear el tráfico ICMP de todas las redes al Server Mail – DNS (172.16.0.3) - (nombre ACL: BT_ICMPTODASRES_ASMAILDNS)
- Permitir que el tráfico http del WEB SERVER FTP (172.16.0.4) sólo se pueda acceder desde la PC1_WS_Guayaquil (172.16.2.3) (nombre ACL: PT_HTTPWSFTP_DESDE_PCG01)
- Bloquear el tráfico http sólo entre la rede 172.16.4.0 y el WEB SERVER FTP- (nombre ACL: BT_ENTRE_RLOJA_Y_WSFTP)