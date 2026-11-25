---
title: "La IA entra en la antena: redes móviles que se optimizan solas"
date: 2026-11-22 18:00:00 +0100
categories: ia-telecom
tags: [ia, ran, 5g, redes-autonomas]
description: "Ericsson ya ofrece modelos de IA que funcionan en tiempo real dentro de la red de acceso radio. Qué hacen, qué tipo de IA usan y cómo encajan en los niveles de red autónoma."
image: /assets/img/posts/ia-ran-portada.svg
image_alt: "Ilustración de una antena de telefonía rodeada por una red neuronal"
image_caption: "Ilustración propia."
---

Durante años, la inteligencia artificial en telecomunicaciones vivía en los centros de operaciones: paneles que detectaban anomalías y recomendaban acciones a un técnico. En 2026 ha dado un salto: los modelos ya se ejecutan **dentro de la propia red de acceso radio**, tomando decisiones en tiempo real. Vemos qué significa y hasta dónde llega.

<!--more-->

## Qué es la RAN y por qué meterle IA

La **RAN** (*Radio Access Network*) es la parte de la red móvil que habla directamente con tu teléfono: antenas y estaciones base. Es donde se decide, continuamente, a qué usuario se le asignan los recursos de radio, con qué modulación se transmite o hacia dónde se orienta el haz de la antena.

Tradicionalmente, esas decisiones las toman algoritmos basados en reglas que los ingenieros ajustan a mano. El problema es que el entorno radio cambia constantemente: gente que se mueve, edificios, interferencias, picos de tráfico. Ahí es donde un modelo que aprende de los datos de la propia red puede hacerlo mejor.

## Lo que ha lanzado Ericsson

En junio de 2026, Ericsson presentó **AI in RAN**, un paquete de software con [modelos de IA diseñados para ejecutarse en tiempo real dentro de la RAN](https://www.ericsson.com/en/news/2026/6/the-ran-gets-smarter-ericsson-puts-ai-where-it-matters). Las primeras funciones llegaron en el segundo trimestre de 2026 y el resto se completa a lo largo del año. Entre ellas:

- Un **planificador con adaptación de enlace nativa de IA**, que decide cómo transmitir a cada usuario.
- **Posicionamiento** de dispositivos basado en IA.
- **Conformación de haz** (*beamforming*) controlada por IA.
- **Coordinación entre capas** de la red basada en IA.

Dos detalles llaman la atención. Primero, según [RCR Wireless](https://www.rcrwireless.com/20260616/ai/ericsson-ai-in-ran), no hace falta instalar GPUs de centro de datos: los modelos se activan sobre hardware de la red que ya está preparado para IA. Segundo, los modelos **siguen aprendiendo** con los datos que genera la propia red, en lugar de quedarse congelados tras el despliegue. Clientes como SoftBank, SK Telecom y Bell Canada [valoran positivamente los resultados](https://www.telecomtv.com/content/ai/ericsson-embeds-ai-in-its-ran-55663/).

## Qué tipo de IA se usa

No toda la IA de la RAN es igual. Ericsson lo resume en [su blog](https://www.ericsson.com/en/blog/2026/4/embedding-ai-in-ran): habrá desde algoritmos de **aprendizaje supervisado** sencillos, como árboles de decisión para mejorar la precisión de la localización, hasta **aprendizaje por refuerzo** profundo para optimizar el planificador.

El aprendizaje por refuerzo funciona como un jugador que aprende probando: un agente toma una decisión, observa el resultado y recibe una «recompensa» si la red mejora. A base de repetir, aprende qué acciones funcionan mejor en cada situación.

La dificultad es el tiempo. Algunas de estas decisiones deben tomarse en **microsegundos**, tan rápido que la propia Ericsson titula uno de sus artículos técnicos [«Cuando la IA no tiene tiempo para pensar»](https://www.ericsson.com/495c7d/assets/local/reports-papers/ericsson-technology-review/docs/2026/when-ai-has-no-time-to-think.pdf). Por eso los modelos deben ser pequeños y eficientes, y ejecutarse junto al equipo de radio.

## El objetivo final: la red autónoma

Todo esto forma parte de un camino más largo: la **red autónoma**, capaz de operarse a sí misma. El TM Forum, la asociación que agrupa a operadores y fabricantes, define seis niveles, del 0 (todo manual) al 5 (totalmente autónoma en cualquier escenario).

![Escalera con los seis niveles de red autónoma del TM Forum, de L0 manual a L5 totalmente autónoma]({{ "/assets/img/posts/niveles-red-autonoma.svg" | relative_url }})
*Niveles de red autónoma según el TM Forum. Diagrama propio.*

En cada nivel, el sistema asume más fases del ciclo de operación: primero ejecuta lo que le dicen, luego detecta, después analiza, decide y, al final, entiende directamente la intención del operador («garantiza esta calidad en este estadio») sin que nadie le diga cómo hacerlo. El TM Forum ya [mide y certifica el nivel que alcanza cada operador](https://rcrwireless.com/20260519/carriers/road-to-level-4-point-solutions-wall-to-wall-autonomy-tm-forum), y, según Cisco, el primer objetivo de los operadores debería ser cerrar bucles de automatización en dominios concretos, como la RAN o el núcleo, [en línea con el nivel 3](https://www.cisco.com/c/en/us/solutions/collateral/networking/auton-ntwk-sp-wp.html).

## Mi lectura

Meter la IA dentro de la antena es un cambio de fondo: la IA deja de ser una herramienta que asesora a las personas y pasa a ser **parte del propio equipo de red**. Las preguntas que quedan abiertas son las de siempre en sistemas críticos: cómo se valida un modelo que sigue aprendiendo, cómo se explica una decisión cuando algo falla y quién tiene la última palabra. De cómo se respondan dependerá la velocidad a la que subamos por esa escalera.

### Fuentes

- Ericsson, [The RAN gets smarter: Ericsson puts AI where it matters](https://www.ericsson.com/en/news/2026/6/the-ran-gets-smarter-ericsson-puts-ai-where-it-matters) (11/06/2026).
- Ericsson, [Embedding AI in RAN](https://www.ericsson.com/en/blog/2026/4/embedding-ai-in-ran) (abril de 2026).
- RCR Wireless, [Ericsson puts AI inside the radio with its new software-only AI in RAN suite](https://www.rcrwireless.com/20260616/ai/ericsson-ai-in-ran) (16/06/2026).
- TelecomTV, [Ericsson embeds AI in its RAN](https://www.telecomtv.com/content/ai/ericsson-embeds-ai-in-its-ran-55663/) (11/06/2026).
- RCR Wireless, [The road to Level 4](https://rcrwireless.com/20260519/carriers/road-to-level-4-point-solutions-wall-to-wall-autonomy-tm-forum) (19/05/2026).
- Cisco, [Autonomous Networks for Service Providers White Paper](https://www.cisco.com/c/en/us/solutions/collateral/networking/auton-ntwk-sp-wp.html).
