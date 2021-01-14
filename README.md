# PracticesPacketTracer
Practices carried out in Packet Tracer. Configuration of Routers, ACL and others.
 ## ACL
 En el archivo **Ejercicio 1 planificación 1** se realiza la configuración de **SERVICIOS DHCP, DNS, HTTP, HTTPS, FTP, TFTP SERVIDOR DE CORREO** además de configurar _ACLs_

![Topología de red base para aplicar ACLs][img1]

Antes de poder configurar cualquier ACL se debe estar dentro de la configuraciones de administrador

        enable
        configure terminal
 ### ACL estándar
- Bloquear el tráfico del pc0 a la red 192.168.187.32

Ir al Router B
        
        access-list 1 deny host 192.168.187.13
        access-list 1 permit any

        interface g 0/0/0
        ip access-group 1 out

- Bloquear el tráfico de la red 192.168.187.32 hacia la red 192.168.187.64

Ir al Router C

        access-list 2 deny 192.168.187.32 0.0.0.31
        access-list 2 permit any

        interface g 0/0/0
        ip access-group 2 out
- Permitir que sólo la red 192.168.187.128 se comunique con la red 192.168.187.96

Ir al Router D

        access-list 3 permit 192.168.187.128 0.0.0.31
        access-list 3 deny any

        interface g 0/0/0
        ip access-group 3 out
- Permitir el acceso PC0(E) a la vty del router A

Ir al Router A

        access-list 4 permit host 192.168.187.130
        access-list 4 deny any

        interface g 0/0/0
        ip access-group 4 in
### ACL extendida
- Bloquear el tráfico de todas las redes hacia la pc2(B)

Ir al Router B

        access-list 100 deny ip any host 192.168.187.36
        access-list 100 permit ip any any

        
- Bloquear el tráfico https sólo entre la red 192.168.187.64 y el WEB SERVER

        access-list 101
- Bloquear el tráfico ICMP de todas las redes al Server MAIL DNS DHCP.

        access-list 102
- Permitir que el tráfico http del WEB SERVER sólo se pueda acceder desde la PC2(E)

        access-list 103
- Permitir que sólo PC1(E) pueda acceder a las vty del router A.

        access-list 104

### ACL nombrada
Permiten que las ACL extendidas y estándar
tengan nombres en lugar de números.

Tienen la capacidad de modificar las ACL sin tener que eliminarlas y luego reconfigurarlas.
- Realizar los ejercicios ACL estándar y extendida, utilizando ACL nombradas

### Importante
<p style=”text-align: justify;”>Las listas de acceso extendidas deben
colocarse normalmente(en lo posible) lo más cerca posible al del origen de tráfico que será negado, mientras que las estándar, lo más cerca posible al destino.</p>

### Restringir el acceso a las VTY

[img1]: https://github.com/AniiEncalada/PracticesPacketTracer/blob/main/Topolog%C3%ADa.png "Topología de red para ACLs"