---
title: Dotfuscator Community Edition (CE)
ms.date: 10/10/2017
ms.devlang: dotnet
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, protección, community edition, ofuscación, .NET, gratuito, Visual Studio 2017
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
description: Obtenga información acerca de cómo proteger las aplicaciones de .NET con la solución Dotfuscator Community Edition gratuita que se incluye en Visual Studio 2017.
ms.assetid: d9550502-0a82-49a6-b005-2caa791fbe02
author: Joe-Sewell-PreEmptive
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 85f4a28e7f0fd3e7d723aa918dce3761b90d3869
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55937528"
---
# <a name="dotfuscator-community-edition-ce"></a>Dotfuscator Community Edition (CE)

*PreEmptive Protection – Dotfuscator* proporciona una protección integral para aplicaciones .NET que se adapta fácilmente a su ciclo de desarrollo de software seguro.
Se utiliza para consolidar, proteger y eliminar aplicaciones de escritorio, móviles, de servidor e insertadas a fin de ayudar a salvaguardar secretos comerciales y propiedad intelectual de otra índole, reducir la piratería y la falsificación y proteger contra la manipulación y la depuración no autorizada.
Dotfuscator funciona en ensamblados compilados sin necesidad de programación adicional ni de obtener acceso al código fuente.

![PreEmptive Protection - Dotfuscator](media/header.svg)

## <a name="why-protection-matters"></a>Por qué es importante la protección

Es importante **proteger su propiedad intelectual**.
El código de su aplicación contiene detalles de diseño e implementación que se pueden considerar propiedad intelectual.
Sin embargo, las aplicaciones que se basan en .NET Framework [contienen metadatos importantes y código intermedio de alto nivel][assemblies], con lo que quedan expuestas a la utilización de técnicas de ingeniería inversa mediante el uso de alguna de las muchas herramientas gratuitas y automatizadas que existen.
Al interrumpir y detener la utilización de técnicas de ingeniería inversa, se puede evitar la divulgación no autorizada de la propiedad intelectual, así como demostrar que el código contiene secretos comerciales.
Dotfuscator puede [ofuscar][obfuscation] los ensamblados de .NET para obstaculizar la utilización de técnicas de ingeniería inversa, manteniendo el comportamiento de la aplicación original.

También es importante **proteger la integridad de la aplicación**.
Además de técnicas de ingeniería inversa, los actores malintencionados pueden tratar de piratear su aplicación, modificar su comportamiento en tiempo de ejecución o manipular los datos.
Dotfuscator puede dotar a su aplicación de la capacidad de [detectar y responder a usos no autorizados][checks], incluidos los casos de manipulación, depuración de terceros y dispositivos con privilegios de usuario root.

Para obtener más información acerca de cómo Dotfuscator se ajusta a un ciclo de vida de desarrollo de software seguro, consulte la [página de protección de aplicaciones de SDL][sdl-protection] de PreEmptive Solutions.

## <a name="about-dotfuscator-ce"></a>Acerca de Dotfuscator CE

Su copia de Microsoft Visual Studio 2017 incluye una copia gratuita de **_PreEmptive Protection - Dotfuscator_ Community Edition**, también conocido como Dotfuscator CE, para su uso personal.
Para obtener instrucciones sobre cómo instalar la versión de Dotfuscator CE incluida con Visual Studio 2017, consulte la [página de instalación][install].

Dotfuscator CE ofrece una gama de servicios de [consolidación y protección de software][software-protection] para desarrolladores, arquitectos y evaluadores.
A continuación se presentan algunos ejemplos de [ofuscación de .NET][obfuscation] y otras características de [protección de aplicaciones][app-protection] incluidas en Dotfuscator CE:

* *[Cambio del nombre][renaming]* de los identificadores para dificultar la utilización de técnicas de ingeniería inversa en los ensamblados compilados.
* *[Antimanipulación][tamper]* para detectar la ejecución de aplicaciones alteradas y finalizar o responder a sesiones alteradas.
* *[Antidepuración][debug]* para detectar cuando se adjunta un depurador a una aplicación en ejecución y finalizar o responder a sesiones depuradas.
* *[Dispositivo protegido contra la obtención de privilegios de usuario root][root]* para detectar si la aplicación se está ejecutando en un dispositivo Android con dichos privilegios y finalizar o responder a las sesiones en dispositivos de este tipo.
* *[Comportamientos de expiración de aplicaciones][shelflife]* que codifican una fecha de fin de ciclo de vida y finalizan sesiones de aplicación expiradas.

Para obtener información acerca de estas características, incluyendo cómo encajan en su estrategia de protección de aplicaciones, consulte la [página de funcionalidades][capabilities].

Dotfuscator CE ofrece protección básica inmediata.
Pero hay más medidas de protección para aplicaciones disponibles para los usuarios registrados de Dotfuscator CE, y para los usuarios de*PreEmptive Protection - Dotfuscator* Professional Edition, el [ofuscador de .NET][net-obfuscator] líder en el mundo.
Para obtener información sobre cómo mejorar Dotfuscator, consulte la [página de actualizaciones][upgrades].

## <a name="getting-started"></a>Introducción

Para comenzar a usar Dotfuscator CE desde Visual Studio, escriba `dotfuscator` en la barra de búsqueda de **inicio rápido** (Ctrl+Q).

* Si ya está instalado Dotfuscator CE, **inicio rápido** abrirá la opción de *menú* para iniciar la interfaz de usuario de Dotfuscator CE. Para obtener detalles, vea [la página de introducción de la guía de usuario completa de Dotfuscator CE][get-started].
* Si Dotfuscator CE aún no está instalado, **inicio rápido** abrirá la correspondiente opción de *instalación*. Consulte la [página de instalación][install] para obtener más información.

También puede obtener la **versión más reciente** de Dotfuscator CE en [la página de descargas de Dotfuscator en preemptive.com][download].

## <a name="full-documentation"></a>Documentación completa

Esta página y sus páginas secundarias proporcionan una descripción general de alto nivel de las características de Dotfuscator CE, así como [instrucciones para instalar la herramienta][install].

Vea [la guía de usuario completa de Dotfuscator CE en preemptive.com][full] para obtener instrucciones detalladas de uso; por ejemplo, [cómo empezar a usar la interfaz de usuario de Dotfuscator CE][get-started].

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

[assemblies]:  https://docs.microsoft.com/dotnet/standard/assembly-format
[software-protection]:  https://www.preemptive.com/software-protection
[obfuscation]:  https://www.preemptive.com/obfuscation
[app-protection]:  https://www.preemptive.com/application-protection
[sdl-protection]:  https://www.preemptive.com/solutions/SDL-App-Protection
[net-obfuscator]:  https://www.preemptive.com/products/dotfuscator/overview
[download]:  https://www.preemptive.com/products/dotfuscator/downloads

[install]:  install.md
[capabilities]:  capabilities.md
[upgrades]:  upgrades.md

[get-started]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html

[renaming]:  https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_renaming.html

[checks]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html
[tamper]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_tamper.html
[debug]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_debug.html
[root]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_root.html
[shelflife]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_shelflife.html

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/index.html
