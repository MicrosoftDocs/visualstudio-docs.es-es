---
title: "Visual Studio Tools para escenarios de instalación de Office en tiempo de ejecución | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio Tools for Office runtime, installation scenarios
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 9c63f5e4cef88ed927326b69f1fa389e34b06c8b
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="visual-studio-tools-for-office-runtime-installation-scenarios"></a>Escenarios de instalación del Motor en runtime de Microsoft Visual Studio Tools para Office
  Puede instalar Visual Studio 2010 Tools para Office Runtime de tres maneras:  
  
-   Al instalar Visual Studio.  
  
-   Al instalar Microsoft Office.  
  
-   Al instalar Microsoft Visual Studio 2010 Tools para Office Runtime redistribuible.  
  
 Los componentes del runtime que se instalan dependen de la configuración del equipo y el escenario de instalación.  
  
## <a name="runtime-components-that-are-installed-in-each-installation-scenario"></a>Componentes del runtime que se instalan en todos los escenarios de instalación  
 Visual Studio 2010 Tools para Office Runtime tiene tres componentes: el cargador de solución de Office, las extensiones de Office para .NET Framework 3.5 y las extensiones de Office para [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o posterior. Cuando se instala el runtime, se instala siempre el cargador de solución de Office. La instalación de las extensiones de Office para .NET Framework depende de la configuración del equipo y el escenario de instalación. Si no se puede instalar alguna de las extensiones de Office al instalar por primera vez el runtime, el runtime instalará automáticamente las extensiones de Office que faltan más adelante, cuando se cumplan ciertos requisitos. Esta característica del runtime se denomina *instalar a petición*.  
  
 La siguiente tabla muestra los componentes del runtime que se instalan de forma predeterminada en cada escenario de instalación del runtime. Podrá ver más información acerca de cada escenario más adelante.  
  
|Escenario de instalación de runtime|Cargador de solución de Office|Extensiones de Office para .NET Framework 3.5|Extensiones de Office para [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]|Extensiones de Office para [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]|  
|-----------------------------------|----------------------------|--------------------------------------------------|---------------------------------------------------------------------------------------|---------------------------------------------------------------------------|  
|Con [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] y versiones posteriores|Sí|Sí, si ya está instalado .NET Framework 3.5.|Sí|Sí|  
|Con [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Sí|Sí, si ya está instalado .NET Framework 3.5.|No|No|  
|Con Office 2010 Service Pack 1 (SP1) o posterior|Sí|Sí, si ya está instalado .NET Framework 3.5.|Sí, si [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ya está instalado.|No|  
|Con el runtime redistribuible|Sí|Sí, si ya está instalado .NET Framework 3.5.|Sí, si [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ya está instalado.|Sí, si [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] ya está instalado.|  
  
### <a name="installing-the-runtime-with-visual-studio-or-the-microsoft-office-developer-tools-for-visual-studio"></a>Instalar el runtime con Visual Studio o con Microsoft Office Developer Tools para Visual Studio  
 Al instalar Office Developer Tools en Visual Studio, se instalan siempre las extensiones de Office para [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] y [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] en el equipo de desarrollo. Las extensiones de Office para .NET Framework 3.5 se instalan sólo si .NET Framework 3.5 ya está presente en el equipo de desarrollo. Si instala .NET Framework 3.5 después de instalar [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], el runtime instalará automáticamente las extensiones de Office para .NET Framework 3.5 la primera vez que cree un proyecto de Office destinado a .NET Framework 3.5.  
  
> [!WARNING]  
>  No se puede crear un proyecto de Office destinado a .NET Framework 3.5 usando [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] o posterior.  
  
 Para obtener más información sobre cómo instalar las herramientas de desarrollo de Office, consulte [Cómo: configurar un equipo para desarrollar soluciones de Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).  
  
### <a name="installing-the-runtime-with-office"></a>Instalar el runtime con Office  
 Al instalar Office, las extensiones de Office para .NET Framework 3.5 se instalan solo si .NET Framework 3.5 ya está presente en el equipo. Si instala .NET Framework 3.5 después de instalar Office, el runtime instalará automáticamente las extensiones de Office para .NET Framework 3.5 la primera vez que una aplicación de Office intente cargar una solución destinada a .NET Framework 3.5.  
  
 Las extensiones de Office para [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o posterior no se instalan con Office, incluso aunque ya está presente [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o posterior cuando se instala Office.  
  
 Las extensiones de Office para [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] se instalan con Office. Los usuarios finales pueden obtener las extensiones de Office para [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] mediante la instalación de una actualización de Windows.  
  
 Para asegurarse de que los usuarios tienen las extensiones necesarias para utilizar la aplicación, incluya la versión más reciente de Visual Studio 2010 Tools para Office Runtime redistribuible como requisito previo para la solución. Para obtener más información sobre los requisitos previos, consulte [requisitos previos de la solución de Office para la implementación](http://msdn.microsoft.com/en-us/9f672809-43a3-40a1-9057-397ce3b5126e).  
  
### <a name="installing-the-runtime-by-using-the-runtime-redistributable"></a>Instalar el tiempo de ejecución mediante el paquete redistribuible del runtime  
 Puede instalar el runtime ejecutando Visual Studio 2010 Tools para Office Runtime redistribuible manualmente o incluyendo el redistribuible como requisito previo al implementar una solución de Office.  
  
 Cuando instala el runtime mediante Visual Studio 2010 Tools para Office Runtime redistribuible, se instalan las extensiones de Office para .NET Framework 3.5 y las extensiones de Office para [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o posterior si las versiones de .NET Framework correspondientes ya están presentes en el equipo. Si el equipo no tiene una de estas versiones de .NET Framework cuando se instala el tiempo de ejecución, las extensiones de Office para la versión de .NET Framework que falta no se instalan en ese momento. Si instala más adelante la versión de .NET Framework que falta, el runtime instala automáticamente las extensiones de Office correspondientes la siguiente vez que se instala (si se instaló el runtime con una solución implementada mediante ClickOnce) o que se carga (si se instaló el runtime con una solución implementada mediante Windows Installer) una solución que requiera esas extensiones.  
  
 Para obtener más información sobre cómo incluir requisitos previos en una solución de ClickOnce, vea [Cómo: instalar los requisitos previos en equipos de usuarios finales para ejecutar soluciones de Office](http://msdn.microsoft.com/en-us/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98). Para obtener más información acerca de cómo instalar manualmente el tiempo de ejecución del paquete redistribuible, vea [Cómo: instalar Visual Studio Tools para Office Runtime redistribuible](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md).  
  
## <a name="see-also"></a>Vea también  
 [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Ensamblados en el Motor en tiempo de ejecución de Visual Studio Tools para Office](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)  
  
  