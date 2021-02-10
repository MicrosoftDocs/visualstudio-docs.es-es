---
title: Instalación de Dotfuscator Community
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: how-to
keywords: Dotfuscator, Dotfuscator Community, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, protección, community edition, ofuscación, .NET, gratuito, Visual Studio 2017, Visual Studio 2019, Visual Studio, instalación
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator Community
- Dotfuscator
- obfuscation
- protection
- Dotfuscator installer
- Dotfuscator setup
- install Dotfuscator
- installing Dotfuscator
- set up Dotfuscator
description: Aprenda a instalar la copia gratuita de Dotfuscator Community incluida en Visual Studio.
ms.assetid: f2146651-e24a-4e24-ade8-8ddee8ff4e43
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: 9f4ca634aa226437b6d8790837c9f95f778a00c0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924760"
---
# <a name="install-dotfuscator-community"></a>Instalación de Dotfuscator Community

Dotfuscator Community es un componente óptimo de Visual Studio.
En estas instrucciones se explica cómo instalarlo.

> [!NOTE]
> Además de las versiones de Dotfuscator Community incluidas en las versiones de Visual Studio, PreEmptive Solutions también ofrece periódicamente versiones actualizadas en su sitio web.
> Si quiere descargar la **última versión** directamente en lugar de instalarla desde Visual Studio, **[haga clic aquí para ir a la página de descargas de Dotfuscator][download]** .

## <a name="within-visual-studio"></a>En Visual Studio

::: moniker range="vs-2019"

Puede instalar Dotfuscator Community desde el IDE de Visual Studio:

1. En el **cuadro de búsqueda** (Ctrl+Q), escriba `dotfuscator`. <br/> <br/> ![Cuadro de búsqueda](media/install_in_vs19_12.png) <br/> <br/>

2. En los resultados de la búsqueda que aparecen, en el encabezado *Componentes*, seleccione **Install PreEmptive Protection - Dotfuscator** (Instalar PreEmptive Protection - Dotfuscator).
   * Si en lugar de esto ve, bajo el encabezado *Menús*, **PreEmptive Protection - Dotfuscator Community**, significa que Dotfuscator Community ya está instalado. Seleccione esa opción para [comenzar][get-started].

3. Se abrirá una ventana del Instalador de Visual Studio, preconfigurada para la instalación de Dotfuscator Community.
   > [!NOTE]
   > Para continuar tiene que proporcionar credenciales de administrador.

4. En la ventana del instalador de Visual Studio, haga clic en *Instalar*. <br/> <br/> ![Haga clic en Instalar](media/install_in_vs19_34.png) <br/> <br/>

::: moniker-end

::: moniker range="vs-2017"

Puede instalar Dotfuscator Community desde el IDE de Visual Studio:

1. En la barra de búsqueda **Inicio rápido** (CTRL+Q), escriba `dotfuscator`. <br/> <br/> ![Inicio rápido](media/install_from_vs_12.png) <br/> <br/>

2. En Los resultados que aparecen en Inicio rápido, bajo el encabezado *Instalar*, seleccione **PreEmptive Protection - Dotfuscator (Componente Individual)** .
   * Si en lugar de esto ve, bajo el encabezado *Menús*, **Herramientas - PreEmptive Protection - Dotfuscator**, significa que Dotfuscator CE ya está instalado. Seleccione esa opción para [comenzar][get-started].

3. Se abrirá una ventana del Instalador de Visual Studio, preconfigurada para la instalación de Dotfuscator CE.
   > [!NOTE]
   > Para continuar tiene que proporcionar credenciales de administrador.

4. En la ventana del instalador de Visual Studio, haga clic en *Instalar*. <br/> <br/> ![Haga clic en Instalar](media/install_from_vs_345.png) <br/> <br/>

::: moniker-end

Una vez completada la instalación, puede [empezar a usar Dotfuscator Community][get-started].

## <a name="during-visual-studio-installation"></a>Durante la instalación de Visual Studio

Si aún no ha instalado Visual Studio, puede obtener el instalador en el [sitio web de Visual Studio][vs-install].
Al ejecutarlo, se mostrarán las opciones de instalación de la edición de Visual Studio seleccionada.

::: moniker range="vs-2019"

![Opciones de instalación](media/install_ui.png)

::: moniker-end

::: moniker range="vs-2017"

![Opciones de instalación](media/install_ui_17.png)

::: moniker-end

A continuación, puede instalar Dotfuscator Community como componente individual de Visual Studio:

1. Seleccione la pestaña **Componentes individuales**.
2. En *Herramientas de código*, active el elemento *PreEmptive Protection - Dotfuscator*.<br/> <br/> ![Componentes individuales](media/install_individually_12.png) <br/> <br/>
3. El panel *Resumen* muestra *PreEmptive Protection - Dotfuscator* en la sección *Componentes individuales*. <br/> <br/> ![Panel Resumen](media/install_individually_3.png) <br/> <br/>
4. Configure opciones de instalación adicionales según corresponda a su entorno.
5. Cuando esté listo para instalar Visual Studio, haga clic en el botón *Instalar*.

Una vez completada la instalación, puede empezar a usar Dotfuscator Community. Para conocer los detalles, consulte [la página de introducción de la guía de usuario completa de Dotfuscator Community][get-started].

## <a name="see-also"></a>Vea también

[Este tema en la guía de usuario completa de Dotfuscator Community](https://www.preemptive.com/dotfuscator/ce/docs/help/)

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[vs-install]:  https://visualstudio.microsoft.com/downloads/
[get-started]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html

[download]:  https://www.preemptive.com/products/dotfuscator/downloads

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_install.html
