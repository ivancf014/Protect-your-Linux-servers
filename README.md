# Protect-your-Linux-servers
With this guide you can keep your Linux servers safe

## Seguridad física
Existen muchas herramientas para saltarse la seguridad de tus servidores de forma física. Un Pendrive, un cable OMG, un CD etc. Asi que no tengas tus servidores al alcance de cualquiera.

### BIOS/UEFI
* Edición de opciones de protegida por contraseña.
* Deshabilitar la selección de medio de arranque.
* Deshabilitar, si es posible, el arranque por USB y tarjetas de red, así si el atacante tiene acceso a los periféricos se encontrará una barrera extra.

### GRUB
Desde el GRUB se puede obtener acceso a root fácilmente, por lo que tenemos que añadir una contraseña maestra al GRUB. Esta contraseña estará cifrada en MD5 o si es posible pbkdf2. Otra recomendación sería cifrar los discos por si el atacante apaga los servidores y se lleva los discos.

### Buenas prácticas
* Variable de entorno TMOUT
Por defecto en las distribuciones que usan bash existe una varible llamada TMOUT que está deshabilitada inicialmente. Su contenido consiste en cerrar una sesión inactiva en el tiempo.

* Evitar el reinicio y apagado accidental 
(chmod a-x /etc/acpi/powerbtn-acpi-support.sh)

## Protección perimetral

### Iptables
Iptables es una aplicación que permite el gestión, configuración y el manejo de filtrado de paquetes.

### VPN
A RELLENAR

### Monitorización a nivel de la red
A RELLENAR

## Protección de la red interna

### Spoofing o suplantación de identidad
En muchos casos se confía en que los usuarios van a realizar un uso correcto de la misma. Los ataques más comunes son MITM o DDos pero existen más tipos.
* ARP Poisoning




