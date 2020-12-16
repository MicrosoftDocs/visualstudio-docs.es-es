---
title: Visual Studio Tools para escenarios de instalación en tiempo de ejecución de Office
description: Obtenga información acerca de cómo puede instalar el motor en tiempo de ejecución de Visual Studio 2010 Tools para Office. En este artículo se describen tres escenarios de instalación.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 484627c01a5385a6da4b2b0a41a966ac31d0e6d8
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526401"
---
# <a name="visual-studio-tools-for-office-runtime-installation-scenarios"></a>Visual Studio Tools para escenarios de instalación en tiempo de ejecución de Office
  Puede instalar el tiempo de ejecución de Visual Studio 2010 Tools para Office de tres maneras:

- Al instalar Visual Studio.

- Al instalar Microsoft Office.

- Al instalar Visual Studio 2010 Tools para Office Runtime Redistributable.

  Los componentes del runtime que se instalan dependen de la configuración del equipo y el escenario de instalación.

## <a name="runtime-components-that-are-installed-in-each-installation-scenario"></a>Componentes en tiempo de ejecución que se instalan en cada escenario de instalación
 Visual Studio 2010 Tools para Office Runtime tiene tres componentes: el cargador de soluciones de Office, las extensiones de Office para el .NET Framework 3,5 y las extensiones de Office para [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores. Cuando se instala el runtime, se instala siempre el cargador de solución de Office. La instalación de las extensiones de Office para .NET Framework depende de la configuración del equipo y el escenario de instalación. Si no se puede instalar alguna de las extensiones de Office al instalar por primera vez el runtime, el runtime instalará automáticamente las extensiones de Office que faltan más adelante, cuando se cumplan ciertos requisitos. Esta característica del tiempo de ejecución se denomina *instalar a petición*.

 La siguiente tabla muestra los componentes del runtime que se instalan de forma predeterminada en cada escenario de instalación del runtime. Podrá ver más información acerca de cada escenario más adelante.

|Escenario de instalación de runtime|Cargador de solución de Office|Extensiones de Office para .NET Framework 3.5|Extensiones de Office para [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]|Extensiones de Office para [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]|
|-----------------------------------|----------------------------|--------------------------------------------------| - |---------------------------------------------------------------------------|
|Con [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] y versiones posteriores|Sí|Sí, si ya está instalado .NET Framework 3.5.|Sí|Sí|
|Con [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Sí|Sí, si ya está instalado .NET Framework 3.5.|No|No|
|Con Office 2010 Service Pack 1 (SP1) o posterior|Sí|Sí, si ya está instalado .NET Framework 3.5.|Sí, si [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ya está instalado.|No|
|Con el runtime redistribuible|Sí|Sí, si ya está instalado .NET Framework 3.5.|Sí, si [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ya está instalado.|Sí, si [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] ya está instalado.|

### <a name="install-the-runtime-with-visual-studio-or-the-microsoft-office-developer-tools-for-visual-studio"></a>Instalar el Runtime con Visual Studio o el Microsoft Office Developer Tools para Visual Studio
 Al instalar Office Developer Tools en Visual Studio, se instalan siempre las extensiones de Office para [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] y [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] en el equipo de desarrollo. Las extensiones de Office para .NET Framework 3.5 se instalan sólo si .NET Framework 3.5 ya está presente en el equipo de desarrollo. Si instala .NET Framework 3.5 después de instalar [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], el runtime instalará automáticamente las extensiones de Office para .NET Framework 3.5 la primera vez que cree un proyecto de Office destinado a .NET Framework 3.5.

> [!WARNING]
> No se puede crear un proyecto de Office destinado a .NET Framework 3.5 usando [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] o posterior.

 Para obtener más información sobre cómo instalar las herramientas de desarrollo de Office, consulte [How to: Configure a Computer to develop Office Solutions](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).

### <a name="install-the-runtime-with-office"></a>Instalación del tiempo de ejecución con Office
 Al instalar Office, las extensiones de Office para .NET Framework 3.5 se instalan solo si .NET Framework 3.5 ya está presente en el equipo. Si instala .NET Framework 3.5 después de instalar Office, el runtime instalará automáticamente las extensiones de Office para .NET Framework 3.5 la primera vez que una aplicación de Office intente cargar una solución destinada a .NET Framework 3.5.

 Las extensiones de Office para [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o posterior no se instalan con Office, incluso aunque ya está presente [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o posterior cuando se instala Office.

 Las extensiones de Office para [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] se instalan con Office. Los usuarios finales pueden obtener las extensiones de Office para [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] mediante la instalación de una actualización de Windows.

 Para asegurarse de que los usuarios tienen las extensiones necesarias para usar la aplicación, incluya la versión más reciente de Visual Studio 2010 Tools para Office Runtime Redistributable como requisito previo para la solución. Para obtener más información sobre los requisitos previos, vea [requisitos previos de la solución de Office para la implementación](/previous-versions/bb608617(v=vs.110)).

### <a name="install-the-runtime-by-using-the-runtime-redistributable"></a>Instalación del tiempo de ejecución mediante el redistribuible en tiempo de ejecución
 Puede instalar el tiempo de ejecución ejecutando Visual Studio 2010 Tools para Office Runtime Redistributable manualmente o incluyendo el redistribuible como requisito previo al implementar una solución de Office.

 Al instalar el tiempo de ejecución mediante el uso de Visual Studio 2010 Tools para Office Runtime Redistributable, se instalan las extensiones de Office para el .NET Framework 3,5 y las extensiones de Office para [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores si las versiones correspondientes del .NET Framework ya están presentes en el equipo. Si el equipo no tiene una de estas versiones de .NET Framework cuando se instala el tiempo de ejecución, las extensiones de Office para la versión de .NET Framework que falta no se instalan en ese momento. Si instala más adelante la versión de .NET Framework que falta, el runtime instala automáticamente las extensiones de Office correspondientes la siguiente vez que se instala (si se instaló el runtime con una solución implementada mediante ClickOnce) o que se carga (si se instaló el runtime con una solución implementada mediante Windows Installer) una solución que requiera esas extensiones.

 Para obtener más información sobre cómo incluir requisitos previos en una solución ClickOnce, consulte [Cómo: instalar requisitos previos en equipos de usuarios finales para ejecutar soluciones de Office](/previous-versions/bb608608(v=vs.110)). Para obtener más información sobre cómo instalar manualmente el tiempo de ejecución del paquete redistribuible, vea [Cómo: instalar el Visual Studio Tools para Office Runtime Redistributable](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md).

## <a name="see-also"></a>Consulte también
- [Información general sobre el tiempo de ejecución de Visual Studio Tools para Office](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Ensamblados en el Visual Studio Tools para Office Runtime](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)