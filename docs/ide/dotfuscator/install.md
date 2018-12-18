---
title: Instalar Dotfuscator Community Edition (CE)
ms.date: 06/22/2017
ms.devlang: dotnet
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, protección, community edition, ofuscación, .NET, gratuito, Visual Studio 2017, instalar
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
- Dotfuscator installer
- Dotfuscator setup
- install Dotfuscator
- installing Dotfuscator
- set up Dotfuscator
description: Aprenda a instalar el producto gratuito Dotfuscator Community Edition incluido en Visual Studio de 2017.
ms.assetid: f2146651-e24a-4e24-ade8-8ddee8ff4e43
author: Joe-Sewell-PreEmptive
ms.author: gewarren
manager: douge
ms.openlocfilehash: d513588a7d00e874b38306150f896157906e2733
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49880369"
---
# <a name="install-dotfuscator-community-edition-ce"></a>Instalar Dotfuscator Community Edition (CE)

Visual Studio 2017 emplea una nueva experiencia de instalación de bajo impacto.
Por ello, Dotfuscator Community Edition (Dotfuscator CE) no se instala de forma predeterminada.
Pero instalar Dotfuscator CE es sencillo, aunque ya haya instalado Visual Studio.

> [!NOTE]
> Además de las versiones de Dotfuscator CE incluidas en las versiones de Visual Studio, PreEmptive Solutions también ofrece periódicamente versiones actualizadas en su sitio web.
> Si quiere descargar la **última versión** directamente en lugar de instalarla desde Visual Studio, **[haga clic aquí para ir a la página de descargas de Dotfuscator][download]**.

## <a name="within-visual-studio"></a>En Visual Studio

Puede instalar Dotfuscator CE desde el IDE de Visual Studio:

1. En la barra de búsqueda **Inicio rápido** (CTRL+Q), escriba `dotfuscator`. <br/> <br/> ![Inicio rápido](media/install_from_vs_12.png) <br/> <br/>
2. En Los resultados que aparecen en Inicio rápido, bajo el encabezado *Instalar*, seleccione **PreEmptive Protection - Dotfuscator (Componente Individual)**.
   * Si en lugar de esto ve, bajo el encabezado *Menús*, **Herramientas - PreEmptive Protection - Dotfuscator**, significa que Dotfuscator CE ya está instalado. Para obtener detalles de uso, vea [la página de introducción de la guía de usuario completa de Dotfuscator CE][get-started].
3. Se abrirá una ventana del instalador de Visual Studio preconfigurada para la instalación de Dotfuscator CE.
   * Para continuar tiene que proporcionar credenciales de administrador.
4. Cierre todas las instancias del IDE de Visual Studio. <br/> <br/> ![Haga clic en Instalar](media/install_from_vs_345.png) <br/> <br/>
5. En la ventana del instalador de Visual Studio, haga clic en *Instalar*.

Una vez completada la instalación, puede empezar a usar Dotfuscator CE. Para obtener detalles, vea [la página de introducción de la guía de usuario completa de Dotfuscator CE][get-started].

## <a name="during-visual-studio-installation"></a>Durante la instalación de Visual Studio

Si aún no ha instalado Visual Studio 2017, puede obtener el instalador en el [sitio web de Visual Studio][2017-install].
Al ejecutarlo, se mostrarán las opciones de instalación de la edición de Visual Studio seleccionada.

![Opciones de instalación](media/install_ui.png)

A continuación, puede instalar Dotfuscator CE como un componente individual de Visual Studio 2017:

1. Seleccione la pestaña **Componentes individuales**.
2. En *Herramientas de código*, active el elemento *PreEmptive Protection - Dotfuscator*.<br/> <br/> ![Componentes individuales](media/install_individually_12.png) <br/> <br/>
3. El panel *Resumen* muestra *PreEmptive Protection - Dotfuscator* en la sección *Componentes individuales*. <br/> <br/> ![Panel Resumen](media/install_individually_3.png) <br/> <br/>
4. Configure opciones de instalación adicionales según corresponda a su entorno.
5. Cuando esté listo para instalar Visual Studio, haga clic en el botón *Instalar*.

Una vez completada la instalación, puede empezar a usar Dotfuscator CE. Para obtener detalles, vea [la página de introducción de la guía de usuario completa de Dotfuscator CE][get-started].

## <a name="see-also"></a>Vea también

[This topic in the full Dotfuscator CE User Guide]: https://www.preemptive.com/dotfuscator/ce/docs/help/

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

[2017-install]:  https://visualstudio.microsoft.com/downloads/#vs-2017
[get-started]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html

[download]:  https://www.preemptive.com/products/dotfuscator/downloads

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_install.html