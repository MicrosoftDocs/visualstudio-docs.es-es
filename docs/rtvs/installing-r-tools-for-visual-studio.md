---
title: Instalación de las Herramientas de R
description: Se describe cómo instalar las Herramientas de R en Visual Studio 2017 y Visual Studio 2015, incluidas las instalaciones sin conexión.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 676b46c87fe9b6af6e0e1baed0ff5fcdc7e68b6e
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "57873654"
---
# <a name="how-to-install-r-tools-for-visual-studio"></a>Cómo instalar Herramientas de R para Visual Studio

En este artículo:

- [Versiones compatibles de Visual Studio](#supported-versions-of-visual-studio)
- [Instalación de RTVS en Visual Studio 2017](#install-rtvs-in-visual-studio-2017)
- [Instalación de RTVS en Visual Studio 2015](#install-rtvs-in-visual-studio-2015)
- [Instalación sin conexión](#offline-installation-of-visual-studio-and-rtvs)

> [!Note]
> Después de instalar Herramientas de R, es posible que quiera configurar Visual Studio para un diseño científico de datos optimizado, tal y como se explica en el artículo [Opciones](options-for-r-tools-in-visual-studio.md).

## <a name="supported-versions-of-visual-studio"></a>Versiones compatibles de Visual Studio

Herramientas de R para Visual Studio (RTVS) es compatible con Windows con las ediciones Community (gratis), Professional y Enterprise de [Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) y [Visual Studio 2015 Update 3 (o versiones superiores)](http://go.microsoft.com/fwlink/?LinkId=691129) (descarga directa).

RTVS no es compatible actualmente con Visual Studio para Mac.

RTVS no se instalará si solo tiene Visual Studio Shell incluido en productos como Visual Studio Test Professional y SQL Server Management Studio. Visual Studio Shell no tiene los componentes necesarios para RTVS.

## <a name="install-rtvs-in-visual-studio-2017"></a>Instalación de RTVS en Visual Studio 2017

1. Ejecute el instalador de Visual Studio y seleccione la opción **Modificar** (para obtener más información, consulte [Modificar Visual Studio](../install/modify-visual-studio.md)). Si aún no ha instalado Visual Studio, consulte [Instalar Visual Studio](../install/install-visual-studio.md). En Windows 7, asegúrese de que el instalador se actualiza para mostrar la versión de Visual Studio 2017 *15.2 compilación 26430.12* o una versión posterior.

1. Seleccione la carga de trabajo **Aplicaciones de ciencia de datos y de análisis**:

    ![Carga de trabajo Aplicaciones de ciencia de datos y de análisis de VS2017](media/installation-data-science-workload.png)

1. Establezca las opciones adicionales de la derecha debajo del mismo nombre de carga de trabajo. De forma predeterminada, esta carga de trabajo incluye compatibilidad con F# y Python. Para R, los requisitos mínimos son **Compatibilidad con el lenguaje R**, **Compatibilidad de runtime con las herramientas de desarrollo de R** y **Microsoft R Client**.

RTVS se instala en: *%ProgramFiles(x86)%\Microsoft Visual Studio\<versión>\<edición>Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio*, donde *\<versión>* es normalmente `2017` y *\<edición>* es `Community`, `Professional` o `Enterprise`.

## <a name="install-rtvs-in-visual-studio-2015"></a>Instalación de RTVS en Visual Studio 2015

Con Visual Studio 2015, debe instalar un intérprete de R y Herramientas de R por separado.

### <a name="install-an-r-interpreter"></a>Instalar un intérprete de R

RTVS necesita una instalación de 64 bits de R versión 3.2.1 o superior desde uno o varios de los siguientes orígenes:

- [Microsoft R Open](https://mran.microsoft.com/download/)
- [Microsoft R Client](/machine-learning-server/r-client/what-is-microsoft-r-client)
- [CRAN R](https://cran.r-project.org/bin/windows/base/)

Microsoft R Open y CRAN R permiten varias versiones en paralelo. En cambio, Microsoft R Client solo admite una versión y siempre usa la más reciente que haya instalado.

### <a name="install-the-r-tools"></a>Instalar Herramientas de R

Descargue la versión actual de RTVS para Visual Studio 2015 desde [https://aka.ms/rtvs-current](https://aka.ms/rtvs-current). RTVS comprobará si hay una versión adecuada de Visual Studio y le ayudará a instalar un intérprete de R si aún no tiene uno.

> [!Note]
> El instalador independiente de RTVS solo funciona con Visual Studio 2015; para Visual Studio 2017, instale la compatibilidad con R a través de la [carga de trabajo Aplicaciones de ciencia de datos y de análisis](#install-rtvs-in-visual-studio-2017) como se describió antes.

RTVS para Visual Studio 2015 se instala en: `%ProgramFiles(x86)%\Microsoft Visual Studio 14\Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio`

## <a name="offline-installation-of-visual-studio-and-rtvs"></a>Instalación sin conexión de Visual Studio y RTVS

La instalación sin conexión es adecuada para los equipos que no están conectados a Internet:

1. Vaya a [Crear una instalación sin conexión de Visual Studio 2017](../install/create-an-offline-installation-of-visual-studio.md).

1. Si usa Visual Studio 2015, seleccione **2015** en el selector situado encima de la tabla de contenido.

1. Siga las instrucciones de la página web para crear una instalación sin conexión.

1. Para Visual Studio 2015, descargue los instaladores de RTVS sin conexión desde [https://aka.ms/rtvs-current-zip](https://aka.ms/rtvs-current-zip) y [https://aka.ms/rtvs-remote-zip](https://aka.ms/rtvs-remote-zip).

1. Instale Visual Studio y RTVS desde el instalador sin conexión.

## <a name="see-also"></a>Vea también

- [Introducción a R](getting-started-with-r.md)
- [Proyectos de ejemplo de Herramientas de R](getting-started-samples.md)
- [Ayuda de Herramientas de R](getting-started-help.md)
- [Opciones de R Tools](options-for-r-tools-in-visual-studio.md)
- [Microsoft Machine Learning Server (anteriormente R Server)](/machine-learning-server/)