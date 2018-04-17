---
title: Automatizar Excel usando objetos extendidos | Documentos de Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], automating
- automation [Office development in Visual Studio], Excel
- host controls, Excel
- Excel [Office development in Visual Studio], host controls
- extended objects [Office development in Visual Studio], Excel
- host controls [Office development in Visual Studio], Excel
- automating Excel
- host items [Office development in Visual Studio], Excel
- controls [Office development in Visual Studio], Excel host controls
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 63c200a3d3a6a64dfc100cc9365f142a8dddae4c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="automating-excel-by-using-extended-objects"></a>Automatizar Excel usando objetos extendidos
  Al desarrollar soluciones de Excel en Visual Studio, puede usar *elementos host* y *controles host*en sus soluciones. Estos son objetos que extienden algunos objetos muy usados en el modelo de objetos de Excel (es decir, el modelo de objetos expuesto por el ensamblado de interoperabilidad primario para Excel), como son los objetos <xref:Microsoft.Office.Interop.Excel.Worksheet> y <xref:Microsoft.Office.Interop.Excel.Range> . Los objetos extendidos se comportan como los objetos de Excel en los que se basan, pero agregan características adicionales, como nuevas capacidades de enlace de eventos y datos a los objetos.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Los elementos y los controles host están disponibles en personalizaciones de nivel de documento y de complemento de VSTO, aunque el contexto en el que se pueden usar es diferente para cada tipo de solución. Para obtener más información, consulta [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md).  
  
## <a name="excel-host-items"></a>Elementos host de Excel  
 Los proyectos de Excel le proporcionan acceso a varios elementos host:  
  
-   <xref:Microsoft.Office.Tools.Excel.Worksheet>. Este elemento host representa una hoja de cálculo en el proyecto. También actúa como contenedor de controles administrados, incluyendo controles host y controles de Windows Forms, y mantiene información acerca de los controles en su superficie. Para obtener más información, consulta [Worksheet Host Item](../vsto/worksheet-host-item.md).  
  
-   <xref:Microsoft.Office.Tools.Excel.Workbook>. Este elemento host representa el libro en el proyecto y actúa como contenedor de componentes compartidos por todas las hojas de cálculo del libro. Para obtener más información, consulta [Workbook Host Item](../vsto/workbook-host-item.md).  
  
-   <xref:Microsoft.Office.Tools.Excel.ChartSheet>. Este elemento host representa una hoja de cálculo de Excel que solo contiene un gráfico y expone eventos.  
  
     Cuando se agrega una hoja de gráfico en tiempo de diseño como una nueva hoja en el proyecto de personalización de nivel de documento de Microsoft Office Excel, Visual Studio crea automáticamente un elemento host <xref:Microsoft.Office.Tools.Excel.ChartSheet> .  
  
     Aunque un elemento host <xref:Microsoft.Office.Tools.Excel.ChartSheet> es una hoja de cálculo de Excel, no puede agregar ningún control a la hoja de gráfico. Si desea tener otros controles en una hoja de cálculo con un gráfico, no use una hoja de gráfico. En su lugar, puede colocar un gráfico como un objeto incrustado en una hoja de cálculo usando el control host <xref:Microsoft.Office.Tools.Excel.Chart> . Para obtener más información, consulta [Chart Control](../vsto/chart-control.md).  
  
## <a name="excel-host-controls"></a>Controles host de Excel  
 Hay varios controles host de Excel que le ayudarán a crean, organizar y automatizar libros y hojas de cálculo. Estos controles host proporcionan eventos y capacidades de enlace de datos que no tienen sus homólogos en el modelo de objetos de Excel nativo.  
  
 Para obtener más información acerca de los controles host que puede usar en proyectos de Excel, consulte los siguientes temas:  
  
-   [Chart Control](../vsto/chart-control.md)  
  
-   [ListObject (control)](../vsto/listobject-control.md)  
  
-   [NamedRange (control)](../vsto/namedrange-control.md)  
  
-   [XmlMappedRange (control)](../vsto/xmlmappedrange-control.md)  
  
## <a name="see-also"></a>Vea también  
 [Cómo: rellenar los controles ListObject con datos](../vsto/how-to-fill-listobject-controls-with-data.md)   
 [Cómo: agregar controles Chart a hojas de cálculo](../vsto/how-to-add-chart-controls-to-worksheets.md)   
 [Cómo: agregar controles ListObject a hojas de cálculo](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [Cómo: agregar controles NamedRange a hojas de cálculo](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Cómo: agregar controles XMLMappedRange a hojas de cálculo](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)   
 [Cómo: cambiar el tamaño de los controles NamedRange](../vsto/how-to-resize-namedrange-controls.md)   
 [Cómo: cambiar el tamaño de los controles ListObject](../vsto/how-to-resize-listobject-controls.md)   
 [Cómo: validar datos cuando se agrega una nueva fila a un ListObject Control](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md)   
 [Cómo: asignar columnas ListObject a datos](../vsto/how-to-map-listobject-columns-to-data.md)   
 [Tutorial: Programar basándose en eventos de un Control NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)   
 [Extender documentos de Word y libros de Excel en complementos VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controles en documentos de Office](../vsto/controls-on-office-documents.md)   
 [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)   
 [Limitaciones de programación de elementos y controles Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  