---
title: "Acceso global a objetos en los proyectos de Office | Microsoft Docs"
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
  - "ThisDocument_Shutdown"
  - "ThisDocument_Startup"
  - "Globals (clase), acceso global a objetos"
  - "hojas de cálculo [desarrollo de Office en Visual Studio], acceso global"
  - "documentos [desarrollo de Office en Visual Studio], acceso global"
  - "controladores de eventos [desarrollo de Office en Visual Studio]"
  - "ThisWorkbook_Startup"
  - "complementos de nivel de aplicación [desarrollo de Office en Visual Studio]"
  - "complementos [desarrollo de Office en Visual Studio], eventos"
  - "libros [desarrollo de Office en Visual Studio], acceso global"
  - "ThisWorkbook_Shutdown"
  - "personalizaciones de nivel de documento [desarrollo de Office en Visual Studio]"
  - "Startup (evento)"
  - "Shutdown (evento)"
  - "proyectos [desarrollo de Office en Visual Studio], acceso global"
  - "documentos de Office[desarrollo de Office en Visual Studio], acceso global"
  - "ThisAddin_Startup"
  - "eventos [desarrollo de Office en Visual Studio]"
  - "ThisAddIn_Shutdown"
ms.assetid: f6a7f0ef-75d0-4a9b-9aec-be95ffa26adf
caps.latest.revision: 55
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 54
---
# Acceso global a objetos en los proyectos de Office
  Cuando se crea un proyecto de Office, Visual Studio genera automáticamente una clase denominada `Globals` en el proyecto. Puede utilizar la clase `Globals` para tener acceso en tiempo de ejecución a diversos elementos del proyecto desde cualquier código del proyecto.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Cómo utilizar la clase Globals  
 `Globals` es una clase estática que mantiene referencias a determinados elementos del proyecto. Mediante el uso de la clase `Globals` puede tener acceso a los siguientes elementos desde cualquier código del proyecto en tiempo de ejecución:  
  
-   Las clases `ThisWorkbook` y `Sheet`*n* de un proyecto de libro o plantilla de Excel. Puede tener acceso a estos objetos mediante las propiedades `Globals.ThisWorkbook` y `Sheet`*n*.  
  
-   La clase `ThisDocument` de un proyecto de documento o plantilla de Word. Puede tener acceso a este objeto mediante la propiedad `Globals.ThisDocument`.  
  
-   La clase `ThisAddIn` en un proyecto de complemento de VSTO. Puede tener acceso a este objeto mediante la propiedad `Globals.ThisAddIn`.  
  
-   Todas las cintas de opciones del proyecto que haya personalizado mediante el Diseñador de la cinta de opciones. Puede tener acceso a las cintas de opciones mediante la propiedad `Globals.Ribbons`. Para obtener más información, consulta [Obtener acceso a la cinta de opciones en tiempo de ejecución](../vsto/accessing-the-ribbon-at-run-time.md).  
  
-   Todas las áreas de formulario de Outlook en un proyecto de complemento de VSTO para Outlook. Puede tener acceso a las áreas de formulario mediante la propiedad `Globals.FormRegions`. Para obtener más información, consulta [Obtener acceso a un área de formulario en tiempo de ejecución](../vsto/accessing-a-form-region-at-run-time.md).  
  
-   Un objeto generador que permite crear controles de cinta y hospedar elementos en tiempo de ejecución en los proyectos que tienen como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Puede tener acceso a este objeto mediante la propiedad `Globals.Factory`. Este objeto es una instancia de una clase que implementa una de las interfaces siguientes:  
  
    -   <xref:Microsoft.Office.Tools.Factory>  
  
    -   <xref:Microsoft.Office.Tools.Excel.Factory>  
  
    -   <xref:Microsoft.Office.Tools.Outlook.Factory>  
  
    -   <xref:Microsoft.Office.Tools.Word.Factory>  
  
 Por ejemplo, puede utilizar la propiedad `Globals.Sheet1` para insertar texto en un control <xref:Microsoft.Office.Tools.Excel.NamedRange> en `Sheet1`, cuando un usuario haga clic en un botón del panel de acciones en un proyecto de nivel de documento para Excel.  
  
 [!code-csharp[Trin_VstcoreProgramming#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/CS/Sheet1.cs#1)]
 [!code-vb[Trin_VstcoreProgramming#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/VB/Sheet1.vb#1)]  
  
## Inicializar la clase Globals  
 El código que intente usar la clase `Globals` antes de que se inicialice completamente el documento o el complemento de VSTO, podría producir una excepción de tiempo de ejecución. Por ejemplo, el uso de `Globals` al declarar una variable de nivel de clase podría provocar un error, ya que la clase `Globals` podría no estar inicializada con referencias a todos los elementos host antes de que se creara una instancia del objeto declarado.  
  
> [!NOTE]  
>  La clase `Globals` nunca se inicializa en tiempo de diseño, sino que el diseñador crea instancias de controles. Esto significa que si crea un control de usuario que utiliza una propiedad de la clase `Globals` desde dentro de una clase de control de usuario, deberá comprobar si la propiedad devuelve **null** antes de intentar usar el objeto devuelto.  
  
## Vea también  
 [Obtener acceso a la cinta de opciones en tiempo de ejecución](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Obtener acceso a un área de formulario en tiempo de ejecución](../vsto/accessing-a-form-region-at-run-time.md)   
 [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)   
 [Elemento host Document](../vsto/document-host-item.md)   
 [Elemento host Workbook](../vsto/workbook-host-item.md)   
 [Elemento host Worksheet](../vsto/worksheet-host-item.md)   
 [Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)  
  
  