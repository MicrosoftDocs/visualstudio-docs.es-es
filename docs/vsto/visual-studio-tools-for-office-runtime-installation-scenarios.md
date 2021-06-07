---
title: Visual Studio Tools escenarios de instalación en tiempo de ejecución de Office
description: Obtenga información sobre cómo instalar el entorno de ejecución Visual Studio 2010 Tools for Office. En este artículo se describen tres escenarios de instalación.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio Tools for Office runtime, installation scenarios
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 671d8e929ebef1085f0bf2aedad2a3280c36514c
ms.sourcegitcommit: f430d014f912aa7874e1db65026dc72688b973e4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2021
ms.locfileid: "111448342"
---
# <a name="visual-studio-tools-for-office-runtime-installation-scenarios"></a>Visual Studio Tools escenarios de instalación en tiempo de ejecución de Office

  Puede instalar el entorno de Visual Studio 2010 Tools for Office en tiempo de ejecución de tres maneras:

- Al instalar Visual Studio.

- Al instalar Microsoft Office.

- Al instalar la versión Visual Studio 2010 Tools for Office runtime redistribuible.

  Los componentes del runtime que se instalan dependen de la configuración del equipo y el escenario de instalación.

## <a name="runtime-components-that-are-installed-in-each-installation-scenario"></a>Componentes en tiempo de ejecución que se instalan en cada escenario de instalación

 El runtime Visual Studio 2010 Tools for Office tiene tres componentes: el cargador de soluciones de Office, las extensiones de Office para .NET Framework 3.5 y las extensiones de Office para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] versiones posteriores. Cuando se instala el runtime, se instala siempre el cargador de solución de Office. La instalación de las extensiones de Office para .NET Framework depende de la configuración del equipo y el escenario de instalación. Si no se puede instalar alguna de las extensiones de Office al instalar por primera vez el runtime, el runtime instalará automáticamente las extensiones de Office que faltan más adelante, cuando se cumplan ciertos requisitos. Esta característica del runtime se denomina *instalar a petición.*

 La siguiente tabla muestra los componentes del runtime que se instalan de forma predeterminada en cada escenario de instalación del runtime. Podrá ver más información acerca de cada escenario más adelante.

|Escenario de instalación de runtime|Cargador de solución de Office|Extensiones de Office para .NET Framework 3.5|Extensiones de Office para [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]|Extensiones de Office para [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]|
|-----------------------------------|----------------------------|--------------------------------------------------| - |---------------------------------------------------------------------------|
|Con [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] y versiones posteriores|Sí|Sí, si ya está instalado .NET Framework 3.5.|Sí|Sí|
|Con [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Sí|Sí, si ya está instalado .NET Framework 3.5.|No|No|
|Con Office 2010 Service Pack 1 (SP1) o posterior|Sí|Sí, si ya está instalado .NET Framework 3.5.|Sí, si [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ya está instalado.|No|
|Con Office 2013 y versiones más recientes|Sí|Sí, si ya está instalado .NET Framework 3.5.|Sí, si [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ya está instalado.|Sí, si [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] ya está instalado.|
|Con el runtime redistribuible|Sí|Sí, si ya está instalado .NET Framework 3.5.|Sí, si [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ya está instalado.|Sí, si [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] ya está instalado.|

### <a name="install-the-runtime-with-visual-studio-or-the-microsoft-office-developer-tools-for-visual-studio"></a>Instale el runtime con Visual Studio o el Microsoft Office Developer Tools para Visual Studio

 Al instalar Office Developer Tools en Visual Studio, se instalan siempre las extensiones de Office para [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] y [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] en el equipo de desarrollo. Las extensiones de Office para .NET Framework 3.5 se instalan sólo si .NET Framework 3.5 ya está presente en el equipo de desarrollo. Si instala .NET Framework 3.5 después de instalar [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], el runtime instalará automáticamente las extensiones de Office para .NET Framework 3.5 la primera vez que cree un proyecto de Office destinado a .NET Framework 3.5.

> [!WARNING]
> No se puede crear un proyecto de Office destinado a .NET Framework 3.5 usando [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] o posterior.

 Para obtener más información sobre cómo instalar las herramientas de desarrollo de Office, [vea Cómo: Configurar un equipo para desarrollar soluciones de Office.](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)

### <a name="install-the-runtime-with-office"></a>Instalación del entorno de ejecución con Office

 Al instalar Office, las extensiones de Office para .NET Framework 3.5 se instalan solo si .NET Framework 3.5 ya está presente en el equipo. Si instala .NET Framework 3.5 después de instalar Office, el runtime instalará automáticamente las extensiones de Office para .NET Framework 3.5 la primera vez que una aplicación de Office intente cargar una solución destinada a .NET Framework 3.5.

 Las extensiones de Office para o versiones posteriores también se instalan con Office si las versiones correspondientes del .NET Framework ya están [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] presentes en el equipo.

 Para asegurarse de que los usuarios tienen las extensiones necesarias para usar la aplicación, incluya la versión más reciente de Visual Studio 2010 Tools for Office runtime redistribuible como requisito previo para la solución. Para obtener más información sobre los requisitos previos, vea [Requisitos previos de la solución de Office para la implementación.](/previous-versions/bb608617(v=vs.110))

### <a name="install-the-runtime-by-using-the-runtime-redistributable"></a>Instalación del entorno de ejecución mediante el runtime redistribuible

 Para instalar el entorno de ejecución, ejecute el entorno de ejecución de Visual Studio 2010 Tools for Office en tiempo de ejecución redistribuible manualmente o incluya redistribuible como requisito previo al implementar una solución de Office.

 Al instalar el runtime mediante las herramientas de Visual Studio 2010 para office en tiempo de ejecución redistribuibles, las extensiones de Office para .NET Framework 3.5 y las extensiones de Office para o versiones posteriores se instalan si las versiones correspondientes de .NET Framework ya están presentes en [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] el equipo. Si el equipo no tiene una de estas versiones de .NET Framework cuando se instala el tiempo de ejecución, las extensiones de Office para la versión de .NET Framework que falta no se instalan en ese momento. Si instala más adelante la versión de .NET Framework que falta, el runtime instala automáticamente las extensiones de Office correspondientes la siguiente vez que se instala (si se instaló el runtime con una solución implementada mediante ClickOnce) o que se carga (si se instaló el runtime con una solución implementada mediante Windows Installer) una solución que requiera esas extensiones.

 Para obtener más información sobre cómo incluir los requisitos previos en una solución ClickOnce, vea Cómo: Instalar los [requisitos previos](/previous-versions/bb608608(v=vs.110))en equipos de usuario final para ejecutar soluciones de Office. Para obtener más información sobre cómo instalar el entorno de ejecución desde el paquete redistribuible manualmente, vea Cómo: Instalar el Visual Studio Tools para office [runtime redistribuible.](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)

## <a name="see-also"></a>Vea también

- [Visual Studio Tools introducción al entorno de ejecución de Office](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Ensamblados en el entorno Visual Studio Tools tiempo de ejecución de Office](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)
