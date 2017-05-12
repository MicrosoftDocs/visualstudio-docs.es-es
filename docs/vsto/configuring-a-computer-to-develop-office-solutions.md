---
title: "Configurar un equipo para desarrollar soluciones de Office"
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
  - "Desarrollo de Office en Visual Studio, instalar herramientas"
ms.assetid: 0b481186-fd31-43bf-aa4a-591f94309555
caps.latest.revision: 97
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 96
---
# Configurar un equipo para desarrollar soluciones de Office
  Para crear complementos y personalizaciones de VSTO para Microsoft Office, instale una versión compatible de Visual Studio, .NET Framework y Microsoft Office.  
  
|Software|Versiones compatibles|  
|--------------|---------------------------|  
|Visual Studio|-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)]<br />-   [!INCLUDE[vsPreShort](../vsto/includes/vspreshort-md.md)]<br />-   [!INCLUDE[vsUltShort](../vsto/includes/vsultshort-md.md)] **Important:**  Debe activar la casilla de Microsoft Office Developer Tools durante la instalación.|  
|.NET Framework|-   .NET Framework 4 o posterior.|  
|Microsoft Office|<ul><li>Cualquier edición de conjunto de Office, incluido Office Professional Plus para Office 365.</li><li>Cualquiera de las siguientes aplicaciones:<br /><br /> <ul><li>Excel</li><li>InfoPath \(solo Office 2013 y Office 2010\)</li><li>Outlook</li><li>PowerPoint</li><li>Proyecto</li><li>Visio</li><li>Word</li></ul></li></ul><br /> Visual Basic para Aplicaciones \(VBA\) debe estar instalado como parte de Office. **Important:**  Las versiones Hacer clic y ejecutar de las aplicaciones de Office 2010 no son compatibles.|  
  
 Para conocer los pasos de instalación detallados, vea [Cómo: Configurar un equipo para desarrollar soluciones de Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).  
  
## Si las plantillas de proyecto no aparecen o no funcionan en Visual Studio  
 Si instala una versión compatible de Visual Studio, .NET Framework y Microsoft Office, pero las plantillas de proyecto de Office no aparecen en el cuadro de diálogo **Nuevo proyecto** de Visual Studio o si recibe un error al intentar usar una plantilla de proyecto, compruebe lo siguiente:  
  
-   Asegúrese de que tiene Microsoft Office Developer Tools instalado en el equipo.  
  
     Office Developer Tools es un componente opcional de Visual Studio, pero normalmente se instala automáticamente junto con Visual Studio. Si personaliza la instalación de Visual Studio y especifica las características que se deben instalar, asegúrese de elegir **Microsoft Office Developer Tools** durante la instalación.  
  
     Para asegurarse de que Microsoft Office Developer Tools se instala, inicie el programa de instalación de Visual Studio y elija el botón **Modificar**. Active la casilla **Microsoft Office Developer Tools** y después elija el botón **Actualizar**.  
  
-   Asegúrese de que no ejecuta una versión de Office entregada por medio de Hacer clic y ejecutar. Vea [Cómo: Comprobar si Outlook es una aplicación de hacer clic y ejecutar en un equipo](http://msdn.microsoft.com/library/office/ff864733(v=office.14).aspx).  
  
-   Asegúrese de que solo ejecuta una versión de Microsoft Office.  
  
 Si sigue teniendo problemas, vea [Soporte técnico adicional para errores de soluciones de Office](../vsto/additional-support-for-errors-in-office-solutions.md).  
  
## Vea también  
 [Introducción &#40;Desarrollo de Office en Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Cómo: Configurar un equipo para desarrollar soluciones de Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)   
 [Cómo: Instalar el Motor en tiempo de ejecución de Microsoft Visual Studio Tools para Office redistribuible](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)   
 [Cómo: Instalar ensamblados de interoperabilidad primarios de Office](../vsto/how-to-install-office-primary-interop-assemblies.md)   
 [Características disponibles por aplicación y tipo de proyecto de Office](../vsto/features-available-by-office-application-and-project-type.md)  
  
  