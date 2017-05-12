---
title: "Referencia administrada (desarrollo de Office en Visual Studio)"
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
  - "referencia [desarrollo de Office en Visual Studio], sistema de Microsoft Office 2007 "
  - "desarrollo de Office en Visual Studio, referencia"
ms.assetid: 1fa66da0-9d90-4524-ba4f-4da13aab73b5
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# Referencia administrada (desarrollo de Office en Visual Studio)
  Esta sección contiene documentación de referencia de API para los espacios de nombres y los tipos que se utilizan en los proyectos de Office que abordan [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Para obtener documentación de referencia de API acerca de los espacios de nombres y los tipos que se usan en proyectos de Office para .NET Framework 3.5, vea la sección de referencia en la documentación de Visual Studio: [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=160658](http://go.microsoft.com/fwlink/?LinkId=160658).  
  
## En esta sección  
 <xref:Microsoft.Office.Tools>  
 Contiene clases comunes para la programación de soluciones de Office. Incluyen la clase base para los complementos VSTO, clases para crear paneles de tareas personalizados en complementos VSTO, clases para la creación de etiquetas inteligentes en soluciones de Excel y Word, y clases para crear paneles de acciones en personalizaciones de nivel de documento.  
  
 <xref:Microsoft.Office.Tools.Excel>  
 Contiene controles host y elementos host que pueden utilizarse en soluciones para Excel.  
  
 <xref:Microsoft.Office.Tools.Excel.Controls>  
 Contiene controles Excel y controles de Windows Forms que pueden utilizarse en soluciones para Excel.  
  
 <xref:Microsoft.Office.Tools.Outlook>  
 Contiene clases usadas por los complementos VSTO para Outlook, incluidas las clases que se usan para crear áreas de formulario personalizadas.  
  
 <xref:Microsoft.Office.Tools.Ribbon>  
 Contiene clases que se usan para modificar mediante programación las personalizaciones de la cinta creadas mediante el Diseñador de la cinta.  
  
 <xref:Microsoft.Office.Tools.Word>  
 Contiene controles host y elementos host que pueden utilizarse en soluciones para Word.  
  
 <xref:Microsoft.Office.Tools.Word.Controls>  
 Contiene controles de Word y controles de Windows Forms que pueden usarse en soluciones para Word.  
  
 <xref:Microsoft.VisualStudio.Tools.Applications>  
 Contiene contiene la clase <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> y un conjunto de clases relacionadas de datos almacenados en la memoria caché. Estas clases se pueden usar para modificar algunos aspectos de las personalizaciones de nivel de documento en los equipos que no tienen instalado Microsoft Office.  
  
 <xref:Microsoft.VisualStudio.Tools.Applications.Deployment>  
 Contiene la interfaz <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> \(que se puede implementar para crear una *acción posterior a la implementación* en una solución de Office\), excepciones que se pueden producir al instalar una solución de Office y otras API que forman parte de la infraestructura de Visual Studio.  
  
 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime>  
 Contiene la mayoría de las excepciones que puede iniciar el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], varias clases que pueden usarse para almacenar datos en caché en las personalizaciones de nivel de documento y otras API que forman parte de la infraestructura de Visual Studio.  
  
 <xref:Microsoft.VisualStudio.Tools.Office.BuildTasks>  
 Contiene las clases de la tarea MSBuild que se usan para crear proyectos de Office.  
  
## Vea también  
 [Información general sobre el Motor en tiempo de ejecución de Microsoft Visual Studio Tools para Office](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Introducción &#40;Desarrollo de Office en Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Ejemplos y tutoriales del desarrollo de Office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)  
  
  