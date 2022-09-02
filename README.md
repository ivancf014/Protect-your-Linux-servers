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
Este ataque consiste, como su nombre indica, en envenenar las tablas de cache ARP de las máquinas víctimas. Envenenando la caché ARP es posible conseguir un entorno MITM.

* Protección contra ARP Poisoning
Queda comprobado que un ataque MITM aprovechando la funcionalidad ARP es muy peligroso si se lleva a cabo de forma transparente consiguiendo que el usuario no sospeche que está siendo atacado.

* Entradas ARP estáticas
La más obvia de ellas es la utilización de entradas ARP estáticas en las máquinas cliente para que estas no puedan ser atacadas con éxito. Se trata de un método muy simple y fácil de llevar a cabo solo si se está en un entorno pequeño.

* Monitorización de ARP
Como se comentaba con anterioridad, no siempre resulta posible o viable mantener entradas estáticas ARP en las máquinas de un entorno. Si fuese posible, sin duda se estaría evitando el ataque pero el administrador de la red puede que no supiera que está habiendo intentos de ataques ARP. Es por ello que existen aplicaciones que se ejecutan como demonios en las máquinas de una red que detectan si se está sufriendo un ataque ARP Poisoning, evitándolo y notificándolo al administrador de la red.

* Utilización del fichero /etc/hosts
Si las entradas ARP estáticas resultaban difíciles de mantener, es posible que establecer una equivalencia IP - Nombre sea aún más complicado.

* DHCP Spoofing
Este ataque consiste en implementar un servidor DHCP alternativo con la finalidad de asignar direcciones IP a aquellas máquinas que las adquieran de forma automática.
A RELLENAR

* ICMP Redirect
A RELLENAR

## Protección de la capa de aplicación

### Jaulas con chroot
Si una aplicación, PDF u otro archivo está infectado puede traer consecuencias graves. Para ello podríamos usar una máquina virtual o Sandbox.
Como su nombre hace pensar, con chroot se modifica la raíz del sistema para un determinado proceso, haciéndole creer que realmente esa es la raíz de ficheros del
sistema. Esto supone que el proceso ejecutado dentro de una jaula chroot “verá” solo lo que se quiera que vea. Inicialmente una jaula es una carcasa totalmente vacía, sin contenido alguno y será necesario poner en ella los componentes justos y necesarios para permitir la ejecución de una aplicación. Antes de pasar a un ejemplo de chroot es necesario conocer algunas particularidades y recomendaciones para su uso:

* Nunca utilizar chroot para un proceso ejecutado como root. No tiene ningún sentido hacerlo así pues el usuario root siempre podrá salir de la jaula al sistema de ficheros real.
* Incluir en la jaula los componentes mínimos necesarios para la ejecución de un proceso. En el ejemplo se verá cómo conocer dichos componentes y cómo agregarlos a la jaula.
* Mantener los permisos de los ficheros lo más restrictivos posibles para no conceder a un potencial atacante ni el mínimo ápice de oportunidad para modificar ficheros a su antojo, ejecutables, etc.
* Nunca utilizar una jaula chroot como único método de seguridad implementado. No servirá de nada en absoluto.

### Limitación de recursos



## Escalada de privilegios


