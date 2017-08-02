---
title: "Instalación de Herramientas de R para Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 4/28/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ff60292-1b88-4ee9-b2b2-edd957f1a519
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
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
ms.sourcegitcommit: 90b2481b0ec4f9387fe3a2c0b733a103e8c03845
ms.openlocfilehash: bc0b1112fe6f3acf2605101a863d831f41bb5f6d
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017

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

Herramientas de R para Visual Studio (RTVS) es compatible con las ediciones Community, Professional y Enterprise de [Visual Studio 2015 Update 3 (o superior)](http://go.microsoft.com/fwlink/?LinkId=691129) y [Visual Studio 2017](https://www.visualstudio.com/downloads/). 

RTVS no se instalará si solo tiene Visual Studio Shell incluido en otros productos como Visual Studio Test Professional y SQL Server Management Studio. Esto se debe a que Visual Studio Shell no tiene los componentes necesarios para RTVS.


## <a name="installing-rtvs-in-visual-studio-2017"></a>Instalación de RTVS en Visual Studio 2017

> [!Important]
> La instalación de RTVS en Visual Studio 2017 en Windows 7 de momento está bloqueada, como se explica en el [problema n.º 3561 de GitHub](https://github.com/Microsoft/RTVS/issues/3561). Esto se solucionará en la actualización 15.3 de Visual Studio 2017.

1. Ejecute el instalador de Visual Studio.
2. Seleccione la carga de trabajo **Aplicaciones de ciencia de datos y de análisis**:

    ![Carga de trabajo Aplicaciones de ciencia de datos y de análisis de VS2017](~/docs/rtvs/media/installation-data-science-workload.png)

3. Establezca las opciones adicionales de la derecha debajo del mismo nombre de carga de trabajo. Tenga en cuenta que, de forma predeterminada, esta carga de trabajo incluye compatibilidad con F# y Python. Para R, como mínimo debe seleccionar **Compatibilidad con el lenguaje R**, **Compatibilidad de runtime con las herramientas de desarrollo de R** y **Microsoft R Client**.

RTVS se instala en: `%ProgramFiles(x86)%\Microsoft Visual Studio\<version>\<edition>Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio`, donde `<version>` suele ser `2017` y `<edition>` es `Community`, `Professional` o `Enterprise`.

## <a name="installing-rtvs-in-visual-studio-2015"></a>Instalación de RTVS en Visual Studio 2015

Con Visual Studio 2015, debe instalar un intérprete de R y Herramientas de R por separado.

### <a name="install-an-r-interpreter"></a>Instalar un intérprete de R

RTVS necesita una instalación de 64 bits de R versión 3.2.1 o superior desde uno o varios de los siguientes orígenes:

* [Microsoft R Open](https://mran.microsoft.com/download/)
* [Microsoft R Client](https://msdn.microsoft.com/microsoft-r/r-client-get-started)
* [CRAN R](https://cran.r-project.org/bin/windows/base/)

Microsoft R Open y CRAN R permiten varias versiones en paralelo. Pero Microsoft R Client solo admite una versión y siempre usará la más reciente que haya instalado.

### <a name="install-the-r-tools"></a>Instalar Herramientas de R

Descargue la versión actual de RTVS desde [https://aka.ms/rtvs-current](https://aka.ms/rtvs-current). RTVS comprobará si hay una versión adecuada de Visual Studio y también le ayudará a instalar un intérprete de R si aún no tiene uno.

RTVS se instala en: `%ProgramFiles(x86)%\Microsoft Visual Studio 14\Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio`

## <a name="offline-installation-of-visual-studio-and-rtvs"></a>Instalación sin conexión de Visual Studio y RTVS

La instalación sin conexión es adecuada para los equipos que no están conectados a Internet:

1. Siga las instrucciones para crear un instalador sin conexión para la versión siguiente de Visual Studio. 

    - [Visual Studio 2017](../install/create-an-offline-installation-of-visual-studio.md)
    - [Visual Studio 2015](https://msdn.microsoft.com/library/mt706497.aspx)

1. Instale Visual Studio desde el instalador sin conexión.
1. [Descargue RTVS](https://aka.ms/rtvs-current) e instálelo como de costumbre.

## <a name="see-also"></a>Vea también

- [Introducción a R](getting-started-with-r.md)
- [Proyectos de ejemplo de Herramientas de R](getting-started-samples.md)
- [Ayuda](getting-started-help.md)
- [Option settings (Opciones)](options.md)

