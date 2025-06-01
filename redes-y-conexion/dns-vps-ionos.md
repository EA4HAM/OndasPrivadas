# Revisión técnica del VPS IONOS 1-1-10

Este análisis corresponde a una prueba técnica de un [servidor](https://es.wikipedia.org/wiki/Servidor) básico de IONOS, con el fin de evaluar su viabilidad para [alojar](https://es.wikipedia.org/wiki/Alojamiento_web) una instancia de [AdGuard Home](https://github.com/AdguardTeam/AdGuardHome). Nuestra intención es contar con un bloqueador de anuncios, rastreadores y [sitios](https://es.wikipedia.org/wiki/Sitio_web) maliciosos disponible globalmente, aprovechando las ventajas de una solución [DNS](https://es.wikipedia.org/wiki/Sistema_de_nombres_de_dominio) personalizada y siempre accesible desde [Internet](https://es.wikipedia.org/wiki/Internet).

A fecha de 1 de junio de 2025, este servidor [VPS](https://es.wikipedia.org/wiki/Servidor_virtual_privado) tiene un coste de 1 €/mes + IVA e incluye [conectividad](https://es.wikipedia.org/wiki/Conectividad_(telecomunicaciones)) mediante [IPv4](https://datatracker.ietf.org/doc/html/rfc791) y un [prefijo](https://es.wikipedia.org/wiki/Subred) /64 de [IPv6](https://www.rfc-es.org/rfc/rfc2460-es.txt) asignado.

## Hardware y virtualización

El VPS 1-1-10 (también conocido como “VPS Linux XS”) ofrece unos recursos básicos: 1 [vCPU](https://es.wikipedia.org/wiki/Unidad_central_de_procesamiento), 1 GB de [RAM](https://es.wikipedia.org/wiki/Memoria_de_acceso_aleatorio), 10 GB de [almacenamiento NVMe](https://es.wikipedia.org/wiki/NVM_Express). Estas especificaciones, aunque modestas, son coherentes con su precio de entrada por 1€ al mes. A continuación, revisamos sus aspectos de [hardware](https://es.wikipedia.org/wiki/Hardware) y soporte de [máquinas virtuales](https://es.wikipedia.org/wiki/Máquina_virtual) con rigor técnico:

* **CPU (vCPU)**: IONOS utiliza tanto [procesadores](https://es.wikipedia.org/wiki/Unidad_central_de_procesamiento) [AMD EPYC](https://www.amd.com/es/products/processors/server/epyc.html) como [Intel Xeon](https://www.intel.la/content/www/xl/es/products/details/processors/xeon.html) en su infraestructura, según el nodo donde se aprovisione el [VPS](https://es.wikipedia.org/wiki/Servidor_virtual_privado). El modelo de [procesador](https://es.wikipedia.org/wiki/Unidad_central_de_procesamiento) no puede seleccionarse manualmente. En cualquier caso, el asignado al [VPS](https://es.wikipedia.org/wiki/Servidor_virtual_privado) soporta las extensiones de [virtualización](https://es.wikipedia.org/wiki/Virtualización) por [hardware](https://es.wikipedia.org/wiki/Hardware), como [AMD-V](https://es.wikipedia.org/wiki/Virtualización_x86#Virtualización_AMD_(AMD-V)) en [CPUs](https://es.wikipedia.org/wiki/Unidad_central_de_procesamiento) [AMD](https://www.amd.com/es.html), equivalente a [Intel VT-x](https://es.wikipedia.org/wiki/Virtualización_x86#Intel_VT_(IVT)), y también [instrucciones AES-NI](https://es.wikipedia.org/wiki/Conjunto_de_Instrucciones_AES) que permiten cifrado acelerado. Esto se traduce en un buen rendimiento en operaciones como [VPN](https://es.wikipedia.org/wiki/Red_privada_virtual), [HTTPS](https://es.wikipedia.org/wiki/Protocolo_seguro_de_transferencia_de_hipertexto) o [DNS mediante HTTPS](https://es.wikipedia.org/wiki/DNS_mediante_HTTPS). En resumen, no hay limitaciones notables en las capacidades de la [CPU](https://es.wikipedia.org/wiki/Unidad_central_de_procesamiento) virtual aparte de la potencia bruta limitada por tratarse de un solo núcleo. Conviene señalar que, al disponer de solo una [vCPU](https://es.wikipedia.org/wiki/Unidad_central_de_procesamiento), no existe paralelismo a nivel de [CPU](https://es.wikipedia.org/wiki/Unidad_central_de_procesamiento) más allá del único hilo de ejecución disponible, lo que limita el rendimiento en pruebas multihilo.

* **Memoria (1 GB RAM)**: De la [RAM](https://es.wikipedia.org/wiki/Memoria_de_acceso_aleatorio) nominal de 1 GB, el [sistema operativo](https://es.wikipedia.org/wiki/Sistema_operativo) muestra algo menos disponible debido a la [memoria](https://es.wikipedia.org/wiki/Memoria_(informática)) reservada para el [núcleo](https://es.wikipedia.org/wiki/Núcleo_(informática)) y la [virtualización](https://es.wikipedia.org/wiki/Virtualización). Es normal ver alrededor de 0,8GB utilizables para usuarios, ya que el [núcleo Linux](https://es.wikipedia.org/wiki/Núcleo_Linux) y la sobrecarga de la [máquina virtual](https://es.wikipedia.org/wiki/Máquina_virtual) pueden reservar 15-20% en este caso. Esto es esperable: la [memoria](https://es.wikipedia.org/wiki/Memoria_(informática)) “reservada” incluye [tablas de página](https://es.wikipedia.org/wiki/Tabla_de_paginación), [búfers](https://es.wikipedia.org/wiki/Búfer_de_datos) y el propio espacio del [núcleo](https://es.wikipedia.org/wiki/Núcleo_(informática)) en [RAM](https://es.wikipedia.org/wiki/Memoria_de_acceso_aleatorio). Para un [VPS](https://es.wikipedia.org/wiki/Servidor_virtual_privado) pequeño, 1GB sigue siendo suficiente para las tareas previstas (como [AdGuard Home](https://github.com/AdguardTeam/AdGuardHome)), pero es importante ser consciente de este margen para planificar el uso.

* **Almacenamiento NVMe (10GB)**: El plan garantiza almacenamiento en [unidades SSD NVMe](https://es.wikipedia.org/wiki/NVM_Express) de alto rendimiento. Hemos verificado mediante pruebas de velocidad que se trata de [NVMe](https://es.wikipedia.org/wiki/NVM_Express) real: por ejemplo, se midió una [velocidad](https://es.wikipedia.org/wiki/Tasa_de_bits) secuencial en torno a 500 MB/s tanto en lectura como escritura, y unas [IOPS](https://es.wikipedia.org/wiki/IOPS) aleatorias 4k cercanas a 20k (lectura/escritura). Estas cifras son consistentes con un [SSD NVMe](https://es.wikipedia.org/wiki/NVM_Express) virtualizado (un [SSD](https://es.wikipedia.org/wiki/Unidad_de_estado_sólido) [SATA](https://es.wikipedia.org/wiki/Serial_ATA) típico suele estar limitado a 550 MB/s y a menos [IOPS](https://es.wikipedia.org/wiki/IOPS) en 4k). Aunque no se alcanza el rendimiento máximo de [NVMe](https://es.wikipedia.org/wiki/NVM_Express) en entornos bare-metal, los resultados superan ampliamente a los [SSD](https://es.wikipedia.org/wiki/Unidad_de_estado_sólido) [SATA](https://es.wikipedia.org/wiki/Serial_ATA) y son adecuados para un [VPS](https://es.wikipedia.org/wiki/Servidor_virtual_privado) de entrada. En conclusión, el uso de [NVMe](https://es.wikipedia.org/wiki/NVM_Express) aporta baja [latencia](https://es.wikipedia.org/wiki/Latencia) y buen rendimiento de entrada/salida, adecuado para un [VPS](https://es.wikipedia.org/wiki/Servidor_virtual_privado) pequeño, sin ser un [cuello de botella](https://es.wikipedia.org/wiki/Cuello_de_botella_(informática)) grave.

Además, la infraestructura de IONOS ofrece tráfico ilimitado con [velocidad](https://es.wikipedia.org/wiki/Tasa_de_bits) de hasta 1 Gbit/s y protección [DDoS](https://es.wikipedia.org/wiki/Ataque_de_denegación_de_servicio) en todos sus [VPS](https://es.wikipedia.org/wiki/Servidor_virtual_privado), lo cual complementa favorablemente las capacidades de [hardware](https://es.wikipedia.org/wiki/Hardware) puro con una conectividad robusta.

## Almacenamiento y rendimiento de disco

El subsistema de almacenamiento de este VPS 1-1-10 de IONOS está respaldado por unidades [NVMe](https://es.wikipedia.org/wiki/NVM_Express). Con el fin de validar su rendimiento, procedimos a realizar pruebas utilizando la herramienta [fio](https://github.com/axboe/fio), una utilidad de referencia para el análisis de entrada/salida en entornos [GNU/Linux](https://es.wikipedia.org/wiki/GNU/Linux). Ejecutamos pruebas de lectura y escritura, tanto secuenciales como aleatorias, empleando tamaños de bloque de 4k, 64k, 512k y 1M, que representan distintos patrones de uso típicos: desde operaciones frecuentes de bajo volumen hasta transferencias sostenidas de [archivos](https://es.wikipedia.org/wiki/Archivo_(informática)) grandes.

Los resultados se resumen en la siguiente tabla:

| Tamaño de bloque | Lectura (IOPS) | Escritura (IOPS) | Total (IOPS) |
| --- | --- | --- | --- |
| 4k | 79.57 MB/s (19.8k) | 79.78 MB/s (19.9k) | 159.36 MB/s (39.8k) |
| 64k | 493.08 MB/s (7.7k) | 495.67 MB/s (7.7k) | 988.75 MB/s (15.4k) |
| 512k | 474.64 MB/s (927) | 499.86 MB/s (976) | 974.51 MB/s (1.9k) |
| 1M | 468.39 MB/s (457) | 499.59 MB/s (487) | 967.98 MB/s (944) |

Los datos revelan un rendimiento competitivo dentro del segmento de entrada, con [velocidades](https://es.wikipedia.org/wiki/Tasa_de_bits) secuenciales cercanas a 500 MB/s y un rendimiento destacado en operaciones aleatorias de lectura/escritura, particularmente en bloques de 4k, donde se alcanzaron cerca de 40k [operaciones por segundo](https://es.wikipedia.org/wiki/IOPS) en total (20k en lectura y 20k en escritura). Consideramos que este resultado es especialmente relevante para escenarios como:

* acceso intensivo a [bases de datos](https://es.wikipedia.org/wiki/Base_de_datos) o sistemas [caché](https://es.wikipedia.org/wiki/Caché_(informática))

* registro continuo de eventos y [logs](https://es.wikipedia.org/wiki/Log_(informática)) de servicios

* resolución de consultas [DNS](https://es.wikipedia.org/wiki/Sistema_de_nombres_de_dominio), como en el caso de [AdGuard Home](https://github.com/AdguardTeam/AdGuardHome), donde predominan operaciones breves y concurrentes

Las pruebas con bloques de mayor tamaño (64k, 512k, 1M) ponen de manifiesto la capacidad de transferencia sostenida del sistema de almacenamiento, tanto en lectura como en escritura, sin indicios de [cuello de botella](https://es.wikipedia.org/wiki/Cuello_de_botella_(informática)) atribuibles al entorno [virtualizado](https://es.wikipedia.org/wiki/Virtualización) o a una contención de recursos, lo cual garantiza una baja [latencia](https://es.wikipedia.org/wiki/Latencia) y buen desempeño.

Cabe señalar que, si bien las cifras no alcanzan valores máximos de [unidades NVMe](https://es.wikipedia.org/wiki/NVM_Express) en entornos bare-metal (frecuentemente por encima de 3.000 MB/s), el rendimiento aquí registrado supera con claridad al de unidades [SSD](https://es.wikipedia.org/wiki/Unidad_de_estado_sólido) [SATA](https://es.wikipedia.org/wiki/Serial_ATA) tradicionales, e incluso al de numerosos [VPS](https://es.wikipedia.org/wiki/Servidor_virtual_privado) basados en almacenamiento compartido.

En conclusión, el subsistema de almacenamiento del VPS 1-1-10 de IONOS cumple ampliamente con los requisitos para aplicaciones ligeras o de carga media, destacando en entornos donde la [latencia](https://es.wikipedia.org/wiki/Latencia) y la eficiencia en operaciones pequeñas son factores determinantes.

## Rendimiento de red

Para evaluar la calidad de la [conectividad](https://es.wikipedia.org/wiki/Conectividad_(telecomunicaciones)) internacional del VPS 1-1-10 de IONOS, procedimos a ejecutar pruebas de rendimiento mediante conexiones tanto [IPv4](https://datatracker.ietf.org/doc/html/rfc791) como [IPv6](https://www.rfc-es.org/rfc/rfc2460-es.txt), abarcando múltiples ubicaciones geográficas y proveedores de tránsito. Las mediciones incluyeron [velocidad](https://es.wikipedia.org/wiki/Tasa_de_bits) de envío, [velocidad](https://es.wikipedia.org/wiki/Tasa_de_bits) de recepción y [latencia](https://es.wikipedia.org/wiki/Latencia) promedio. A continuación, detallamos los resultados obtenidos:

### Resultados con IPv4

| Proveedor | Ubicación | Envío | Recepción | Latencia |
| --- | --- | --- | --- | --- |
| Clouvider | Londres, Reino Unido (10G) | 1.81 Gbits/sec | 3.97 Gbits/sec | 35.7 ms |
| Eranium | Ámsterdam, Países Bajos (100G) | 1.80 Gbits/sec | 3.82 Gbits/sec | 39.2 ms |
| Uztelecom | Taskent, Uzbekistán (10G) | 1.20 Gbits/sec | 984 Mbits/sec | 147 ms |
| Leaseweb | Singapore, SG (10G) | 674 Mbits/sec | 856 Mbits/sec | 173 ms |
| Clouvider | Los Ángeles, EE.UU. (10G) | 870 Mbits/sec | 846 Mbits/sec | 176 ms |
| Leaseweb | NYC, NY, US (10G) | 1.40 Gbits/sec | 1.63 Gbits/sec | 108 ms |
| Edgoo | São Paulo, Brasil (1G) | 706 Mbits/sec | 755 Mbits/sec | 215 ms |

### Resultados con IPv6

| Proveedor | Ubicación | Envío | Recepción | Latencia |
| --- | --- | --- | --- | --- |
| Clouvider | Londres, Reino Unido (10G) | 1.83 Gbits/sec | 5.01 Gbits/sec | 35.9 ms |
| Eranium | Ámsterdam, Países Bajos (100G) | 1.83 Gbits/sec | 3.57 Gbits/sec | 38.9 ms |
| Uztelecom | Taskent, Uzbekistán (10G) | 1.28 Mbits/sec| 91.5 Mbits/sec | 148 ms |
| Leaseweb | Singapore, SG (10G) | 838 Mbits/sec | 936 Mbits/sec | 172 ms|
| Clouvider | Los Ángeles, EE.UU. (10G) | 855 Mbits/sec | 906 Mbits/sec | 176 ms |
| Leaseweb | NYC, NY, US (10G) | 1.54 Gbits/sec | 1.59 Gbits/sec | 108 ms |
| Edgoo | São Paulo, Brasil (1G) | 713 Mbits/sec | 691 Mbits/sec | 215 ms |

A partir de estas métricas, observamos que la conectividad del [VPS](https://es.wikipedia.org/wiki/Servidor_virtual_privado) bajo análisis es sólida y presenta un comportamiento equilibrado en la mayoría de ubicaciones, con [anchos de banda](https://es.wikipedia.org/wiki/Ancho_de_banda_(informática)) notables tanto en descarga como en subida. En particular, se registraron tasas agregadas superiores a 3 Gbits/sec en varios nodos europeos, lo que refleja una integración eficaz con proveedores de tránsito de primer nivel.

La única excepción fue el bajo rendimiento con [IPv6](https://www.rfc-es.org/rfc/rfc2460-es.txt) en [Uzbekistán](https://gov.uz/en), posiblemente debido a rutas degradadas. Fuera de este caso aislado, la consistencia de resultados en ambas pilas de [red](https://es.wikipedia.org/wiki/Red_de_computadoras), salvo excepciones regionales, respalda la calidad de la implementación dual-stack de IONOS.

Consideramos que esta infraestructura de [red](https://es.wikipedia.org/wiki/Red_de_computadoras) es adecuada para desplegar servicios distribuidos, redes privadas (como [VPN](https://es.wikipedia.org/wiki/Red_privada_virtual) o [redes de distribución de contenidos (CDN)](https://es.wikipedia.org/wiki/Red_de_distribución_de_contenidos)), así como [sistemas](https://es.wikipedia.org/wiki/Sistema_informático) accesibles desde múltiples regiones. Asimismo, la baja [latencia](https://es.wikipedia.org/wiki/Latencia) registrada en Europa y Norteamérica favorece el uso del [servidor](https://es.wikipedia.org/wiki/Servidor) como punto de resolución [DNS](https://es.wikipedia.org/wiki/Sistema_de_nombres_de_dominio) personalizado o nodo intermedio en arquitecturas de [alta disponibilidad](https://es.wikipedia.org/wiki/Sistema_de_nombres_de_dominio).

## Rendimiento computacional

Con el objetivo de analizar el rendimiento bruto del procesador asignado al VPS 1-1-10 de IONOS, intentamos ejecutar la suite [Geekbench 6](https://www.geekbench.com/), referencia moderna para [benchmarking](https://es.wikipedia.org/wiki/Benchmark_(informática)) sintético multiplataforma. Sin embargo, encontramos una limitación significativa: la escasa cantidad de [RAM](https://es.wikipedia.org/wiki/Memoria_de_acceso_aleatorio) disponible impidió completar la prueba con [Geekbench 6](https://www.geekbench.com/), incluso tras habilitar manualmente un [archivo de intercambio (swap)](https://es.wikipedia.org/wiki/Espacio_de_intercambio) de 1 GB, lo cual es un comportamiento común en [VPS](https://es.wikipedia.org/wiki/Servidor_virtual_privado) con 1 GB de [RAM](https://es.wikipedia.org/wiki/Memoria_de_acceso_aleatorio).

El mensaje de error fue el siguiente:

```bash
Geekbench test failed and low memory was detected. Add at least 1GB of SWAP or use GB4 instead (higher compatibility with low memory systems).
```

Ante esta situación, decidimos recurrir a versiones anteriores de la herramienta, más compatibles con entornos de recursos limitados. Los resultados obtenidos fueron los siguientes:

### Geekbench 4

| Prueba | Resultado |
| --- | --- |
| Rendimiento de un solo hilo | 4518 |
| Rendimiento multihilo | 4004 |
| Resultado completo | [Ver en línea](https://browser.geekbench.com/v4/cpu/18762046) |

### Geekbench 5

| Prueba | Resultado |
| --- | --- |
| Rendimiento de un solo hilo | 892 |
| Rendimiento multihilo | 833 |
| Resultado completo | [Ver en línea](https://browser.geekbench.com/v5/cpu/23579697) |

Dado que el [VPS](https://es.wikipedia.org/wiki/Servidor_virtual_privado) dispone únicamente de un núcleo virtual, la puntuación multihilo tiene un valor interpretativo limitado al ejecutarse sobre un único núcleo con soporte hiperhilo no garantizado. Las puntuaciones obtenidas, modestas en comparación con equipos físicos, se encuentran dentro del rango esperable para entornos virtualizados de bajo coste. El rendimiento se ve limitado tanto por la frecuencia base del [procesador](https://es.wikipedia.org/wiki/Unidad_central_de_procesamiento) como por las restricciones de [memoria](https://es.wikipedia.org/wiki/Memoria_(informática)), que en algunos casos limitan incluso la ejecución de pruebas sintéticas modernas.

Es suficiente para [DNS](https://es.wikipedia.org/wiki/Sistema_de_nombres_de_dominio), tareas ligeras de [red](https://es.wikipedia.org/wiki/Red_de_computadoras) y [cifrado](https://es.wikipedia.org/wiki/Cifrado_(criptografía)) moderado (gracias a la disponibilidad de [instrucciones AES-NI](https://es.wikipedia.org/wiki/Conjunto_de_Instrucciones_AES)), pero no se recomienda para cargas sostenidas de cómputo, [compilación](https://es.wikipedia.org/wiki/Compilador), procesamiento [multimedia](https://es.wikipedia.org/wiki/Multimedia) ni [virtualización](https://es.wikipedia.org/wiki/Virtualización) anidada, aunque técnicamente admite esta última en algunos casos gracias al soporte de [AMD-V](https://es.wikipedia.org/wiki/Virtualización_x86#Virtualización_AMD_(AMD-V)) o [Intel VT-x](https://es.wikipedia.org/wiki/Virtualización_x86#Intel_VT_(IVT)).

## Nota de transparencia

Este artículo ha sido elaborado de forma totalmente independiente. No mantenemos ninguna relación de afiliación, patrocinio o colaboración con IONOS ni con ninguna de las entidades mencionadas. El [VPS](https://es.wikipedia.org/wiki/Servidor_virtual_privado) utilizado para esta evaluación fue contratado por nosotros como clientes finales y sufragado íntegramente con fondos propios, sin intervención ni compensación externa. Las conclusiones reflejan exclusivamente los resultados observados durante las pruebas, sin influencia comercial de ningún tipo.

## Conclusión

Este [VPS](https://es.wikipedia.org/wiki/Servidor_virtual_privado) básico de IONOS ofrece un rendimiento sorprendentemente alto en red y almacenamiento para su precio, pero está claramente limitado por su única [CPU](https://es.wikipedia.org/wiki/Unidad_central_de_procesamiento) y la escasa cantidad de [RAM](https://es.wikipedia.org/wiki/Memoria_de_acceso_aleatorio) disponible. El rendimiento de procesamiento es bajo, y la falta de [memoria](https://es.wikipedia.org/wiki/Memoria_de_acceso_aleatorio) impidió completar [Geekbench 6](https://www.geekbench.com/), incluso tras configurar [swap](https://es.wikipedia.org/wiki/Espacio_de_intercambio). Aun así, lo consideramos adecuado para [servicios](https://es.wikipedia.org/wiki/Servicio_web) ligeros como [proxies](https://es.wikipedia.org/wiki/Servidor_proxy), [servidores web](https://es.wikipedia.org/wiki/Servidor_web) estáticos, túneles [VPN](https://es.wikipedia.org/wiki/Red_privada_virtual) o automatizaciones simples.

En nuestro caso, se ha evaluado como plataforma para instalar [AdGuard Home](https://github.com/AdguardTeam/AdGuardHome), con el fin de disponer de un bloqueador de [DNS](https://es.wikipedia.org/wiki/Sistema_de_nombres_de_dominio) siempre disponible desde [Internet](https://es.wikipedia.org/wiki/Internet). Aunque es técnicamente viable implementarlo y mantenerlo operativo, esta solución requiere conocimientos de administración de servidores [GNU/Linux](https://es.wikipedia.org/wiki/GNU/Linux): configuración del [cortafuegos](https://es.wikipedia.org/wiki/Cortafuegos_(informática)), [seguridad](https://es.wikipedia.org/wiki/Seguridad_informática), [actualizaciones](https://es.wikipedia.org/wiki/Parche_(informática)), mantenimiento, supervisión, etcétera.

Teniendo en cuenta que este [VPS](https://es.wikipedia.org/wiki/Servidor_virtual_privado) cuesta 1 €/mes + IVA, y que servicios como [Control D](https://controld.com/plans?step=plans) o [NextDNS](https://nextdns.io) tienen un precio anual de 16,52 € (19,99 € con IVA), puede resultar difícil justificar su uso si únicamente deseamos un filtro [DNS](https://es.wikipedia.org/wiki/Sistema_de_nombres_de_dominio), dado que las alternativas comerciales ofrecen [alta disponibilidad](https://es.wikipedia.org/wiki/Alta_disponibilidad), mantenimiento nulo y límites razonables incluso en sus planes gratuitos.

En conclusión, aunque la experiencia de montar nuestro propio [servidor](https://es.wikipedia.org/wiki/Servidor) puede resultar enriquecedora desde el punto de vista del aprendizaje o para quienes deseen tener un control absoluto sobre el tráfico, no siempre es la opción más práctica frente a servicios gestionados, especialmente cuando se prioriza simplicidad y soporte multiplataforma sin mantenimiento.
