---
title: "Instalación de Herramientas de R para Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 6/29/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.devlang: r
ms.topic: article
ms.assetid: 3ff60292-1b88-4ee9-b2b2-edd957f1a519
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 712cc780388acc5e373f71d51fc8f1f42adb5bed
ms.openlocfilehash: 8e35c82a5f8583a609e9fccbacb0b27d9c3eac8f
ms.contentlocale: es-es
ms.lasthandoff: 07/12/2017

---

# <a name="how-to-install-r-tools-for-visual-studio"></a>Cómo instalar Herramientas de R para Visual Studio

En este tema:

- [Versiones compatibles de Visual Studio](#supported-versions-of-visual-studio)
- [Instalación de RTVS en Visual Studio 2017](#installing-rtvs-in-visual-studio-2017)
- [Instalación de RTVS en Visual Studio 2015](#installing-rtvs-in-visual-studio-2015)
- [Instalación sin conexión](#offline-installation-of-visual-studio-and-rtvs)

> [!Note]
> Después de instalar Herramientas de R, es posible que quiera configurar Visual Studio para un diseño científico de datos optimizado, como se explica en el tema [Opciones](options.md#data-scientist-layout).

## <a name="supported-versions-of-visual-studio"></a>Versiones compatibles de Visual Studio

Herramientas de R para Visual Studio (RTVS) es compatible con las ediciones Community (gratis), Professional y Enterprise de [Visual Studio 2017](https://www.visualstudio.com/downloads/) y [Visual Studio 2015 Update 3 (o versiones superiores)](http://go.microsoft.com/fwlink/?LinkId=691129) (descarga directa). 

RTVS no se instalará si solo tiene Visual Studio Shell incluido en productos como Visual Studio Test Professional y SQL Server Management Studio. Visual Studio Shell no tiene los componentes necesarios para RTVS.


## <a name="installing-rtvs-in-visual-studio-2017"></a>Instalación de RTVS en Visual Studio 2017

1. Ejecute el instalador de Visual Studio. (Consulte [Descargas](https://www.visualstudio.com/downloads/) si aún no tiene instalado Visual Studio). En Windows 7, asegúrese de que el instalador se actualiza para mostrar la versión de Visual Studio *15.2 compilación 26430.12* o una versión posterior.

2. Seleccione la carga de trabajo **Aplicaciones de ciencia de datos y de análisis**:

    ![Carga de trabajo Aplicaciones de ciencia de datos y de análisis de VS2017](media/installation-data-science-workload.png)

3. Establezca las opciones adicionales de la derecha debajo del mismo nombre de carga de trabajo. De forma predeterminada, esta carga de trabajo incluye compatibilidad con F# y Python. Para R, los requisitos mínimos son **Compatibilidad con el lenguaje R**, **Compatibilidad de runtime con las herramientas de desarrollo de R** y **Microsoft R Client**.

RTVS se instala en: `%ProgramFiles(x86)%\Microsoft Visual Studio\<version>\<edition>Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio`, donde `<version>` suele ser `2017` y `<edition>` es `Community`, `Professional` o `Enterprise`.

## <a name="installing-rtvs-in-visual-studio-2015"></a>Instalación de RTVS en Visual Studio 2015

Con Visual Studio 2015, debe instalar un intérprete de R y Herramientas de R por separado.

### <a name="install-an-r-interpreter"></a>Instalar un intérprete de R

RTVS necesita una instalación de 64 bits de R versión 3.2.1 o superior desde uno o varios de los siguientes orígenes:

* [Microsoft R Open](https://mran.microsoft.com/download/)
* [Microsoft R Client](https://msdn.microsoft.com/microsoft-r/r-client-get-started)
* [CRAN R](https://cran.r-project.org/bin/windows/base/)

Microsoft R Open y CRAN R permiten varias versiones en paralelo. En cambio, Microsoft R Client solo admite una versión y siempre usa la más reciente que haya instalado.

### <a name="install-the-r-tools"></a>Instalar Herramientas de R

Descargue la versión actual de RTVS desde [https://aka.ms/rtvs-current](https://aka.ms/rtvs-current). RTVS comprobará si hay una versión adecuada de Visual Studio y le ayudará a instalar un intérprete de R si aún no tiene uno.

RTVS se instala en: `%ProgramFiles(x86)%\Microsoft Visual Studio 14\Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio`

## <a name="offline-installation-of-visual-studio-and-rtvs"></a>Instalación sin conexión de Visual Studio y RTVS

La instalación sin conexión es adecuada para los equipos que no están conectados a Internet:

1. Siga las instrucciones para crear un instalador sin conexión para la versión siguiente de Visual Studio: 

    - [Visual Studio 2017](../install/create-an-offline-installation-of-visual-studio.md)
    - [Visual Studio 2015](https://msdn.microsoft.com/library/mt706497.aspx)

1. Descargue los instaladores de RTVS sin conexión de [https://aka.ms/rtvs-current-zip](https://aka.ms/rtvs-current-zip) y [https://aka.ms/rtvs-remote-zip](https://aka.ms/rtvs-remote-zip). 

1. Instale Visual Studio y RTVS desde el instalador sin conexión.

## <a name="see-also"></a>Vea también

- [Introducción a R](getting-started-with-r.md)
- [Proyectos de ejemplo de Herramientas de R](getting-started-samples.md)
- [Ayuda](getting-started-help.md)
- [Option settings (Opciones)](options.md)

