---
title: Propiedades de proyectos de Office | Documentos de Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Trust Assemblies Location property
- Cache in Document property
- properties [Office development in Visual Studio]
- Namespace for Host Item property
- Office projects [Office development in Visual Studio], properties
- projects [Office development in Visual Studio], properties
- Value2 property
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 47af1dae914528a3a338503989e53f081dfffde5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="properties-in-office-projects"></a>Propiedades de los proyectos de Office
  Hay varias propiedades importantes que están disponibles para los proyectos de Office en Visual Studio. Se puede obtener acceso a estas propiedades en la ventana **Propiedades** .  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="namespace-for-host-item"></a>Espacio de nombres para el elemento host  
 Utilice la propiedad **Espacio de nombres para el elemento host** para cambiar el espacio de nombres de las clases de elementos host (por ejemplo, las clases `ThisAddIn`, `ThisWorkbook`o `ThisDocument` ) en proyectos de Visual C#. Esta propiedad aparece en la ventana **Propiedades** cuando se selecciona el nodo de documento de un proyecto de nivel de documento (como ExcelWorkbook1.xlsx o WordDocument1.docx) o el nodo de aplicación de un proyecto de complemento de VSTO (como Excel o Word) en el **Explorador de soluciones**.  
  
 Cuando se crea un proyecto de Visual C# de Office, los elementos host reciben un espacio de nombres basado en el nombre del proyecto. Se recomienda utilizar la propiedad **Espacio de nombres para el elemento host** para cambiar el espacio de nombres en lugar de para modificar los archivos de código directamente. Cuando se utiliza esta propiedad, se cambia el espacio de nombres en los archivos de código generados (ocultos), así como en los archivos de código visibles.  
  
## <a name="cacheindocument"></a>CacheInDocument  
 La propiedad **CacheInDocument** aparece en la ventana **Propiedades** de los proyectos de nivel de documento cuando se selecciona una instancia de un <xref:System.Data.DataSet> en el diseñador de Visual Studio. Solo es posible almacenar en caché los miembros públicos; asegúrese de que la propiedad **Modificadores** esté establecida en **Público** si desea almacenar en caché un <xref:System.Data.DataSet>.  
  
 Esta propiedad toma un valor booleano:  
  
-   Seleccione **true** para almacenar en caché el conjunto de datos en el documento.  
  
-   Seleccione **false** si no desea que el conjunto de datos se almacene en caché en el documento.  
  
 Para obtener más información sobre el almacenamiento de datos en caché, vea [Cached Data in Document-Level Customizations](../vsto/cached-data-in-document-level-customizations.md).  
  
## <a name="value2"></a>Value2  
 La propiedad **Value2** solo está disponible para los proyectos de libro o plantilla de Excel. Aparece en el nodo de propiedad **Databindings** de la ventana **Propiedades** cuando se selecciona un control <xref:Microsoft.Office.Tools.Excel.NamedRange> en el diseñador de hojas de cálculo.  
  
 Utilice la propiedad **Value2** de la ventana **Propiedades** para enlazar la propiedad <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> del <xref:Microsoft.Office.Tools.Excel.NamedRange> a un campo del origen de datos.  
  
## <a name="see-also"></a>Vea también  
 [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)   
 [Información general de plantillas de proyecto de Office](../vsto/office-project-templates-overview.md)   
 [Eventos de los proyectos de Office](../vsto/events-in-office-projects.md)  
  
  