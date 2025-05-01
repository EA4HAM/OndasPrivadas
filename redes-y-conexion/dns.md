# Sistema de nombres de dominio (DNS)

Utilizamos [Internet](https://es.wikipedia.org/wiki/Internet) a diario, pero pocas veces pensamos en el mecanismo oculto que convierte los nombres de los [sitios web](https://es.wikipedia.org/wiki/Sitio_web) (como `example.com`) en [direcciones numéricas](https://es.wikipedia.org/wiki/Dirección_IP) comprensibles para los [ordenadores](https://es.wikipedia.org/wiki/Computadora). El [sistema de nombres de dominio (DNS, por sus siglas en inglés)](https://es.wikipedia.org/wiki/Sistema_de_nombres_de_dominio) funciona, esencialmente, como la guía telefónica de [Internet](https://es.wikipedia.org/wiki/Internet): introducimos un [nombre fácil de recordar](https://es.wikipedia.org/wiki/Dominio_de_internet) y el [DNS](https://es.wikipedia.org/wiki/Sistema_de_nombres_de_dominio) lo traduce en una [dirección IP](https://es.wikipedia.org/wiki/Dirección_IP) (por ejemplo, `192.168.1.1`) para que nuestro [navegador](https://es.wikipedia.org/wiki/Navegador_web) encuentre el [servidor](https://es.wikipedia.org/wiki/Servidor) correspondiente. Este proceso ocurre de forma automática y constante cada vez que accedemos a una [página web](https://es.wikipedia.org/wiki/Sitio_web) o un [servicio en línea](https://es.wikipedia.org/wiki/Servicio_web).

Por defecto, las consultas [DNS](https://es.wikipedia.org/wiki/Sistema_de_nombres_de_dominio) no están [cifradas](https://es.wikipedia.org/wiki/Cifrado_(criptografía)). Esto significa que cualquier [servidor](https://es.wikipedia.org/wiki/Servidor) intermedio por donde pase nuestra consulta puede ver qué [dominios](https://es.wikipedia.org/wiki/Dominio_de_internet) estamos visitando. Es como si las [direcciones web](https://es.wikipedia.org/wiki/Localizador_de_recursos_uniforme) estuvieran impresas de cada uno de nuestros [paquetes de datos](https://es.wikipedia.org/wiki/Paquete_de_red): cualquier entidad que intercepte el tráfico podría leerlas. Para nuestra [privacidad](https://es.wikipedia.org/wiki/Privacidad), esto es un riesgo porque expone nuestros hábitos de navegación a terceros.

Afortunadamente, disponemos de diversas estrategias para proteger la [confidencialidad](https://es.wikipedia.org/wiki/Confidencialidad) de nuestras consultas [DNS](https://es.wikipedia.org/wiki/Sistema_de_nombres_de_dominio). Podemos recurrir a [servidores](https://es.wikipedia.org/wiki/Servidor) públicos que prometen no registrar nuestra actividad, o bien optar por [autoalojar](https://es.wikipedia.org/wiki/Autoalojamiento_(servicios_web)) nuestro propio [servidor](https://es.wikipedia.org/wiki/Servidor) (lo cual confiere control total). También existen [servicios en línea](https://es.wikipedia.org/wiki/Servicio_web) que ofrecen [DNS](https://es.wikipedia.org/wiki/Sistema_de_nombres_de_dominio) en la [nube](https://es.wikipedia.org/wiki/Computación_en_la_nube) con [cifrado](https://es.wikipedia.org/wiki/Cifrado_(criptografía)) y filtros avanzados sin necesidad de adquirir [hardware](https://es.wikipedia.org/wiki/Hardware). A continuación, abordamos cada una de estas alternativas con detalle.

## Servidores DNS públicos

Entre las soluciones más accesibles para reforzar nuestra [privacidad](https://es.wikipedia.org/wiki/Privacidad) en el uso del [DNS](https://es.wikipedia.org/wiki/Sistema_de_nombres_de_dominio), se encuentran los [servidores](https://es.wikipedia.org/wiki/Servidor) públicos ofrecidos por terceros. Estos [servicios](https://es.wikipedia.org/wiki/Servicio_web), generalmente gratuitos, son mantenidos por empresas u organizaciones que se encargan de resolver [nombres de dominios](https://es.wikipedia.org/wiki/Dominio_de_internet) en nuestro lugar. Podemos configurar las [direcciones](https://es.wikipedia.org/wiki/Dirección_IP) correspondientes en nuestro [router](https://es.wikipedia.org/wiki/Rúter) o directamente en nuestros dispositivos, reemplazando así los [DNS](https://es.wikipedia.org/wiki/Sistema_de_nombres_de_dominio) asignados por nuestro [proveedor de servicios de Internet](https://es.wikipedia.org/wiki/Proveedor_de_servicios_de_internet). Esta sustitución nos brinda beneficios como mayor velocidad, seguridad y, en algunos casos, filtrado de contenidos.

En particular, el [DNS](https://es.wikipedia.org/wiki/Sistema_de_nombres_de_dominio) público de [Google](https://www.google.com/?hl=es) ha ganado popularidad por su rapidez y disponibilidad. Sin embargo, debemos considerar que los datos recogidos a través de este servicio se emplean con fines comerciales, como la mejora de productos y la personalización de publicidad. Aunque [Google](https://www.google.com/?hl=es) declara que no vende estos datos a terceros, el hecho de que conserve registros de nuestras consultas facilita el rastreo de nuestros hábitos en línea.

Por esta razón, recomendamos emplear [servidores](https://es.wikipedia.org/wiki/Servidor) [DNS](https://es.wikipedia.org/wiki/Sistema_de_nombres_de_dominio) que antepongan la [privacidad](https://es.wikipedia.org/wiki/Privacidad) del usuario. Una excelente fuente de opciones confiables es el [sitio web](https://es.wikipedia.org/wiki/Sitio_web) de [Privacy Guides](https://www.privacyguides.org/es/dns/?h=dns#proveedores-recomendados). Entre los destacados se encuentra [Quad9](https://quad9.net/es), un proveedor suizo con una sólida política de [privacidad](https://es.wikipedia.org/wiki/Privacidad). [Suiza](https://www.aboutswitzerland.eda.admin.ch/es), al contar con una legislación especialmente estricta en esta materia, ofrece un entorno legal muy favorable para proteger nuestros datos. Además, [Quad9](https://quad9.net/es) incorpora filtros que bloquean [sitios web](https://es.wikipedia.org/wiki/Sitio_web) maliciosos y rastreadores de forma predeterminada.

Al seleccionar un [servidor](https://es.wikipedia.org/wiki/Servidor) [DNS](https://es.wikipedia.org/wiki/Sistema_de_nombres_de_dominio), conviene priorizar aquellos que:

* Soporten resolución tanto en texto claro como cifrada ([DoH (DNS sobre HTTPS)](https://es.wikipedia.org/wiki/DNS_mediante_HTTPS) o [DoT (DNS sobre TLS)](https://es.wikipedia.org/wiki/DNS_mediante_TLS)),

* No registren [logs](https://es.wikipedia.org/wiki/Log_(informática)) identificables, o bien los almacenen de manera anonimizada,

* No utilicen [ECS (subred de cliente EDNS)](https://en.wikipedia.org/wiki/EDNS_Client_Subnet), o lo hagan de forma segura y no invasiva,

* Implementen filtros de protección contra [malware](https://es.wikipedia.org/wiki/Malware), anuncios y rastreadores.

En nuestra propia red doméstica, hemos optado por utilizar los [servidores gratuitos de Control D](https://controld.com/free-dns), diseñados para un entorno familiar. Estos [servidores](https://es.wikipedia.org/wiki/Servidor) bloquean eficazmente [malware](https://es.wikipedia.org/wiki/Malware), anuncios, rastreadores y contenidos no deseados como material para adultos o relacionado con drogas.

Las [direcciones](https://es.wikipedia.org/wiki/Dirección_IP) a introducir dependerán de las capacidades de nuestro [router](https://es.wikipedia.org/wiki/Rúter):

* Para aquellos que solo admiten resolución en texto claro:
   | IPv4 | IPv6 |
   | --- | --- |
   | `76.76.2.4` | `2606:1a40::4` |
   | `76.76.10.4` | `2606:1a40:1::4` |

* Para [routers](https://es.wikipedia.org/wiki/Rúter) que soportan [DoH (DNS sobre HTTPS)](https://es.wikipedia.org/wiki/DNS_mediante_HTTPS):
   ```
   https://freedns.controld.com/family
   ```

* Para [routers](https://es.wikipedia.org/wiki/Rúter) que soportan [DoT (DNS mediante TLS)](https://es.wikipedia.org/wiki/DNS_mediante_TLS):
   ```
   family.freedns.controld.com
   ```
  
Dada la variedad de modelos de dispositivos [red](https://es.wikipedia.org/wiki/Red_de_computadoras) disponibles en el mercado, no resulta viable ofrecer una guía genérica de configuración. Recomendamos, por tanto, consultar la documentación específica de nuestro [router](https://es.wikipedia.org/wiki/Rúter) o contactar con el soporte técnico del fabricante.

## Servidor DNS autoalojado

Para quienes desean control absoluto sobre nuestras consultas, la opción más robusta consiste en [autoalojar](https://es.wikipedia.org/wiki/Autoalojamiento_(servicios_web)) nuestro propio [servidor](https://es.wikipedia.org/wiki/Servidor) [DNS](https://es.wikipedia.org/wiki/Sistema_de_nombres_de_dominio). En esta modalidad, todas las peticiones de [nombres de dominios](https://es.wikipedia.org/wiki/Dominio_de_internet) generadas en nuestra red local se dirigen primero a un sistema bajo nuestro control. Así, eliminamos cualquier dependencia de terceros en la resolución de [direcciones](https://es.wikipedia.org/wiki/Localizador_de_recursos_uniforme) y reforzamos nuestra [privacidad](https://es.wikipedia.org/wiki/Privacidad) desde la base.

Una arquitectura efectiva para ello combina tres componentes de software libre: [Proxmox](https://proxmox.com/en/) como plataforma de [virtualización](https://es.wikipedia.org/wiki/Virtualización), [Alpine Linux](https://www.alpinelinux.org) como [sistema operativo](https://es.wikipedia.org/wiki/Sistema_operativo) ligero y seguro, y [AdGuard Home](https://github.com/AdguardTeam/AdGuardHome) como solución de filtrado y resolución [DNS](https://es.wikipedia.org/wiki/Sistema_de_nombres_de_dominio).

### Descarga del sistema operativo

En primer lugar, accedemos al [sitio web oficial de Alpine Linux](https://www.alpinelinux.org) y localizamos la sección de descarga de [imágenes ISO](https://es.wikipedia.org/wiki/Imagen_ISO). Seleccionamos la versión *VIRTUAL*, optimizada para entornos [virtualizados](https://es.wikipedia.org/wiki/Virtualización), que cuenta con un [núcleo](https://es.wikipedia.org/wiki/Núcleo_(informática)) más reducido en comparación con la versión estándar.

Hacemos clic derecho sobre el enlace correspondiente a la [arquitectura x86_64](https://es.wikipedia.org/wiki/X86-64) - la habitual en la mayoría de [servidores](https://es.wikipedia.org/wiki/Servidor) y [ordenadores](https://es.wikipedia.org/wiki/Computadora) - y copiamos su [dirección](https://es.wikipedia.org/wiki/Localizador_de_recursos_uniforme).

A continuación, accedemos a nuestra interfaz de [Proxmox](https://proxmox.com/en/), seleccionamos el almacenamiento *local* (u otro que permita albergar [imágenes ISO](https://es.wikipedia.org/wiki/Imagen_ISO)) y pulsamos el botón *Download from URL*. Pegamos la [dirección](https://es.wikipedia.org/wiki/Localizador_de_recursos_uniforme) copiada en el campo *URL* y hacemos clic en *Query URL*.

Una vez comprobado el enlace, se mostrará el nombre del archivo junto con su tamaño. Activamos la opción *Advanced*, y en *Hash algorithm* elegimos *SHA-256*, que es el algoritmo utilizado actualmente - a fecha del primero de mayo de 2025 - para verificar la integridad del archivo. Pegamos el valor de [hash](https://es.wikipedia.org/wiki/Función_hash) obtenido desde el [sitio oficial](https://www.alpinelinux.org) en el campo *Checksum*.

La verificación del [hash](https://es.wikipedia.org/wiki/Función_hash) presenta múltiples beneficios:

1. **Integridad**: confirmamos que el archivo no se haya corrompido durante la descarga.

2. **Autenticidad**: nos aseguramos de que la fuente sea legítima y no haya sido alterada maliciosamente.

3. **Prevención contra malware**: evitamos ejecutar archivos que pudieran haber sido modificados con fines maliciosos.

4. **Estabilidad de la instalación**: reducimos el riesgo de errores o fallos imprevistos.

Una vez cumplimentados los campos, pulsamos *Download* y aguardamos a que finalice el proceso.

### Creación de la máquina virtual

Dentro de [Proxmox](https://proxmox.com/en/), pulsamos el botón *Create VM* para iniciar la creación de una nueva [máquina virtual](https://es.wikipedia.org/wiki/Máquina_virtual).

* En la pestaña *General*, activamos *Advanced*, elegimos el *Node* correspondiente (en caso de contar con un [clúster](https://es.wikipedia.org/wiki/Clúster_de_computadoras)) y asignamos un nombre a la [máquina](https://es.wikipedia.org/wiki/Máquina_virtual). Habilitamos *Start at boot* para que la [máquina](https://es.wikipedia.org/wiki/Máquina_virtual) se inicie automáticamente junto con el sistema anfitrión.

* En *OS*, seleccionamos *Use CD/DVD disc image file*, escogemos la [ISO](https://es.wikipedia.org/wiki/Imagen_ISO) descargada, establecemos el tipo de *Linux* y la versión en *6.x - 2.6 Kernel*.

* En *System*, configuramos *Graphic card* como *Standard VGA*, *Machine* como *Default (i440fx)*, *BIOS* en *SeaBIOS*, y *SCSI Controller* en *VirtIO SCSI single*. Habilitamos *Qemu Agent*.

* En *Disks*, seleccionamos *SCSI* y un tamaño de 2 GiB. En *Cache*, optamos por *Write through*, lo cual garantiza que los datos se escriban directamente en el almacenamiento físico, incrementando la seguridad frente a pérdida de energía. Activamos *SSD emulation* si nuestro medio de almacenamiento es un [SSD](https://es.wikipedia.org/wiki/Unidad_de_estado_sólido) o [NVMe](https://es.wikipedia.org/wiki/NVM_Express), y en *Async IO*, seleccionamos *io_uring* por su eficiencia.

* En *CPU*, asignamos 1 socket y 1 core, eligiendo *x86-64-v3* si nuestro procesador lo soporta, o bien *x86-64-v2-AES* si no es el caso.

* En la *Memory*, reservamos 512 MiB y desactivamos la opción *Ballooning Device*.

* En *Network*, seleccionamos el puente *vmbr0* y el modelo *VirtIO (paravirtualized)*. Dejamos las demás opciones en blanco o desactivadas.

Tras repasar todas las opciones, pulsamos *Finish* para crear la [máquina virtual](https://es.wikipedia.org/wiki/Máquina_virtual).

### Instalación del sistema operativo

Una vez creada la [máquina virtual](https://es.wikipedia.org/wiki/Máquina_virtual), procedemos a instalar el [sistema operativo](https://es.wikipedia.org/wiki/Sistema_operativo) [Alpine Linux](https://www.alpinelinux.org), una [distribución](https://es.wikipedia.org/wiki/Distribución_Linux) ligera y segura.

Seleccionamos la [máquina](https://es.wikipedia.org/wiki/Máquina_virtual) recién creada en el panel izquierdo de [Proxmox](https://proxmox.com/en/), pulsamos el botón *Start* y, acto seguido, hacemos clic en *>_ Console*.  Esto abrirá una nueva pestaña de nuestro [navegador web](https://es.wikipedia.org/wiki/Navegador_web), desde la cual podremos interactuar con la consola de la [máquina virtual](https://es.wikipedia.org/wiki/Máquina_virtual).

Al arrancar desde la [imagen ISO](https://es.wikipedia.org/wiki/Imagen_ISO), se nos solicitará un nombre de usuario. Introducimos *root* y accedemos directamente, sin necesidad de contraseña.

A continuación, iniciamos el asistente de instalación ejecutando el siguiente comando:

```shell
localhost:~# setup-alpine
```

El proceso se compone de varias etapas que detallamos a continuación.

#### 1. Configuración del teclado

Cuando se nos presente la lista de [distribuciones de teclado](https://es.wikipedia.org/wiki/Distribución_del_teclado), seleccionamos *es* y luego *es-deadtilde*, una variante común del teclado español:

```shell
 ALPINE LINUX INSTALL
----------------------

 Keymap
--------

af  al  am  ara  at  az  ba  bd  be  bg  br  brai  by  ca  ch  cm  cn  cz  de  dk  dz  ee     epo  es  fi  fo
fr  gb  ge  gh   gr  hr  hu  id  ie  il  in  iq    ir  is  it  jp  ke  kg  kr  kz  la  latam  lk   lt  lv  ma
md  me  mk  ml   mm  mt  my  ng  nl  no  nz  ph    pk  pl  pt  ro  rs  ru  se  si  sk  sy     th   tj  rm  tr
tw  ua  us  uz   vn

Select keyboard layout: [none] es

es-ast	es-cat	es-deadtilde	es-dvorak	es-nodeadkeys	es-winkeys	es

Select variant (or ‘abort’): es-deadtilde

 * Caching service dependencies ...
 * Setting keymap ... 
```

#### 2. Nombre del equipo (hostname)

Asignamos un [nombre identificativo](https://es.wikipedia.org/wiki/Hostname) a nuestro sistema:

```shell
 Hostname
----------
Enter system hostname (fully qualified form, e.g. 'foo.example.org') [localhost] dns1
```

#### 3. Configuración de red

Especificamos los parámetros de [red](https://es.wikipedia.org/wiki/Red_de_computadoras):  la interfaz de red, la [dirección IP](https://es.wikipedia.org/wiki/Dirección_IP) estática deseada, la [máscara de red](https://es.wikipedia.org/wiki/Máscara_de_red), la [puerta de enlace](https://es.wikipedia.org/wiki/Puerta_de_enlace) y el [servidor](https://es.wikipedia.org/wiki/Servidor) [DNS](https://es.wikipedia.org/wiki/Sistema_de_nombres_de_dominio). Por ejemplo:

```shell
 Interface
-----------
Available interfaces are: eth0.
Enter '?' for help on bridges, bonding and vlans.
Which one do you want to initialize? (or '?' or 'done') [eth0] eth0
Ip address for eth0? (or 'dhcp', 'none', '?') [dhcp] 192.168.1.53
Netmask? [255.255.255.0] 255.255.255.0
Gateway? (or 'none') [none] 192.168.1.1
Configuration for eth0:
  type=static
  address=192.168.1.53
  netmask=255.255.255.0
  gateway=192.168.1.1
Do you want to do any manual network configuration? (y/n) [n] n
DNS domain name? (e.g 'bar.com') mydomain.com
DNS nameserver(s)? 9.9.9.9
```

#### 4. Contraseña de root

Asignamos una contraseña segura al usuario administrador:

```shell
 Root Password
---------------
Changing password for root
New password: 
Retype password:
passwd: password for root changed by root
```

#### 5. Zona horaria

Seleccionamos nuestro [huso horario](https://es.wikipedia.org/wiki/Huso_horario), por ejemplo *Europe/Madrid*:

```shell
 Timezone
----------
Africa/            EET                GMT0               MST                Singapore
America/           EST                Greenwich          MST7MDT            Turkey
Antarctica/        EST5EDT            HST                Mexico/            UCT
Arctic/            Egypt              Hongkong           NZ                 US/
Asia/              Eire               Iceland            NZ-CHAT            UTC
Atlantic/          Etc/               Indian/            Navajo             Universal
Australia/         Europe/            Iran               PRC                W-SU
Brazil/            Factory            Israel             PST8PDT            WET
CET                GB                 Jamaica            Pacific/           Zulu
CST6CDT            GB-Eire            Japan              Poland             leap-seconds.list
Canada/            GMT                Kwajalein          Portugal           posixrules
Chile/             GMT+0              Libya              ROC
Cuba               GMT-0              MET                ROK

Which timezone are you in? (or '?' or 'none') [UTC] Europe/Madrid

 * Seeding random number generator ...
 * Saving 256 bits of creditable seed for next boot
 * Starting busybox acpid ...
 * Starting busybox crond ...
```

#### 6. Proxy (opcional)

Si no utilizamos [proxy](https://es.wikipedia.org/wiki/Servidor_proxy), simplemente pulsamos *Intro*:

```shell
 Proxy
-------
HTTP/FTP proxy URL? (e.g. 'http://proxy:8080', or 'none') [none]
```

#### 7. Repositorios de software

Elegimos el [espejo](https://es.wikipedia.org/wiki/Espejo_(Internet)) más rápido para la instalación de [paquetes](https://es.wikipedia.org/wiki/Paquete_de_software):

```shell
 APK Mirror
------------
 (f)    Find and use fastest mirror
 (s)    Show mirrorlist
 (r)    Use random mirror
 (e)    Edit /etc/apk/repositories with text editor
 (c)    Community repo enable
 (skip) Skip setting up apk repositories

Enter mirror number or URL: [1] f
```

El sistema buscará y seleccionará automáticamente el [servidor](https://es.wikipedia.org/wiki/Espejo_(Internet)) más veloz.

```shell
Finding fastest mirror... 
0.04 http://dl-cdn.alpinelinux.org/alpine/
0.14 http://uk.alpinelinux.org/alpine/
... 
1.67 http://mirrors.hust.edu.cn/alpine/
0.15 http://ftp2.crifo.org/alpine
Added mirror uk.alpinelinux.org
Updating repository indexes... done
```

#### 8. Usuario adicional y acceso remoto

Creamos un usuario no privilegiado (opcional) y habilitamos el acceso mediante [SSH](https://www.ssh.com/academy/ssh):

```shell
 User
------
Setup a user? (enter a lower-case loginname, or 'no') [no] usuario
Full name for user usuario [usuario] 
Changing password for usuario
New password: 
Retype password: 
passwd: password for usuario changed by root
Enter ssh key or URL for usuario (or 'none') [none] 
```

El sistema instalará y activará el servicio [SSH](https://www.ssh.com/academy/ssh) con las claves correspondientes.

```shell
(1/1) Installing doas (6.8.2-r8)
Executing busybox-1.37.0-r12.trigger
OK: 9 MiB in 26 packages
Which ssh server? ('openssh', 'dropbear' or 'none') [openssh] 
 * service sshd added to runlevel default
 * Caching service dependencies ...
ssh-keygen: generating new host keys: RSA ECDSA ED25519
 * Starting sshd ...
```

#### 9. Instalación en disco

Escogemos el [disco](https://es.wikipedia.org/wiki/Unidad_de_disco_duro) (por ejemplo *sda*) y el modo de instalación *sys*, que crea automáticamente las [particiones](https://es.wikipedia.org/wiki/Partición_de_disco) */boot*, */* y *swap*. Confirmamos que se borren todos los datos del [disco](https://es.wikipedia.org/wiki/Unidad_de_disco_duro):

```shell
 Disk & Install
----------------
Available disks are:
  sda   (2.1 GB QEMU     QEMU HARDDISK   )

Which disk(s) would you like to use? (or '?' for help or 'none') [none] sda

The following disk is selected:
  sda   (2.1 GB QEMU     QEMU HARDDISK   )

How would you like to use it? ('sys', 'data', 'crypt', 'lvm' or '?' for help) [?] sys

WARNING: The following disk(s) will be erased:
  sda   (2.1 GB QEMU     QEMU HARDDISK   )

WARNING: Erase the above disk(s) and continue? (y/n) [n] y
```

El sistema formateará y comenzará a instalar los archivos necesarios.

```shell
Creating file systems...
Installing system on /dev/sda3:
/mnt/boot is device /dev/sda1
100% █████████████████████████████████████████████████████████████████████████████████████████████████████████==> initramfs: creating /boot/initramfs-virt for 6.12.25-0-virt
/boot is device /dev/sda1
```

Una vez completada la instalación, se nos indicará que reiniciemos el sistema:

```shell
Installation is complete. Please reboot.
```

Apagamos la [máquina virtual](https://es.wikipedia.org/wiki/Máquina_virtual) con:

```shell
dns1:~# poweroff
```

Ya con la [máquina virtual](https://es.wikipedia.org/wiki/Máquina_virtual) detenida, retiramos la [unidad CD/DVD](https://es.wikipedia.org/wiki/Unidad_de_disco_óptico) desde la configuración de [Proxmox](https://proxmox.com/en/), pulsando *Remove* y confirmando con *Yes*. Si fuera necesario, forzamos la detención con *Stop*.

Reiniciamos la [máquina virtual](https://es.wikipedia.org/wiki/Máquina_virtual), ya sin la [unidad CD/DVD](https://es.wikipedia.org/wiki/Unidad_de_disco_óptico) conectada; y a partir de aquí podemos acceder al sistema vía [SSH](https://www.ssh.com/academy/ssh) usando el nombre usuario definido.

### Instalación del servidor DNS

Para gestionar las consultas de nuestra [red](https://es.wikipedia.org/wiki/Red_de_computadoras) de manera eficiente y segura, vamos a instalar [AdGuard Home](https://github.com/AdguardTeam/AdGuardHome), una solución de [software de código abierto y gratuito](https://es.wikipedia.org/wiki/Software_libre_y_de_código_abierto) que actúa como [servidor](https://es.wikipedia.org/wiki/Servidor) [DNS](https://es.wikipedia.org/wiki/Sistema_de_nombres_de_dominio) y bloqueador de anuncios, rastreadores y contenido malicioso a nivel de [red](https://es.wikipedia.org/wiki/Red_de_computadoras).

Comenzamos accediendo por [SSH](https://www.ssh.com/academy/ssh) a nuestra [máquina virtual](https://es.wikipedia.org/wiki/Máquina_virtual) desde un [emulador de terminal](https://es.wikipedia.org/wiki/Emulador_de_terminal) de nuestra elección. Una vez dentro, escalamos al usuario *root* con el siguiente comando:

```shell
Welcome to Alpine!

The Alpine Wiki contains a large amount of how-to guides and general
information about administrating Alpine systems.
See <https://wiki.alpinelinux.org/>.

You can setup the system with the command: setup-alpine

You may change this message by editing /etc/motd.

dns1:~$ su -
Password: 
dns1:~#
```

A continuación, nos aseguramos de que el sistema tenga instalado el [paquete](https://es.wikipedia.org/wiki/Paquete_de_software) [curl](https://curl.se). Si no estuviera presente, lo instalamos con:

```shell
dns1:~# apk add curl
```

El sistema procederá a resolver las dependencias necesarias y mostrará un mensaje de confirmación al finalizar la instalación:

```shell
(1/8) Installing brotli-libs (1.1.0-r2)
(2/8) Installing c-ares (1.34.5-r0)
(3/8) Installing libunistring (1.2-r0)
(4/8) Installing libidn2 (2.3.7-r0)
(5/8) Installing nghttp2-libs (1.64.0-r0)
(6/8) Installing libpsl (0.21.5-r3)
(7/8) Installing libcurl (8.12.1-r1)
(8/8) Installing curl (8.12.1-r1)
Executing busybox-1.37.0-r12.trigger
OK: 71 MiB in 65 packages
```

Nos desplazamos al directorio `/opt`, donde alojaremos el [software](https://es.wikipedia.org/wiki/Software):

```shell
dns1:~# cd /opt
```

Descargamos la última versión de [AdGuard Home](https://github.com/AdguardTeam/AdGuardHome) ejecutando:

```shell
dns1:/opt# curl -s -S -L https://static.adguard.com/adguardhome/release/AdGuardHome_linux_amd64.tar.gz -o AdGu
ardHome.tar.gz
```

Extraemos el contenido del archivo comprimido:

```shell
dns1:/opt# tar -xvf AdGuardHome.tar.gz
./AdGuardHome/
./AdGuardHome/AdGuardHome
./AdGuardHome/LICENSE.txt
./AdGuardHome/AdGuardHome.sig
./AdGuardHome/README.md
./AdGuardHome/CHANGELOG.md
```

Accedemos al directorio recién creado:

```shell
dns1:/opt# cd AdGuardHome
```

Y ejecutamos la instalación del [servicio](https://es.wikipedia.org/wiki/Servicio_(arquitectura_de_sistemas)):

```shell
dns1:/opt/AdGuardHome# ./AdGuardHome -s install
```

Durante la instalación, el sistema nos informará de que [AdGuard Home](https://github.com/AdguardTeam/AdGuardHome) se iniciará automáticamente al arrancar y nos proporcionará dos [direcciones](https://es.wikipedia.org/wiki/Localizador_de_recursos_uniforme) a las que podemos acceder para completar la configuración: una local (`http://127.0.0.1:3000`) y otra correspondiente a la [IP](https://es.wikipedia.org/wiki/Dirección_IP) estática que configuramos anteriormente (`http://192.168.1.53:3000`).

```shell
2025/05/01 00:00:00 [info] AdGuard Home, version v0.107.61
2025/05/01 00:00:00 [info] service: control action: install
2025/05/01 00:00:00 [info] service: started
2025/05/01 00:00:00 [info] Almost ready!
AdGuard Home is successfully installed and will automatically start on boot.
There are a few more things that must be configured before you can use it.
Click on the link below and follow the Installation Wizard steps to finish setup.
AdGuard Home is now available at the following addresses:
2025/05/01 00:00:00 [info] go to http://127.0.0.1:3000
2025/05/01 00:00:00 [info] go to http://192.168.1.53:3000
2025/05/01 00:00:00 [info] service: action install has been done successfully on linux-openrc
```

Abrimos nuestro [navegador web](https://es.wikipedia.org/wiki/Navegador_web) y accedemos a la [dirección](https://es.wikipedia.org/wiki/Localizador_de_recursos_uniforme) proporcionada para continuar con la configuración inicial.

### Configuración del servidor DNS

Una vez que accedemos a la [URL](https://es.wikipedia.org/wiki/Localizador_de_recursos_uniforme) proporcionada por el instalador de [AdGuard Home](https://github.com/AdguardTeam/AdGuardHome) - `https://192.168.1.53:3000` - se nos presenta un asistente de configuración que nos guiará paso a paso.

En primer lugar, seleccionamos el idioma *Español* en el menú desplegable situado en la esquina inferior derecha. A continuación, pulsamos el botón *Get Started* para iniciar el proceso.

#### 1. Configuración de interfaces

En la pantalla correspondiente a la *Interfaz web de administración* y al *Servidor DNS*, seleccionamos como *Interfaz de escucha* la red local, normalmente *eth0 - 192.168.1.53*. En el campo *Puerto*, introduciremos:

* *80* para la interfaz web de administración

* *53* para el servicio [DNS](https://es.wikipedia.org/wiki/Sistema_de_nombres_de_dominio) propiamente dicho.

Una vez configurados los valores, pulsamos el botón *Siguiente*.

#### 2. Credenciales de acceso

En la siguiente pantalla, definimos el nombre de usuario y la contraseña que utilizaremos para administrar el panel de control. Elegimos combinaciones seguras y fáciles de recordar, y procedemos con el botón *Siguiente*.

#### 3. Instrucciones para configurar dispositivos

[AdGuard Home](https://github.com/AdguardTeam/AdGuardHome) nos mostrará ahora una breve guía sobre cómo redirigir las consultas [DNS](https://es.wikipedia.org/wiki/Sistema_de_nombres_de_dominio) de nuestros dispositivos hacia este nuevo [servidor](https://es.wikipedia.org/wiki/Servidor). Podemos consultar esta información en cualquier momento desde el panel de control, por lo que simplemente pulsamos *Siguiente* una vez más.

#### 4. Finalización

En esta última pantalla, pulsamos *Abrir panel de control* para completar el proceso. A partir de este momento, podremos acceder al panel de administración directamente desde `http://192.168.1.53` utilizando las credenciales que acabamos de establecer.

Desde este panel, tendremos la posibilidad de:

* revisar estadísticas detalladas sobre las consultas realizadas,

* activar o desactivar filtros de bloqueo,

* importar listas personalizadas,

* y configurar parámetros avanzados de resolución y [privacidad](https://es.wikipedia.org/wiki/Privacidad).

Recomendamos familiarizarnos con las opciones disponibles consultando la [wiki oficial](https://github.com/AdguardTeam/Adguardhome/wiki/Configuration) de [AdGuard Home](https://github.com/AdguardTeam/AdGuardHome), donde encontraremos documentación completa y actualizada.

#### 5. Configuración del router (opcional pero recomendable)

Para centralizar el uso del [servidor](https://es.wikipedia.org/wiki/Servidor) y aplicarlo a todos los dispositivos conectados a nuestra [red](https://es.wikipedia.org/wiki/Red_de_computadoras), recomendamos acceder a la configuración de nuestro [router](https://es.wikipedia.org/wiki/Rúter) y establecer la [dirección IP](https://es.wikipedia.org/wiki/Dirección_IP) del [servidor](https://es.wikipedia.org/wiki/Servidor) [AdGuard Home](https://github.com/AdguardTeam/AdGuardHome) como [servidor](https://es.wikipedia.org/wiki/Servidor) [DNS](https://es.wikipedia.org/wiki/Sistema_de_nombres_de_dominio) primario distribuido mediante [DHCP](https://es.wikipedia.org/wiki/Protocolo_de_configuración_dinámica_de_host).

De esta forma, todos los dispositivos que se conecten a nuestra red obtendrán automáticamente la dirección del [servidor](https://es.wikipedia.org/wiki/Servidor) [DNS](https://es.wikipedia.org/wiki/Sistema_de_nombres_de_dominio) filtrante, sin necesidad de configurar manualmente cada equipo.

### Sincronización de la configuración

En aquellos casos en los que deseemos contar con más de una [instancia](https://es.wikipedia.org/wiki/Instancia_(informática)) de [AdGuard Home](https://github.com/AdguardTeam/AdGuardHome) - por ejemplo, para garantizar una mayor disponibilidad ante tareas de mantenimiento, fallos del [sistema](https://es.wikipedia.org/wiki/Sistema_informático) o actualizaciones - se nos plantea la cuestión lógica de cómo mantener sincronizada la configuración entre ambas instalaciones.

Existen tres enfoques principales para abordar esta necesidad, cada uno con un nivel distinto de automatización y complejidad:

#### 1. Sincronización manual

La opción más directa consiste en reproducir manualmente los ajustes realizados en una [instancia](https://es.wikipedia.org/wiki/Instancia_(informática)) en la otra. Este método resulta perfectamente válido si los cambios en la configuración son esporádicos. Basta con acceder al panel de control de cada [instancia](https://es.wikipedia.org/wiki/Instancia_(informática)) y replicar las reglas, filtros o ajustes que hayamos modificado.

#### 2. Sincronización mediante herramientas estándar

Para quienes preferimos una solución más automatizada, podemos recurrir a herramientas clásicas como [Git](https://git-scm.com) o [rsync](https://rsync.samba.org). En este caso, podemos versionar el archivo de configuración principal (`AdGuardHome.yaml`) y mantenerlo sincronizado entre [servidores](https://es.wikipedia.org/wiki/Servidor) mediante [scripts](https://es.wikipedia.org/wiki/Script) o tareas programadas. Esta alternativa ofrece flexibilidad y transparencia, pero requiere ciertos conocimientos técnicos sobre automatización y gestión de archivos de configuración.

#### 3. AdGuardHome Sync

Finalmente, disponemos de una herramienta específica llamada [AdGuardHome sync](https://github.com/bakito/adguardhome-sync), diseñada precisamente para este tipo de propósito. Esta utilidad permite mantener múltiples [instancias](https://es.wikipedia.org/wiki/Instancia_(informática)) de [AdGuard Home](https://github.com/AdguardTeam/AdGuardHome) sincronizadas en tiempo real o a intervalos regulares, replicando automáticamente configuraciones como filtros, reglas personalizadas o ajustes generales.

Podemos instalarla y configurarla siguiendo su [documentación oficial](https://github.com/bakito/adguardhome-sync/blob/main/README.md), que incluye también [un vídeo explicativo en castellano](https://www.youtube.com/watch?v=1LPeu_JG064) que detalla los pasos a seguir.

Recomendamos esta opción si buscamos un equilibrio entre facilidad de uso y automatización completa, especialmente en entornos donde la disponibilidad del servicio [DNS](https://es.wikipedia.org/wiki/Sistema_de_nombres_de_dominio) es crítica.

## Servicios DNS en la nube

Para quienes desean reforzar la [privacidad](https://es.wikipedia.org/wiki/Privacidad) sin necesidad de mantener infraestructura propia, los [servicios](https://es.wikipedia.org/wiki/Servicio_web) [DNS](https://es.wikipedia.org/wiki/Sistema_de_nombres_de_dominio) en la [nube](https://es.wikipedia.org/wiki/Computación_en_la_nube) constituyen una opción intermedia muy conveniente. Estos [servicios en línea](https://es.wikipedia.org/wiki/Servicio_web) ofrecen características similares a una solución [autoalojada](https://es.wikipedia.org/wiki/Autoalojamiento_(servicios_web)): filtrado de contenidos, estadísticas detalladas, [cifrado](https://es.wikipedia.org/wiki/Cifrado_(criptografía)) de consultas, entre otras funciones.

A diferencia de un servidor casero, no necesitamos instalar [software](https://es.wikipedia.org/wiki/Software) ni mantener un [sistema](https://es.wikipedia.org/wiki/Sistema_informático). En la mayoría de los casos, basta con crear una cuenta con el proveedor y apuntar nuestros dispositivos o nuestro [router](https://es.wikipedia.org/wiki/Rúter) a sus direcciones [DNS](https://es.wikipedia.org/wiki/Sistema_de_nombres_de_dominio). Esta configuración puede realizarse en cuestión de minutos.

Entre los proveedores más destacados encontramos:

### Control D

El servicio de [Control D](https://controld.com/personal) nos permite elegir la ubicación geográfica donde se almacenarán los [registros](https://es.wikipedia.org/wiki/Log_(informática)) de nuestras consultas. Podemos seleccionar entre distintas regiones: [Nueva York](https://www.nyc.gov) ([Estados Unidos](https://www.usa.gov/es/)), [Ámsterdam](https://www.amsterdam.nl/en/) ([Países Bajos](https://www.government.nl)) y [Sídney](https://www.cityofsydney.nsw.gov.au) ([Australia](https://www.homeaffairs.gov.au)).

Este enfoque nos ofrece un mayor control sobre la jurisdicción bajo la cual se rige el tratamiento de nuestros datos. Además, [Control D](https://controld.com/personal) también dispone de filtros avanzados y reglas personalizables, lo que permite adaptar el comportamiento del [servidor](https://es.wikipedia.org/wiki/Servidor) [DNS](https://es.wikipedia.org/wiki/Sistema_de_nombres_de_dominio) a nuestras preferencias particulares. Esta flexibilidad resulta especialmente útil en [redes domésticas](https://es.wikipedia.org/wiki/Red_de_computadoras) con múltiples perfiles de uso (trabajo, familia, menores, etc.)

### NextDNS

[NextDNS](https://nextdns.io) es otro servicio muy valorado por la comunidad orientada a [privacidad](https://es.wikipedia.org/wiki/Privacidad) digital. Permite definir la ubicación del almacenamiento de los [logs](https://es.wikipedia.org/wiki/Log_(informática)) en tres regiones principales: [Estados Unidos](https://www.usa.gov/es/), la [Unión Europea](https://european-union.europa.eu/index_es) o [Zúrich](https://www.zuerich.ch/zh/es/index.html) ([Suiza](https://www.aboutswitzerland.eda.admin.ch/es)). Esta última opción, en particular, destaca por su sólido marco legal en materia de protección de datos.

[NextDNS](https://nextdns.io) proporciona una interfaz de configuración intuitiva, completamente traducida al castellano, y permite definir filtros personalizados, listas negras y blancas, reglas por dispositivo, estadísticas detalladas y soporte para [DNS](https://es.wikipedia.org/wiki/Sistema_de_nombres_de_dominio) [cifrado](https://es.wikipedia.org/wiki/Cifrado_(criptografía)) ([DoH](https://es.wikipedia.org/wiki/DNS_mediante_HTTPS)/[DoT](https://es.wikipedia.org/wiki/DNS_mediante_TLS)). El servicio ofrece también un plan gratuito que permite hasta 300.000 consultas [DNS](https://es.wikipedia.org/wiki/Sistema_de_nombres_de_dominio) mensuales, lo cual resulta más que suficiente para el uso habitual en un hogar medio.

Para quienes deseen una introducción visual, recomendamos [este vídeo explicativo](https://www.youtube.com/watch?v=nGCCqOLK5uE), en el que se presentan sus funciones básicas de forma clara y amena.

### Consideraciones sobre la jurisdicción y la privacidad

La ubicación de los [registros](https://es.wikipedia.org/wiki/Log_(informática)) es un aspecto crucial en lo que respecta a la privacidad. Nosotros recomendamos preferentemente opciones como [Suiza](https://www.aboutswitzerland.eda.admin.ch/es), dado que su legislación en protección de datos es una de las más estrictas y garantistas a nivel mundial.

Por ello, si nuestra prioridad es la privacidad de nuestras consultas [DNS](https://es.wikipedia.org/wiki/Sistema_de_nombres_de_dominio) y de los datos generados por ellas, sugerimos emplear [NextDNS](https://nextdns.io) con almacenamiento de [registros](https://es.wikipedia.org/wiki/Log_(informática)) en [Zúrich](https://www.zuerich.ch/zh/es/index.html) ([Suiza](https://www.aboutswitzerland.eda.admin.ch/es)). Su equilibrio entre opciones avanzadas, facilidad de uso y garantías legales lo convierte en una solución idónea para usuarios con conciencia digital y exigencias técnicas moderadas o altas.

## Conclusión

A lo largo de este recorrido hemos explorado distintas estrategias para mejorar nuestra [privacidad](https://es.wikipedia.org/wiki/Privacidad) mediante un control más consciente sobre el [DNS](https://es.wikipedia.org/wiki/Sistema_de_nombres_de_dominio). Cada una de ellas presenta ventajas y consideraciones particulares, y puede ser adoptada en función de nuestras necesidades, conocimientos técnicos y contextos de uso.

Los [servidores](https://es.wikipedia.org/wiki/Servidor) [DNS](https://es.wikipedia.org/wiki/Sistema_de_nombres_de_dominio) públicos constituyen el punto de partida más accesible. En muchos casos, basta con modificar una dirección en la configuración de [red](https://es.wikipedia.org/wiki/Red_de_computadoras) para empezar a disfrutar de mayor velocidad, bloqueo de rastreadores y protección contra [malware](https://es.wikipedia.org/wiki/Malware). Sin embargo, al usar estos servicios depositamos nuestra confianza en terceros, lo que implica cierto grado de dependencia en cuanto al tratamiento de nuestros datos.

Los [servidores](https://es.wikipedia.org/wiki/Servidor) [DNS](https://es.wikipedia.org/wiki/Sistema_de_nombres_de_dominio) [autoalojados](https://es.wikipedia.org/wiki/Autoalojamiento_(servicios_web)) ofrecen el máximo nivel de control. Al encargarnos personalmente de la resolución de nombres dentro de nuestra [red](https://es.wikipedia.org/wiki/Red_de_computadoras), podemos definir con exactitud qué [dominios](https://es.wikipedia.org/wiki/Dominio_de_internet) se permiten, cuáles se bloquean y cómo se gestionan los [registros](https://es.wikipedia.org/wiki/Log_(informática)). Esta opción requiere conocimientos técnicos y cierto mantenimiento, pero nos brinda una soberanía digital difícil de igualar.

Por último, los [servicios](https://es.wikipedia.org/wiki/Servicio_web) [DNS](https://es.wikipedia.org/wiki/Sistema_de_nombres_de_dominio) en la [nube](https://es.wikipedia.org/wiki/Computación_en_la_nube) nos permiten disfrutar de muchas de las ventajas del [autoalojamiento](https://es.wikipedia.org/wiki/Autoalojamiento_(servicios_web)) sin necesidad de gestionar infraestructura. Incluyen [cifrado](https://es.wikipedia.org/wiki/Cifrado_(criptografía)), estadísticas, personalización avanzada y la posibilidad de elegir jurisdicción donde se almacenan nuestros datos.

En resumen, recomendamos comenzar por lo más sencillo: cambiar los [DNS](https://es.wikipedia.org/wiki/Sistema_de_nombres_de_dominio) que usamos actualmente por otros que respeten mejor nuestra [privacidad](https://es.wikipedia.org/wiki/Privacidad). Podemos hacerlo directamente desde el [router](https://es.wikipedia.org/wiki/Rúter) o en cada dispositivo. Más adelante, si deseamos avanzar hacia soluciones más potentes, siempre podemos explorar servicios como [NextDNS](https://nextdns.io) o montar nuestra propia [instancia](https://es.wikipedia.org/wiki/Instancia_(informática)) de [AdGuard Home](https://github.com/AdguardTeam/AdGuardHome).

Lo esencial es comprender que el [DNS](https://es.wikipedia.org/wiki/Sistema_de_nombres_de_dominio) actúa como traductor entre los [nombres de dominio](https://es.wikipedia.org/wiki/Dominio_de_internet) que introducimos en el [navegador](https://es.wikipedia.org/wiki/Navegador_web) y las [direcciones IP](https://es.wikipedia.org/wiki/Dirección_IP) que permiten acceder a los [servidores](https://es.wikipedia.org/wiki/Servidor). Controlar dónde se realiza esta traducción - y si se realiza de forma [cifrada](https://es.wikipedia.org/wiki/Cifrado_(criptografía)) - representa un paso fundamental para evitar que terceros espíen nuestras actividades en línea.

Con medidas simples y bien elegidas, podemos navegar con mayor confianza, sabiendo que nuestra [privacidad](https://es.wikipedia.org/wiki/Privacidad) está mejor protegida.
