---
title: Funcionalidades de Dotfuscator
ms.date: 10/10/2017
ms.devlang: dotnet
ms.prod: visual-studio-dev15
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, protección, community edition, ofuscación, .NET, gratuito, Visual Studio 2017
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
description: Obtenga información sobre las funcionalidades del producto gratuito Dotfuscator Community Edition incluido en Visual Studio 2017.
ms.assetid: 0ee89c58-c900-48fc-a6a2-65ace00e8bab
author: Joe-Sewell-PreEmptive
ms.author: gewarren
manager: douge
ms.openlocfilehash: f7054eabf20da08bb22df080b0c737222b556483
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53963902"
---
# <a name="capabilities-of-dotfuscator"></a>Funcionalidades de Dotfuscator

Esta página se centra en las funcionalidades de Dotfuscator Community Edition (Dotfuscator CE) con algunas referencias a las opciones avanzadas disponibles a través de [actualizaciones][upgrades].

Dotfuscator es un sistema *posterior a la compilación* para aplicaciones .NET.
Con Dotfuscator CE, los usuarios de Visual Studio pueden [ofuscar ensamblados][obfuscation] e insertar [medidas defensa activa][checks] en la aplicación, todo ello sin que Dotfuscator necesite acceder al código fuente original.
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

Dotfuscator CE puede insertar [código de validación de aplicación][checks] en los ensamblados, incluidas medidas [contra alteraciones][tamper], [contra depuración][debug] y [contra dispositivos con rooting][root].
Cuando se detecta un estado de la aplicación no válido, el código de validación puede [llamar al código de aplicación para que se haga cargo de la situación de forma adecuada][check-app].
O bien, si prefiere no escribir código para tratar el uso no válido de la aplicación, Dotfuscator también puede insertar comportamientos de [respuesta][check-action], sin requerir ninguna modificación en el código fuente.

Muchos de estos métodos también se pueden usar para exigir [fechas límite de final de ciclo de vida][shelflife] para software de evaluación o de prueba.

## <a name="see-also"></a>Vea también

[Este tema en la guía de usuario completa de Dotfuscator CE][full]

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

[assemblies]:  https://docs.microsoft.com/dotnet/standard/assembly-format
[uwp]:  https://www.preemptive.com/blog/article/856-uwp-applications-in-dotfuscator-ce/91-dotfuscator-ce
[xamarin]:  https://www.preemptive.com/obfuscating-xamarin-with-dotfuscator

[upgrades]:  upgrades.md

[obfuscation]:  https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_overview.html
[renaming]:  https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_renaming.html

[checks]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html
[check-app]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html#app-notification
[check-action]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html#action

[tamper]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_tamper.html
[debug]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_debug.html
[root]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_root.html
[shelflife]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_shelflife.html

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_capabilities.html
