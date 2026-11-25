---
title: "Qué es una eSIM y cómo llega el perfil a tu móvil"
date: 2026-11-20 18:00:00 +0100
categories: explicado
tags: [esim, gsma, sgp22, movil]
description: "Lo que ocurre de verdad entre que escaneas un código QR y tu móvil tiene línea: las piezas de la arquitectura eSIM de la GSMA, paso a paso."
image: /assets/img/posts/esim-portada.svg
image_alt: "Ilustración de un móvil con un chip eSIM y un código QR"
image_caption: "Ilustración propia."
---

Escaneas un código QR, esperas unos segundos y tu móvil ya tiene línea, sin tarjeta de plástico y sin pasar por la tienda. Parece magia, pero detrás hay una arquitectura muy concreta definida por la GSMA, con servidores, certificados y un chip que guarda tus credenciales. En esta entrada la desmontamos pieza a pieza.

<!--more-->

## De la tarjeta de plástico al chip soldado

Una SIM clásica es una tarjeta con un pequeño procesador donde el operador graba tus credenciales: la identidad de tu línea y las claves con las que la red te autentica. Si quieres cambiar de operador, cambias de tarjeta.

La eSIM separa dos cosas que antes iban juntas:

- **El chip (eUICC)**: viene soldado en el móvil, el reloj o el coche, y puede guardar **varios perfiles**. Cada eUICC tiene un identificador único, el **EID**.
- **El perfil**: el conjunto de datos y aplicaciones del operador que antes venía grabado en la tarjeta. Ahora se **descarga** por Internet y se instala en el chip.

Dentro del eUICC hay zonas de seguridad separadas: una raíz que gestiona el chip (ISD-R), un dominio que guarda las credenciales del propio chip (ECASD) y un contenedor aislado por cada perfil instalado (ISD-P). Así, los perfiles de dos operadores conviven sin poder verse entre sí.

## Las piezas de la arquitectura

La GSMA define la arquitectura de la eSIM para dispositivos de consumo en dos documentos: **SGP.21** (arquitectura) y **SGP.22** (especificación técnica). Estas son las piezas que intervienen:

| Pieza | Dónde está | Qué hace |
| --- | --- | --- |
| **Operador** | Sus sistemas de negocio | Da de alta la línea y encarga el perfil |
| **SM-DP+** | Servidor del operador o de un proveedor | Prepara, protege y entrega los perfiles |
| **SM-DS** | Servidor de descubrimiento | Avisa al dispositivo de que tiene un perfil pendiente |
| **LPA** | En el propio móvil | El «asistente» que descarga el perfil y te deja gestionarlo |
| **eUICC** | Chip soldado en el móvil | Guarda e instala los perfiles de forma segura |

Cada conversación entre dos piezas tiene su interfaz con nombre propio en la especificación: por ejemplo, **ES2+** entre el operador y el SM-DP+, **ES9+** entre el móvil y el SM-DP+, o **ES10** entre el LPA y el chip.

## Paso a paso: qué ocurre cuando escaneas el QR

![Diagrama del flujo de descarga de un perfil eSIM entre operador, SM-DP+, móvil y chip eUICC]({{ "/assets/img/posts/esim-flujo.svg" | relative_url }})
*Flujo simplificado de descarga de un perfil. Diagrama propio basado en GSMA SGP.22.*

1. **El operador encarga el perfil.** Cuando contratas la línea, el operador pide al SM-DP+ que prepare un perfil para ti (interfaz ES2+).
2. **Recibes un código de activación.** Es lo que va dentro del QR. Contiene la **dirección del SM-DP+** y un **Matching ID**, un identificador que permite al servidor saber qué perfil te corresponde. Escrito en texto tiene esta forma: `LPA:1$direccion-del-smdp$MATCHING-ID`.
3. **El móvil y el servidor se autentican.** El LPA se conecta al SM-DP+ (ES9+) y ambos se identifican con certificados digitales emitidos dentro de la infraestructura de claves de la GSMA. El chip demuestra que es un eUICC legítimo y el servidor demuestra que es un SM-DP+ legítimo.
4. **El perfil viaja cifrado para tu chip.** El SM-DP+ prepara un paquete vinculado a ese eUICC concreto. El móvil solo lo transporta: la comunicación segura es de extremo a extremo entre el servidor y el chip (ES8+), así que ni siquiera el sistema operativo puede leer su contenido.
5. **El chip instala el perfil** en su propio contenedor aislado y envía una notificación de resultado al SM-DP+.
6. **Lo activas.** Desde los ajustes del móvil, que hablan con el chip a través del LPA, habilitas el perfil, lo desactivas, le cambias el nombre o lo borras.

## ¿Y si no hay código QR? El servicio de descubrimiento

No siempre hace falta escanear nada. El operador puede **registrar un evento** en el SM-DS indicando que hay un perfil esperando a un EID concreto. Cuando el móvil consulta al SM-DS, recibe la dirección del SM-DP+ y continúa con la descarga como en el paso 3. Es lo que permite, por ejemplo, activar la línea directamente desde la app del operador.

## Lo que cambia para ti

- **Varias líneas en un dispositivo**, por ejemplo la personal y la del trabajo, o una de datos para viajar.
- **Alta inmediata**, sin esperar a que llegue una tarjeta.
- **Cambio de móvil más sencillo**: las versiones recientes de SGP.22 incluyen procedimientos específicos de cambio de dispositivo y recuperación de perfiles.

La próxima vez que escanees un QR para activar una línea, ya sabes que tu móvil acaba de mantener una conversación cifrada con un servidor del operador para instalar tus credenciales en un chip que no podrías sacar aunque quisieras.

### Fuentes

- GSMA, [SGP.22 v3.1, RSP Technical Specification](https://www.gsma.com/esim/wp-content/uploads/2023/12/SGP.22-v3.1.pdf).
- GSMA, [SGP.24 v3.2, requisitos de cumplimiento de SGP.21 y SGP.22](https://www.gsma.com/solutions-and-impact/technologies/esim/wp-content/uploads/2025/01/SGP.24-V3.2.docx).
