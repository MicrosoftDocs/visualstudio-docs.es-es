---
title: Visual Studio Tools para escenarios de instalación de Office en tiempo de ejecución
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
ms.openlocfilehash: 5bf5314abd1cf2266d89feaa8f1772b7a7177949
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54872474"
---
# <a name="visual-studio-tools-for-office-runtime-installation-scenarios"></a>Visual Studio Tools para escenarios de instalación de Office en tiempo de ejecución
  Puede instalar Visual Studio 2010 Tools para Office runtime de tres maneras:  
  
- Al instalar Visual Studio.  
  
- Al instalar Microsoft Office.  
  
- Cuando instala Visual Studio 2010 Tools para Office runtime redistribuible.  
  
  Los componentes del runtime que se instalan dependen de la configuración del equipo y el escenario de instalación.  
  
## <a name="runtime-components-that-are-installed-in-each-installation-scenario"></a>Componentes del Runtime que se instalan en cada escenario de instalación  
 Visual Studio 2010 Tools para Office runtime tiene tres componentes: el cargador de solución de Office, las extensiones de Office para .NET Framework 3.5 y las extensiones de Office para la [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o una versión posterior. Cuando se instala el runtime, se instala siempre el cargador de solución de Office. La instalación de las extensiones de Office para .NET Framework depende de la configuración del equipo y el escenario de instalación. Si no se puede instalar alguna de las extensiones de Office al instalar por primera vez el runtime, el runtime instalará automáticamente las extensiones de Office que faltan más adelante, cuando se cumplan ciertos requisitos. Esta característica del tiempo de ejecución se denomina *instalar a petición*.  
  
 La siguiente tabla muestra los componentes del runtime que se instalan de forma predeterminada en cada escenario de instalación del runtime. Podrá ver más información acerca de cada escenario más adelante.  
  
|Escenario de instalación de runtime|Cargador de solución de Office|Extensiones de Office para .NET Framework 3.5|Extensiones de Office para [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]|Extensiones de Office para [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]|  
|-----------------------------------|----------------------------|--------------------------------------------------| - |---------------------------------------------------------------------------|  
|Con [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] y versiones posteriores|Sí|Sí, si ya está instalado .NET Framework 3.5.|Sí|Sí|  
|Con [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Sí|Sí, si ya está instalado .NET Framework 3.5.|No|No|  
|Con Office 2010 Service Pack 1 (SP1) o posterior|Sí|Sí, si ya está instalado .NET Framework 3.5.|Sí, si [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ya está instalado.|No|  
|Con el runtime redistribuible|Sí|Sí, si ya está instalado .NET Framework 3.5.|Sí, si [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ya está instalado.|Sí, si [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] ya está instalado.|  
  
### <a name="install-the-runtime-with-visual-studio-or-the-microsoft-office-developer-tools-for-visual-studio"></a>Instalar el runtime con Visual Studio o Microsoft Office Developer Tools para Visual Studio  
 Al instalar Office Developer Tools en Visual Studio, se instalan siempre las extensiones de Office para [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] y [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] en el equipo de desarrollo. Las extensiones de Office para .NET Framework 3.5 se instalan sólo si .NET Framework 3.5 ya está presente en el equipo de desarrollo. Si instala .NET Framework 3.5 después de instalar [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], el runtime instalará automáticamente las extensiones de Office para .NET Framework 3.5 la primera vez que cree un proyecto de Office destinado a .NET Framework 3.5.  
  
> [!WARNING]  
>  No se puede crear un proyecto de Office destinado a .NET Framework 3.5 usando [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] o posterior.  
  
 Para obtener más información sobre cómo instalar las herramientas de desarrollo de Office, vea [Cómo: Configurar un equipo para desarrollar soluciones de Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).  
  
### <a name="install-the-runtime-with-office"></a>Instalar el runtime con Office  
 Al instalar Office, las extensiones de Office para .NET Framework 3.5 se instalan solo si .NET Framework 3.5 ya está presente en el equipo. Si instala .NET Framework 3.5 después de instalar Office, el runtime instalará automáticamente las extensiones de Office para .NET Framework 3.5 la primera vez que una aplicación de Office intente cargar una solución destinada a .NET Framework 3.5.  
  
 Las extensiones de Office para [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o posterior no se instalan con Office, incluso aunque ya está presente [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o posterior cuando se instala Office.  
  
 Las extensiones de Office para [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] se instalan con Office. Los usuarios finales pueden obtener las extensiones de Office para [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] mediante la instalación de una actualización de Windows.  
  
 Para asegurarse de que los usuarios tengan las extensiones necesarias para utilizar la aplicación, incluya la versión más reciente de Visual Studio 2010 Tools para Office runtime redistribuible como requisito previo para la solución. Para obtener más información sobre los requisitos previos, consulte [requisitos previos de la solución de Office para implementación](https://msdn.microsoft.com/9f672809-43a3-40a1-9057-397ce3b5126e).  
  
### <a name="install-the-runtime-by-using-the-runtime-redistributable"></a>Instalar el tiempo de ejecución con el runtime redistribuible  
 Puede instalar el tiempo de ejecución mediante la ejecución de Visual Studio 2010 Tools para Office runtime redistribuible manualmente o incluyendo el redistribuible como requisito previo al implementar una solución de Office.  
  
 Cuando instala el tiempo de ejecución mediante el uso de Visual Studio 2010 Tools para Office runtime redistribuible, las extensiones de Office para .NET Framework 3.5 y las extensiones de Office para la [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o posterior si se instalan las correspondientes versiones de .NET Marco de trabajo ya están presentes en el equipo. Si el equipo no tiene una de estas versiones de .NET Framework cuando se instala el tiempo de ejecución, las extensiones de Office para la versión de .NET Framework que falta no se instalan en ese momento. Si instala más adelante la versión de .NET Framework que falta, el runtime instala automáticamente las extensiones de Office correspondientes la siguiente vez que se instala (si se instaló el runtime con una solución implementada mediante ClickOnce) o que se carga (si se instaló el runtime con una solución implementada mediante Windows Installer) una solución que requiera esas extensiones.  
  
 Para obtener más información sobre cómo incluir requisitos previos en una solución ClickOnce, vea [Cómo: Instalar requisitos previos en equipos de usuarios finales para ejecutar soluciones de Office](https://msdn.microsoft.com/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98). Para obtener más información sobre cómo instalar manualmente el tiempo de ejecución del paquete redistribuible, vea [Cómo: Instalar Visual Studio Tools para Office runtime redistribuible](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md).  
  
## <a name="see-also"></a>Vea también  
 [Visual Studio Tools para Office runtime overview](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Ensamblados en Visual Studio Tools para Office runtime](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)  
