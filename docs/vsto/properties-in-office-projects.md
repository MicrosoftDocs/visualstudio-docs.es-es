---
title: "Propiedades de los proyectos de Office"
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
  - "propiedad de ubicación de los ensamblados de plena confianza"
  - "propiedad de caché en documento"
  - "propiedades [desarrollo de Office en Visual Studio]"
  - "Propiedad del espacio de nombres para el elemento host"
  - "proyectos de Office [desarrollo de Office en Visual Studio], propiedades"
  - "proyectos [desarrollo de Office en Visual Studio], propiedades"
  - "Value2 (propiedad)"
ms.assetid: 1284d6c3-8200-4151-88ce-0b5c7765af25
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# Propiedades de los proyectos de Office
  Hay varias propiedades importantes que están disponibles para los proyectos de Office en Visual Studio. Se puede obtener acceso a estas propiedades en la ventana **Propiedades**.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Espacio de nombres para el elemento host  
 Utilice la propiedad **Espacio de nombres para el elemento host** para cambiar el espacio de nombres de las clases de elementos host \(por ejemplo, las clases `ThisAddIn`, `ThisWorkbook` o `ThisDocument`\) en proyectos de Visual C\#. Esta propiedad aparece en la ventana **Propiedades** cuando se selecciona el nodo de documento de un proyecto de nivel de documento \(como ExcelWorkbook1.xlsx o WordDocument1.docx\) o el nodo de aplicación de un proyecto de complemento de VSTO \(como Excel o Word\) en el **Explorador de soluciones**.  
  
 Cuando se crea un proyecto de Visual C\# de Office, los elementos host reciben un espacio de nombres basado en el nombre del proyecto. Se recomienda utilizar la propiedad **Espacio de nombres para el elemento host** para cambiar el espacio de nombres en lugar de para modificar los archivos de código directamente. Cuando se utiliza esta propiedad, se cambia el espacio de nombres en los archivos de código generados \(ocultos\), así como en los archivos de código visibles.  
  
## CacheInDocument  
 La propiedad **CacheInDocument** aparece en la ventana **Propiedades** de los proyectos de nivel de documento cuando se selecciona una instancia de un <xref:System.Data.DataSet> en el diseñador de Visual Studio. Solo es posible almacenar en caché los miembros públicos; asegúrese de que la propiedad **Modificadores** esté establecida en **Público** si desea almacenar en caché un <xref:System.Data.DataSet>.  
  
 Esta propiedad toma un valor booleano:  
  
-   Seleccione **true** para almacenar en caché el conjunto de datos en el documento.  
  
-   Seleccione **false** si no desea que el conjunto de datos se almacene en caché en el documento.  
  
 Para obtener más información sobre el almacenamiento de datos en caché, vea [Datos almacenados en caché en las personalizaciones de nivel de documento](../vsto/cached-data-in-document-level-customizations.md).  
  
## Value2  
 La propiedad **Value2** solo está disponible para los proyectos de libro o plantilla de Excel. Aparece en el nodo de propiedad **Databindings** de la ventana **Propiedades** cuando se selecciona un control <xref:Microsoft.Office.Tools.Excel.NamedRange> en el diseñador de hojas de cálculo.  
  
 Utilice la propiedad **Value2** de la ventana **Propiedades** para enlazar la propiedad <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> del <xref:Microsoft.Office.Tools.Excel.NamedRange> a un campo del origen de datos.  
  
## Vea también  
 [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)   
 [Información general sobre las plantillas de Office Project](../vsto/office-project-templates-overview.md)   
 [Eventos de los proyectos de Office](../vsto/events-in-office-projects.md)  
  
  