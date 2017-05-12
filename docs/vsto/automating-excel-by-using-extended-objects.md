---
title: "Automatizar Excel usando objetos extendidos"
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
  - "Excel [desarrollo de Office en Visual Studio], automatizar"
  - "automatización [desarrollo de Office en Visual Studio], Excel"
  - "controles host, Excel"
  - "Excel [desarrollo de Office en Visual Studio], controles host"
  - "objetos extendidos [desarrollo de Office en Visual Studio], Excel"
  - "controles host [desarrollo de Office en Visual Studio], Excel"
  - "automatizar Excel"
  - "elementos host [desarrollo de Office en Visual Studio], Excel"
  - "controles [desarrollo de Office en Visual Studio], controles host de Excel"
ms.assetid: 3ed99480-234d-46b1-b91c-226018bd3faf
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# Automatizar Excel usando objetos extendidos
  Al desarrollar soluciones de Excel en Visual Studio, puede usar *elementos host* y *controles host* en sus soluciones. Estos son objetos que extienden algunos objetos muy usados en el modelo de objetos de Excel \(es decir, el modelo de objetos expuesto por el ensamblado de interoperabilidad primario para Excel\), como son los objetos <xref:Microsoft.Office.Interop.Excel.Worksheet> y <xref:Microsoft.Office.Interop.Excel.Range>. Los objetos extendidos se comportan como los objetos de Excel en los que se basan, pero agregan características adicionales, como nuevas capacidades de enlace de eventos y datos a los objetos.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Los elementos y los controles host están disponibles en personalizaciones de nivel de documento y de complemento de VSTO, aunque el contexto en el que se pueden usar es diferente para cada tipo de solución. Para obtener más información, consulta [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md).  
  
## Elementos host de Excel  
 Los proyectos de Excel le proporcionan acceso a varios elementos host:  
  
-   <xref:Microsoft.Office.Tools.Excel.Worksheet>. Este elemento host representa una hoja de cálculo en el proyecto. También actúa como contenedor de controles administrados, incluyendo controles host y controles de Windows Forms, y mantiene información acerca de los controles en su superficie. Para obtener más información, consulta [Elemento host Worksheet](../vsto/worksheet-host-item.md).  
  
-   <xref:Microsoft.Office.Tools.Excel.Workbook>. Este elemento host representa el libro en el proyecto y actúa como contenedor de componentes compartidos por todas las hojas de cálculo del libro. Para obtener más información, consulta [Elemento host Workbook](../vsto/workbook-host-item.md).  
  
-   <xref:Microsoft.Office.Tools.Excel.ChartSheet>. Este elemento host representa una hoja de cálculo de Excel que solo contiene un gráfico y expone eventos.  
  
     Cuando se agrega una hoja de gráfico en tiempo de diseño como una nueva hoja en el proyecto de personalización de nivel de documento de Microsoft Office Excel, Visual Studio crea automáticamente un elemento host <xref:Microsoft.Office.Tools.Excel.ChartSheet>.  
  
     Aunque un elemento host <xref:Microsoft.Office.Tools.Excel.ChartSheet> es una hoja de cálculo de Excel, no puede agregar ningún control a la hoja de gráfico. Si desea tener otros controles en una hoja de cálculo con un gráfico, no use una hoja de gráfico. En su lugar, puede colocar un gráfico como un objeto incrustado en una hoja de cálculo usando el control host <xref:Microsoft.Office.Tools.Excel.Chart>. Para obtener más información, consulta [Chart &#40;Control&#41;](../vsto/chart-control.md).  
  
## Controles host de Excel  
 Hay varios controles host de Excel que le ayudarán a crean, organizar y automatizar libros y hojas de cálculo. Estos controles host proporcionan eventos y capacidades de enlace de datos que no tienen sus homólogos en el modelo de objetos de Excel nativo.  
  
 Para obtener más información acerca de los controles host que puede usar en proyectos de Excel, consulte los siguientes temas:  
  
-   [Chart &#40;Control&#41;](../vsto/chart-control.md)  
  
-   [ListObject &#40;Control&#41;](../vsto/listobject-control.md)  
  
-   [NamedRange &#40;Control&#41;](../vsto/namedrange-control.md)  
  
-   [XmlMappedRange &#40;Control&#41;](../vsto/xmlmappedrange-control.md)  
  
## Vea también  
 [Cómo: Rellenar los controles ListObject con datos](../vsto/how-to-fill-listobject-controls-with-data.md)   
 [Cómo: Agregar controles Chart a hojas de cálculo](../vsto/how-to-add-chart-controls-to-worksheets.md)   
 [Cómo: Agregar controles ListObject a hojas de cálculo](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [Cómo: Agregar controles NamedRange a hojas de cálculo](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Cómo: Agregar controles XMLMappedRange a hojas de cálculo](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)   
 [Cómo: Cambiar el tamaño de los controles NamedRange](../vsto/how-to-resize-namedrange-controls.md)   
 [Cómo: Cambiar el tamaño de los controles ListObject](../vsto/how-to-resize-listobject-controls.md)   
 [Cómo: Validar datos cuando se agrega una fila nueva a un control ListObject](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md)   
 [Cómo: Asignar columnas ListObject a datos](../vsto/how-to-map-listobject-columns-to-data.md)   
 [Tutorial: Programar basándose en los eventos de un control NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)   
 [Extender documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controles en documentos de Office](../vsto/controls-on-office-documents.md)   
 [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)   
 [Limitaciones de programación de elementos y controles Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  