---
title: Desinstalación de Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
f1_keywords:
- uninstalling
- uninstalling visual studio
- uninstall
- uninstall Visual Studio
ms.assetid: 0e445255-b796-426d-ad93-a4d8e36da2c5
caps.latest.revision: 9
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: e00ca9212c03d4123259715da157201c06d90f2b
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/17/2019
ms.locfileid: "59667305"
---
# <a name="uninstall-visual-studio"></a>Desinstalar Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para obtener la documentación más reciente de Visual Studio, consulte [Desinstalar Visual Studio](/visualstudio/install/uninstall-visual-studio).

Esta página le guía a través de la desinstalación de Visual Studio 2015, una versión anterior de nuestro conjunto integrado de herramientas de productividad para desarrolladores.

## <a name="uninstall-visual-studio-by-using-the-standard-uninstallation-method"></a>Desinstalación de Visual Studio mediante el método de desinstalación "estándar"

1. En el **Panel de control**, en la página **Programas y características**, elija la edición del producto que quiera desinstalar y, a continuación, elija **Cambiar**.

2. En el Asistente para la instalación, elija **Desinstalar**, elija **Sí** y siga las instrucciones restantes del asistente.

   Este método estándar o predeterminado dejará algunos elementos de la instalación original de Visual Studio (por ejemplo, Microsoft .NET Framework, Microsoft Visual C++ Redistributables, Microsoft SQL Server, etc.).   Estos elementos se dejan instalados porque muchas otras aplicaciones dependen de ellos. Sin embargo, si también desea eliminarlos, seleccione su entrada en **Programas y características** y luego elimine cada uno individualmente.

## <a name="uninstall-visual-studio-and-all-other-related-files-that-is-to-uninstall-almost-everything"></a>Desinstalación de Visual Studio y otros archivos relacionados (es decir, desinstalarlo casi todo)

1.  Busque el archivo .exe de Visual Studio (por ejemplo, "vs_enterprise.exe").

    > [!NOTE]
    > El archivo debe estar en una subcarpeta de "%ProgramData%\Package Cache"; por ejemplo: C:\ProgramData\Package Cache\\{37e19555-e88d-4aed-9d42-82d0784d2b79}\vs_enterprise.exe

2.  Ejecute el archivo .exe utilizando los parámetros de la línea de comandos /uninstall /force.

     Por ejemplo, ejecute ```vs_enterprise.exe /uninstall /force```, que quitará Visual Studio y la mayoría de los componentes principales que quedan en una desinstalación predeterminada. Sin embargo, no quitará todo el contenido adicional que los complementos y extensiones de Visual Studio pueden instalar (por ejemplo, actualizaciones de Visual Studio y otros componentes opcionales).

    > [!TIP]
    > Como alternativa, puede usar la herramienta "**Total Uninstaller**" para quitar todo lo que Visual Studio o sus actualizaciones pueden haber instalado. Es decir, cualquier versión de Visual Studio 2013 o posterior. Para obtener más información, consulte la [herramienta de desinstalación de Visual Studio](https://github.com/Microsoft/VisualStudioUninstaller/releases) en GitHub.

## <a name="uninstall-visual-studio-in-silent-or-passive-modes-that-is-to-uninstall-from-source"></a>Desinstalación de Visual Studio en los modos silencioso o pasivo (es decir, desinstalar desde el origen)

1.  En el equipo donde está instalado Visual Studio, abra el símbolo del sistema de Windows.

2.  Escriba los parámetros siguientes:

     *DVDRoot* \\<Archivo de instalación\> \</quiet&#124;/passive> [/norestart]/uninstall

## <a name="roll-back-to-a-previous-version-or-release-of--visual-studio"></a>Reversión a una versión anterior o una versión de Visual Studio

1. Desinstale Visual Studio con cualquiera de los métodos descritos en este tema.

   > [!WARNING]
   > La desinstalación de una versión actual de Visual Studio (o una actualización de Visual Studio) y la instalación posterior de una versión anterior podría no funcionar como se esperaba.
   >
   > El resultado depende de qué versión de Visual Studio haya instalado, qué versiones de sus componentes están instaladas, qué productos están instalados que podrían tener dependencias de la versión de Visual Studio o sus componentes y, finalmente, en qué versión anterior de Visual Studio planea instalar o reinstalar.  Debido a todas estas variables, una desinstalación estándar a menudo deja componentes que podrían no funcionar con versiones anteriores de Visual Studio.
   >
   > Por lo tanto, para obtener mejores resultados, se recomienda usar la [herramienta de desinstalación de Visual Studio](https://github.com/Microsoft/VisualStudioUninstaller/releases).

2. Instale o reinstale la versión anterior de Visual Studio que desea usar.

   Incluso si instala una versión anterior de Visual Studio, es posible que el programa de instalación intente utilizar una versión más reciente, si está disponible. Para obtener información más detallada, vea [Cómo: Instalar una versión específica de Visual Studio](../install/how-to-install-a-specific-release-of-visual-studio.md).

## <a name="see-also"></a>Vea también

- [Instalar Visual Studio](https://msdn.microsoft.com/library/e2h7fzkw.aspx)