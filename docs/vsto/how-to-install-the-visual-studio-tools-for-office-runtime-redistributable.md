---
title: "C&#243;mo: Instalar el Motor en tiempo de ejecuci&#243;n de Microsoft Visual Studio Tools para Office redistribuible | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "instalar las herramientas de desarrollo de Office en Visual Studio"
  - "runtime de Office [desarrollo de Office en Visual Studio]"
ms.assetid: ac7a9ad3-e810-4d7f-a0e2-9992c9036b8d
caps.latest.revision: 94
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 93
---
# C&#243;mo: Instalar el Motor en tiempo de ejecuci&#243;n de Microsoft Visual Studio Tools para Office redistribuible
  El runtime de Microsoft Visual Studio 2010 Tools para Office debe estar instalado en los equipos que ejecuten soluciones creadas con Microsoft Office Developer Tools en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  El runtime se instala de forma automática cuando se instala [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] y Microsoft Office.  Para obtener más información, consulte [Escenarios de instalación del Motor en tiempo de ejecución de Microsoft Visual Studio Tools para Office](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).  
  
 En las situaciones siguientes, deberá seguir las instrucciones de instalación manual que aparecen a continuación:  
  
-   Debe instalar [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] en un servidor.  Por ejemplo, desea utilizar la clase <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> para administrar las soluciones de nivel de documento en un servidor.  
  
-   Debe instalar el runtime en un equipo que ya tiene todos los otros requisitos previos para las soluciones de Office instaladas.  
  
    > [!NOTE]  
    >  Tiene que ser administrador del equipo de desarrollo para instalar .NET Framework y [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
### Para instalar el runtime de Microsoft Visual Studio Tools para Office  
  
1.  Instale [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores.  
  
    -   Para descargar [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], vea [Microsoft .NET Framework 4 \(instalador web\)](http://go.microsoft.com/fwlink/?LinkId=178957).  
  
    -   Para descargar [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)], vea [Microsoft .NET Framework 4 Client Profile \(instalador web\)](http://go.microsoft.com/fwlink/?LinkId=178958).  
  
    -   Para descargar [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], vea [Microsoft .NET Framework 4.5](http://www.microsoft.com/download/details.aspx?id=30653).  
  
2.  Ejecute vstor\_redist.exe para instalar [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
     Puede descargar estos archivos de programa de instalación de [Visual Studio 2010 Tools para Office Runtime](http://go.microsoft.com/fwlink/?LinkId=140384).  Los requisitos previos para [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] coinciden con los requisitos previos para .NET Framework.  
  
     [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] incluye paquetes de idioma.  Si la instalación de Windows está establecida en un idioma distinto del inglés, puede mostrar los mensajes del runtime en el mismo idioma que se usa para Windows.  De igual forma, si los usuarios finales instalan [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] y, a continuación, ejecutan sus soluciones en instalaciones de Windows que están establecidas en un idioma distinto del inglés, los mensajes del runtime aparecerán en el mismo idioma que Windows.  En algunos casos, puede necesitar paquetes de idioma adicionales.  Por ejemplo, podría necesitar paquetes de idioma adicionales si su copia de Windows utiliza más de una configuración de idioma o si cambia a otro idioma después de haber instalado [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  Puede encontrar los paquetes de idioma en [Paquete de idioma de Microsoft Visual Studio 2010 Tools para Office \(versión 4.0 Runtime\)](http://go.microsoft.com/fwlink/?LinkId=140386).  
  
## Vea también  
 [Introducción &#40;Desarrollo de Office en Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Configurar un equipo para desarrollar soluciones de Office](../vsto/configuring-a-computer-to-develop-office-solutions.md)   
 [Cómo: Configurar un equipo para desarrollar soluciones de Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)   
 [Cómo: Instalar ensamblados de interoperabilidad primarios de Office](../vsto/how-to-install-office-primary-interop-assemblies.md)   
 [Administrar documentos en un servidor mediante la clase ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)  
  
  