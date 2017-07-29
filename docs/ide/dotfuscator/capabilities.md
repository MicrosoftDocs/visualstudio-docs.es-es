---
title: Funcionalidades de Dotfuscator | Microsoft Docs
ms.date: 2017-06-22
ms.prod: visual-studio-dev15
ms.devlang: dotnet
ms.technology:
- dotfuscator
ms.topic: article
keywords: "Dotfuscator, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, protección, community edition, ofuscación, .NET, gratuito, Visual Studio 2017"
helpviewer_keywords:
- PreEmptive Protection - Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
description: "Obtenga información sobre las funcionalidades del producto gratuito Dotfuscator Community Edition incluido en Visual Studio 2017."
ms.assetid: 0ee89c58-c900-48fc-a6a2-65ace00e8bab
author: Joe-Sewell-PreEmptive
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 8ce85525f6af336682f6f8547c2f6c13dde73c8c
ms.openlocfilehash: 9193020b9031b5e1a5637fd4ec207d0449ec85ae
ms.contentlocale: es-es
ms.lasthandoff: 06/23/2017

---

# <a name="capabilities-of-dotfuscator"></a>Funcionalidades de Dotfuscator

Esta página se centra en las funcionalidades de Dotfuscator Community Edition (Dotfuscator CE) con algunas referencias a las opciones avanzadas disponibles a través de [actualizaciones][upgrades].

Dotfuscator es un sistema *posterior a la compilación* para aplicaciones .NET.
Con Dotfuscator CE, los usuarios de Visual Studio pueden [ofuscar ensamblados][obfuscation] e insertar [defensa activa][checks] y [seguimiento de análisis][analytics] en la aplicación, todo ello sin que Dotfuscator necesite acceder al código fuente original.
Dotfuscator protege la aplicación de varias formas, creando una estrategia de protección por capas.

Dotfuscator CE admite una gran variedad de tipos de aplicaciones y ensamblados de .NET, incluidos la [Plataforma universal de Windows (UWP)][uwp] y [Xamarin][xamarin].

## <a name="intellectual-property-protection"></a>Protección de la propiedad intelectual

El diseño, el comportamiento y la implementación de la aplicación son formas de propiedad intelectual (PI).
En cambio, las aplicaciones creadas para .NET Framework son prácticamente libros abiertos; es muy fácil usar técnicas de ingeniería inversa en los ensamblados de .NET, [ya que contienen metadatos de alto nivel y código intermedio][assemblies].

Dotfuscator CE incluye [ofuscación de .NET][obfuscation] básica en forma de [cambio de nombre][renaming].
Ofuscar el código con Dotfuscator reduce el riesgo de acceso no autorizado al código fuente a través de técnicas de ingeniería inversa, ya que la información importante de nomenclatura ya no será pública.
La ofuscación también muestra esfuerzo por su parte para proteger el código de exámenes, un paso valioso para establecer que la PI está protegida legalmente como secreto comercial.

Muchas de las [características de protección de integridad de aplicación](#application-integrity-protection) de Dotfuscator CE dificultan aún más el uso de técnicas de ingeniería inversa.
Por ejemplo, un actor perjudicial puede intentar adjuntar un depurador a una instancia en ejecución de la aplicación para comprender la lógica del programa.
Dotfuscator puede insertar un [comportamiento contra depuración][debug] en la aplicación para impedirlo.

## <a name="application-integrity-protection"></a>Protección de la integridad de la aplicación

Además de proteger el código fuente, también es importante asegurarse de que la aplicación se usa como se ha diseñado.
Los atacantes pueden intentar atacar la aplicación para evitar directivas de licencia (es decir, piratería de software), robar o manipular datos confidenciales controlados por la aplicación, o para cambiar su comportamiento.

Dotfuscator CE puede insertar [código de validación de aplicación][checks] en los ensamblados, incluidas medidas [contra alteraciones][tamper] y [contra depuración][debug].
Cuando se detecta un estado de la aplicación no válido, el código de validación puede [llamar al código de aplicación para que se haga cargo de la situación de forma adecuada][check-app].
O bien, si prefiere no escribir código para tratar el uso no válido de la aplicación, Dotfuscator también puede insertar comportamientos de [creación de informes de telemetría][check-telemetry] y [respuesta][check-action], sin requerir ninguna modificación en el código fuente.

Muchos de estos métodos también se pueden usar para exigir [fechas límite de final de ciclo de vida][shelflife] para software de evaluación o de prueba.

## <a name="application-monitoring"></a>Supervisión de aplicaciones

Al desarrollar una aplicación, es fundamental comprender los patrones de comportamiento de los usuarios, incluidos los evaluadores de la versión beta y los usuarios de versiones anteriores.
El análisis de la aplicación le permite realizar un seguimiento de la frecuencia con la que se usa la aplicación y cómo se usa, incluidos los errores que experimentan los clientes.

Dotfuscator CE puede insertar código de [seguimiento de excepciones][exceptions], [seguimiento de sesión][sessions] y [seguimiento de características][features] en la aplicación.
Cuando se ejecuta, la aplicación procesada transmite datos de análisis a un [punto de conexión configurado de PreEmptive Analytics][endpoints].

## <a name="see-also"></a>Vea también

[Este tema en la guía de usuario completa de Dotfuscator CE][full]

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

[assemblies]: https://docs.microsoft.com/en-us/dotnet/standard/assembly-format
[uwp]: https://www.preemptive.com/blog/article/856-uwp-applications-in-dotfuscator-ce/91-dotfuscator-ce
[xamarin]: https://www.preemptive.com/obfuscating-xamarin-with-dotfuscator

[upgrades]: upgrades.md

[obfuscation]: https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_overview.html
[renaming]: https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_renaming.html

[analytics]: https://www.preemptive.com/dotfuscator/ce/docs/help/analytics_overview.html
[endpoints]: https://www.preemptive.com/dotfuscator/ce/docs/help/analytics_overview.html#endpoints

[checks]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html
[check-app]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html#app-notification
[check-action]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html#action

[tamper]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_tamper.html
[debug]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_debug.html
[shelflife]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_shelflife.html
[exceptions]: https://www.preemptive.com/dotfuscator/ce/docs/help/analytics_exceptions.html
[sessions]: https://www.preemptive.com/dotfuscator/ce/docs/help/analytics_sessions.html
[features]: https://www.preemptive.com/dotfuscator/ce/docs/help/analytics_features.html
[check-telemetry]: https://www.preemptive.com/dotfuscator/ce/docs/help/analytics_checks.html

[full]: https://www.preemptive.com/dotfuscator/ce/docs/help/intro_capabilities.html

