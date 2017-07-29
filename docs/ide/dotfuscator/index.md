---
title: Dotfuscator Community Edition (CE) | Microsoft Docs
ms.date: 2017-06-22
ms.prod: visual-studio-dev15
ms.devlang: dotnet
ms.technology:
- dotfuscator
ms.topic: article
keywords: Dotfuscator, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, protection, community edition, obfuscation, .NET, free, Visual Studio 2017
helpviewer_keywords:
- PreEmptive Protection - Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
description: "Obtenga información acerca de cómo proteger las aplicaciones de .NET con la solución Dotfuscator Community Edition gratuita que se incluye en Visual Studio 2017."
ms.assetid: d9550502-0a82-49a6-b005-2caa791fbe02
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
ms.openlocfilehash: 15dd6127493b9977732fdb891a086f931e002459
ms.contentlocale: es-es
ms.lasthandoff: 06/23/2017

---

# <a name="dotfuscator-community-edition-ce"></a>Dotfuscator Community Edition (CE)

*PreEmptive Protection – Dotfuscator* proporciona una protección integral para aplicaciones .NET que se adapta fácilmente a su ciclo de desarrollo de software seguro.
Se utiliza para consolidar, proteger y eliminar aplicaciones de escritorio, móviles, de servidor e insertadas a fin de ayudar a salvaguardar secretos comerciales y propiedad intelectual de otra índole, reducir la piratería y la falsificación y proteger contra la manipulación y la depuración no autorizada.
Dotfuscator funciona en ensamblados compilados sin necesidad de programación adicional ni de obtener acceso al código fuente.

![](media/header.svg)

## <a name="why-protection-matters"></a>Por qué es importante la protección

Es importante **proteger su propiedad intelectual**.
El código de su aplicación contiene detalles de diseño e implementación que se pueden considerar propiedad intelectual.
Sin embargo, las aplicaciones que se basan en .NET Framework [contienen metadatos importantes y código intermedio de alto nivel][assemblies], con lo que quedan muy expuestas a la utilización de técnicas de ingeniería inversa mediante el uso de alguna de las muchas herramientas gratuitas y automatizadas que existen.
Al interrumpir y detener la utilización de técnicas de ingeniería inversa, se puede evitar la divulgación no autorizada de la propiedad intelectual, así como demostrar que el código contiene secretos comerciales.
Dotfuscator puede [ofuscar][obfuscation] los ensamblados de .NET para obstaculizar la utilización de técnicas de ingeniería inversa, manteniendo el comportamiento de la aplicación original.

También es importante **proteger la integridad de la aplicación**.
Además de técnicas de ingeniería inversa, los actores malintencionados pueden tratar de piratear su aplicación, modificar su comportamiento en tiempo de ejecución o manipular los datos.
Dotfuscator puede dotar a su aplicación de la capacidad de [detectar, notificar y responder a usos no autorizados][checks], incluidas las manipulaciones y la depuración de terceros.

Para obtener más información acerca de cómo Dotfuscator se ajusta a un ciclo de vida de desarrollo de software seguro, consulte la [página de protección de aplicaciones de SDL][sdl-protection] de PreEmptive Solutions.

## <a name="about-dotfuscator-ce"></a>Acerca de Dotfuscator CE

Su copia de Microsoft Visual Studio 2017 incluye una copia gratuita de ***PreEmptive Protection - Dotfuscator* Community Edition**, también conocido como Dotfuscator CE, para su uso personal.
Para obtener instrucciones sobre cómo instalar la versión de Dotfuscator CE incluida con Visual Studio 2017, consulte la [página de instalación][install].

Dotfuscator CE ofrece una gama de servicios de [consolidación y protección de software] [ software-protection] para desarrolladores, arquitectos y evaluadores.
A continuación se presentan algunos ejemplos de [ofuscación de .NET][obfuscation] y otras características de [protección de aplicaciones][app-protection] incluidas en Dotfuscator CE:

