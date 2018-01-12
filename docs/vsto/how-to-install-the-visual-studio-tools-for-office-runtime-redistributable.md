---
title: "Cómo: instalar Visual Studio Tools para Office Runtime redistribuible | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office runtime [Office development in Visual Studio]
- installing Office development tools in Visual Studio
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 5f76191ca8b41f252e5009c0d3e7e09415f6f081
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-install-the-visual-studio-tools-for-office-runtime-redistributable"></a>Cómo: Instalar el Motor en runtime de Microsoft Visual Studio Tools para Office redistribuible
  Visual Studio 2010 Tools para Office Runtime debe instalarse en cada equipo que ejecuta las soluciones que se crean mediante las herramientas de desarrollo de Microsoft Office en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. El runtime se instala de forma automática cuando se instala [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] y Microsoft Office. Para obtener más información, consulta [Visual Studio Tools for Office Runtime Installation Scenarios](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).  
  
 En las situaciones siguientes, deberá seguir las instrucciones de instalación manual que aparecen a continuación:  
  
-   Debe instalar [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] en un servidor. Por ejemplo, desea utilizar la clase <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> para administrar las soluciones de nivel de documento en un servidor.  
  
-   Debe instalar el runtime en un equipo que ya tiene todos los otros requisitos previos para las soluciones de Office instaladas.  
  
    > [!NOTE]  
    >  Tiene que ser administrador del equipo de desarrollo para instalar .NET Framework y [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
### <a name="to-install-the-visual-studio-tools-for-office-runtime"></a>Para instalar el runtime de Microsoft Visual Studio Tools para Office  
  
1.  Instale [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores.  
  
    -   Para descargar el [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], consulte [Microsoft .NET Framework 4 (instalador Web)](http://go.microsoft.com/fwlink/?LinkId=178957).  
  
    -   Para descargar el [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)], consulte [Microsoft .NET Framework 4 Client Profile (instalador Web)](http://go.microsoft.com/fwlink/?LinkId=178958).  
  
    -   Para descargar el [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], consulte [Microsoft .NET Framework 4.5](http://www.microsoft.com/download/details.aspx?id=30653).  
  
2.  Ejecute vstor_redist.exe para instalar [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
     Puede descargar estos archivos de programa de instalación de [Visual Studio 2010 Tools para Office Runtime](http://go.microsoft.com/fwlink/?LinkId=140384). Los requisitos previos para [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] coinciden con los requisitos previos para .NET Framework.  
  
     El [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]incluye paquetes de idioma. Si la instalación de Windows está establecida en un idioma distinto del inglés, puede mostrar los mensajes del runtime en el mismo idioma que se usa para Windows. De igual forma, si los usuarios finales instalan [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] y, a continuación, ejecutan sus soluciones en instalaciones de Windows que están establecidas en un idioma distinto del inglés, los mensajes del runtime aparecerán en el mismo idioma que Windows. En algunos casos, puede necesitar paquetes de idioma adicionales. Por ejemplo, podría necesitar paquetes de idioma adicionales si su copia de Windows utiliza más de una configuración de idioma, o cambia a otro idioma después de que ya ha instalado el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Puede encontrar paquetes de idioma en [Microsoft Visual Studio 2010 Tools para el paquete de idioma de Microsoft Office System (versión 4.0 Runtime)](http://go.microsoft.com/fwlink/?LinkId=140386).  
  
## <a name="see-also"></a>Vea también  
 [Introducción a &#40; desarrollo de Office en Visual Studio &#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Configuring a Computer to Develop Office Solutions](../vsto/configuring-a-computer-to-develop-office-solutions.md)   
 [Cómo: configurar un equipo para desarrollar soluciones de Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)   
 [Cómo: instalar ensamblados de interoperabilidad primarios de Office](../vsto/how-to-install-office-primary-interop-assemblies.md)   
 [Administrar documentos en un servidor mediante la clase ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Implementación de una solución de Office](../vsto/deploying-an-office-solution.md)  
  
  