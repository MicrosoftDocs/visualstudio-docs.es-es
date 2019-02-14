---
title: Filtrar Instalar Visual Studio Tools para Office runtime redistribuible
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office runtime [Office development in Visual Studio]
- installing Office development tools in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 28bd6b050f5f313132167631d25ec7c4be661462
ms.sourcegitcommit: 22b73c601f88c5c236fe81be7ba4f7f562406d75
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/13/2019
ms.locfileid: "56227373"
---
# <a name="how-to-install-the-visual-studio-tools-for-office-runtime-redistributable"></a>Filtrar Instalar Visual Studio Tools para Office runtime redistribuible
  Visual Studio 2010 Tools para Office runtime debe instalarse en cada equipo que ejecuta las soluciones que se crean mediante el uso de Microsoft Office developer tools en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. El runtime se instala de forma automática cuando se instala [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] y Microsoft Office. Para obtener más información, consulte [Visual Studio Tools para escenarios de instalación de Office en tiempo de ejecución](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).  
  
 En las situaciones siguientes, deberá seguir las instrucciones de instalación manual que aparecen a continuación:  
  
-   Debe instalar [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] en un servidor. Por ejemplo, desea utilizar la clase <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> para administrar las soluciones de nivel de documento en un servidor.  
  
-   Debe instalar el runtime en un equipo que ya tiene todos los otros requisitos previos para las soluciones de Office instaladas.  
  
    > [!NOTE]  
    >  Tiene que ser administrador del equipo de desarrollo para instalar .NET Framework y [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
## <a name="to-install-the-visual-studio-tools-for-office-runtime"></a>Para instalar el runtime de Microsoft Visual Studio Tools para Office  
  
1.  Instale [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores.  
  
    -   Para descargar el [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], consulte [Microsoft .NET Framework 4 (instalador Web)](http://go.microsoft.com/fwlink/?LinkId=178957).  
  
    -   Para descargar el [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)], consulte [Microsoft .NET Framework 4 Client Profile (instalador Web)](http://go.microsoft.com/fwlink/?LinkId=178958).  
  
    -   Para descargar el [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], consulte [Microsoft .NET Framework 4.5](http://www.microsoft.com/download/details.aspx?id=30653).  
  
2.  Ejecute *vstor_redist.exe* para instalar el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
     Puede descargar estos archivos de programa de instalación de [Visual Studio 2010 Tools para Office runtime](http://go.microsoft.com/fwlink/?LinkId=140384). Los requisitos previos para [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] coinciden con los requisitos previos para .NET Framework.  
  
     [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] incluye paquetes de idioma. Si la instalación de Windows está establecida en un idioma distinto del inglés, puede mostrar los mensajes del runtime en el mismo idioma que se usa para Windows. De igual forma, si los usuarios finales instalan [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] y, a continuación, ejecutan sus soluciones en instalaciones de Windows que están establecidas en un idioma distinto del inglés, los mensajes del runtime aparecerán en el mismo idioma que Windows. En algunos casos, puede necesitar paquetes de idioma adicionales. Por ejemplo, puede necesitar paquetes de idioma adicionales si su copia de Windows utiliza más de una configuración de idioma, o cambia a otro idioma después de que ya ha instalado el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Puede encontrar paquetes de idioma en [Microsoft Visual Studio 2010 Tools para el paquete de idioma de Microsoft Office system (versión 4.0 runtime)](http://go.microsoft.com/fwlink/?LinkId=140386).  
  
## <a name="see-also"></a>Vea también  
 [Introducción a &#40;desarrollo de Office en Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Configurar un equipo para desarrollar soluciones de Office](../vsto/configuring-a-computer-to-develop-office-solutions.md)   
 [Cómo: Configurar un equipo para desarrollar soluciones de Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)   
 [Cómo: Instalar a ensamblados de interoperabilidad primarios de Office](../vsto/how-to-install-office-primary-interop-assemblies.md)   
 [Administrar documentos en un servidor mediante la clase ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)  