* *[Cambio del nombre][renaming]* de los identificadores para dificultar la utilización de técnicas de ingeniería inversa en los ensamblados compilados.
* *[Antimanipulación][tamper]* para detectar la ejecución de aplicaciones alteradas, transmitir alertas de incidentes y finalizar sesiones alteradas.
* *[Antidepuración][debug]* para detectar cuando se adjunta un depurador a una aplicación en ejecución, transmitir alertas de incidentes y finalizar sesiones depuradas.
* *[Comportamientos de expiración de la aplicación][shelflife]* que codifican una fecha de "final de vida", transmiten alertas cuando las aplicaciones se ejecutan después de su fecha de caducidad y finalizan sesiones de la aplicación caducadas.
* *[Seguimiento de excepciones][exceptions]* para supervisar las excepciones no controladas que se producen dentro de la aplicación.
* Seguimiento de uso de *[sesiones][sessions] y [características][features] para* determinar las aplicaciones que se han ejecutado, las versiones de esas aplicaciones y las características de estas que se han usado.

Para obtener información acerca de estas características, incluyendo cómo encajan en su estrategia de protección de aplicaciones, consulte la [página de funcionalidades][capabilities].

Dotfuscator CE ofrece protección básica inmediata.
Pero hay más medidas de protección para aplicaciones disponibles para los usuarios registrados de Dotfuscator CE, y para los usuarios de*PreEmptive Protection - Dotfuscator* Professional Edition, el [ofuscador de .NET][net-obfuscator] líder en el mundo.
Para obtener información sobre cómo mejorar Dotfuscator, consulte la [página de actualizaciones][upgrades].

## <a name="getting-started"></a>Introducción

Para comenzar a usar Dotfuscator CE desde Visual Studio, escriba `dotfuscator` en la barra de búsqueda de **inicio rápido** (Ctrl+Q).

* Si ya está instalado Dotfuscator CE, se abrirá la opción de *menú* para iniciar la interfaz de usuario de Dotfuscator CE. Para obtener detalles, vea [la página de introducción de la guía de usuario completa de Dotfuscator CE][get-started].
* Si Dotfuscator CE aún no está instalado, se abrirá la correspondiente opción de *instalación*. Consulte la [página de instalación][install] para obtener más información.

También puede obtener la **versión más reciente** de Dotfuscator CE en [la página de descargas de Dotfuscator en preemptive.com][download].

## <a name="full-documentation"></a>Documentación completa

Esta página y sus páginas secundarias proporcionan una descripción general de alto nivel de las características de Dotfuscator CE, así como [instrucciones para instalar la herramienta][install].

Consulte [la guía de usuario completa de Dotfuscator CE en preemptive.com][full] para obtener instrucciones detalladas de uso; por ejemplo, [cómo empezar a usar la interfaz de usuario de Dotfuscator CE][get-started].

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

[assemblies]: https://docs.microsoft.com/en-us/dotnet/standard/assembly-format
[software-protection]: https://www.preemptive.com/software-protection
[obfuscation]: https://www.preemptive.com/obfuscation
[app-protection]: https://www.preemptive.com/application-protection
[sdl-protection]: https://www.preemptive.com/solutions/SDL-App-Protection
[net-obfuscator]: https://www.preemptive.com/products/dotfuscator/overview
[download]: https://www.preemptive.com/products/dotfuscator/downloads

[install]: install.md
[capabilities]: capabilities.md
[upgrades]: upgrades.md

[get-started]: https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html

[renaming]: https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_renaming.html

[checks]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html
[tamper]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_tamper.html
[debug]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_debug.html
[shelflife]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_shelflife.html

[exceptions]: https://www.preemptive.com/dotfuscator/ce/docs/help/analytics_exceptions.html
[sessions]: https://www.preemptive.com/dotfuscator/ce/docs/help/analytics_sessions.html
[features]: https://www.preemptive.com/dotfuscator/ce/docs/help/analytics_features.html

[full]: https://www.preemptive.com/dotfuscator/ce/docs/help/index.html

