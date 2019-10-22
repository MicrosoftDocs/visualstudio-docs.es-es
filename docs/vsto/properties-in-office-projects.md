---
title: Propiedades de los proyectos de Office
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9fc2a0774206eac0c9295a425d81555ffdd3cac8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62561374"
---
# <a name="properties-in-office-projects"></a>Propiedades de los proyectos de Office
  Hay varias propiedades importantes que están disponibles para los proyectos de Office en Visual Studio. Se puede obtener acceso a estas propiedades en la ventana **Propiedades** .

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="namespace-for-host-item"></a>Namespace para el elemento host
 Utilice la propiedad **Espacio de nombres para el elemento host** para cambiar el espacio de nombres de las clases de elementos host (por ejemplo, las clases `ThisAddIn`, `ThisWorkbook`o `ThisDocument` ) en proyectos de Visual C#. Esta propiedad aparece en la **propiedades** ventana cuando se selecciona el nodo de documento en un proyecto de nivel de documento (como *ExcelWorkbook1.xlsx* o *WordDocument1.docx* ) o el nodo de la aplicación en un proyecto complemento de VSTO (como Excel o Word) en **el Explorador de soluciones**.

 Cuando se crea un proyecto de Visual C# de Office, los elementos host reciben un espacio de nombres basado en el nombre del proyecto. Se recomienda utilizar la propiedad **Espacio de nombres para el elemento host** para cambiar el espacio de nombres en lugar de para modificar los archivos de código directamente. Cuando se utiliza esta propiedad, se cambia el espacio de nombres en los archivos de código generados (ocultos), así como en los archivos de código visibles.

## <a name="cacheindocument"></a>CacheInDocument
 La propiedad **CacheInDocument** aparece en la ventana **Propiedades** de los proyectos de nivel de documento cuando se selecciona una instancia de un <xref:System.Data.DataSet> en el diseñador de Visual Studio. Solo es posible almacenar en caché los miembros públicos; asegúrese de que la propiedad **Modificadores** esté establecida en **Público** si desea almacenar en caché un <xref:System.Data.DataSet>.

 Esta propiedad toma un valor booleano:

- Seleccione **true** para almacenar en caché el conjunto de datos en el documento.

- Seleccione **false** si no desea que el conjunto de datos se almacene en caché en el documento.

  Para obtener más información acerca de la caché de datos, vea [en caché los datos en las personalizaciones de nivel de documento](../vsto/cached-data-in-document-level-customizations.md).

## <a name="value2"></a>Value2
 La propiedad **Value2** solo está disponible para los proyectos de libro o plantilla de Excel. Aparece en el nodo de propiedad **Databindings** de la ventana **Propiedades** cuando se selecciona un control <xref:Microsoft.Office.Tools.Excel.NamedRange> en el diseñador de hojas de cálculo.

 Utilice la propiedad **Value2** de la ventana **Propiedades** para enlazar la propiedad <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> del <xref:Microsoft.Office.Tools.Excel.NamedRange> a un campo del origen de datos.

## <a name="see-also"></a>Vea también
- [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)
- [Introducción a las plantillas de proyecto de Office](../vsto/office-project-templates-overview.md)
- [Eventos en proyectos de Office](../vsto/events-in-office-projects.md)
