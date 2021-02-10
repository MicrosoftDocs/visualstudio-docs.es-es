---
title: Funcionalidades de Dotfuscator
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator Community, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, protección, community edition, ofuscación, .NET, gratuito, Visual Studio 2017, Visual Studio 2019, Visual Studio
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator Community
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
description: Obtenga información sobre las funcionalidades de la copia gratuita de Dotfuscator Community incluida en Visual Studio
ms.assetid: 0ee89c58-c900-48fc-a6a2-65ace00e8bab
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: ad53c99656096fec2393ecbd9f63fbffe1343e9a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924810"
---
# <a name="capabilities-of-dotfuscator"></a>Funcionalidades de Dotfuscator

Esta página se centra en las funcionalidades de Dotfuscator Community con algunas referencias a las opciones avanzadas disponibles a través de [actualizaciones][upgrades].

Dotfuscator Community es un sistema *posterior a la compilación* para aplicaciones .NET.
Con él, los usuarios de Visual Studio pueden [ofuscar ensamblados][obfuscation] e insertar [medidas de defensa activa][checks] en la aplicación, todo ello sin que Dotfuscator necesite acceder al código fuente original.
Dotfuscator protege la aplicación de varias formas, creando una estrategia de protección por capas.

Dotfuscator Community admite una gran variedad de tipos de aplicaciones y ensamblados de .NET, incluidos la [Plataforma universal de Windows (UWP)][uwp] y [Xamarin][xamarin].

## <a name="intellectual-property-protection"></a>Protección de la propiedad intelectual

El diseño, el comportamiento y la implementación de la aplicación son formas de propiedad intelectual (PI).
En cambio, las aplicaciones creadas para .NET son básicamente libros abiertos; es fácil usar técnicas de ingeniería inversa en los ensamblados de .NET, [ya que contienen metadatos de alto nivel y código intermedio][assemblies].

Dotfuscator Community incluye [ofuscación de .NET][obfuscation] básica en forma de [cambio de nombre][renaming].
Ofuscar el código con Dotfuscator reduce el riesgo de acceso no autorizado al código fuente a través de técnicas de ingeniería inversa, ya que la información importante de nomenclatura ya no será pública.
La ofuscación también muestra esfuerzo por su parte para proteger el código de exámenes, un paso valioso para establecer que la PI está protegida legalmente como secreto comercial.

Muchas de las [características de protección de integridad de aplicación](#application-integrity-protection) de Dotfuscator Community dificultan aún más el uso de técnicas de ingeniería inversa.
Por ejemplo, un actor perjudicial puede intentar adjuntar un depurador a una instancia en ejecución de la aplicación para comprender la lógica del programa.
Dotfuscator puede insertar un [comportamiento contra depuración][debug] en la aplicación para impedirlo.

## <a name="application-integrity-protection"></a>Protección de la integridad de la aplicación

Además de proteger el código fuente, también es importante asegurarse de que la aplicación se usa como se ha diseñado.
Los atacantes pueden intentar atacar la aplicación para evitar directivas de licencia (es decir, piratería de software), robar o manipular datos confidenciales controlados por la aplicación, o para cambiar su comportamiento.

Dotfuscator Community puede insertar [código de validación de aplicación][checks] en los ensamblados, incluidas medidas [contra alteraciones][tamper], [contra depuración][debug] y [contra dispositivos con rooting][root].
Cuando se detecta un estado de la aplicación no válido, el código de validación puede [llamar al código de aplicación para que se haga cargo de la situación de forma adecuada][check-app].
O bien, si prefiere no escribir código para tratar el uso no válido de la aplicación, Dotfuscator también puede insertar comportamientos de [respuesta][check-action], sin requerir ninguna modificación en el código fuente.

Muchos de estos métodos también se pueden usar para exigir [fechas límite de final de ciclo de vida][shelflife] para software de evaluación o de prueba.

## <a name="see-also"></a>Vea también

[Este tema en la guía de usuario completa de Dotfuscator Community][full]

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[assemblies]:  /dotnet/standard/assembly-format
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
