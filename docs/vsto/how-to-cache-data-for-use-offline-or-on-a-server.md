---
title: Procedimiento Almacenar en caché datos para su uso sin conexión o en un servidor
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], server use
- Office applications [Office development in Visual Studio], data
- datasets [Office development in Visual Studio], caching
- offline data [Office development in Visual Studio]
- data [Office development in Visual Studio], caching
- data caching [Office development in Visual Studio], offline use
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 671b4c18963be4f9c81e15fe33e5d68a410655c9
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/27/2018
ms.locfileid: "53804661"
---
# <a name="how-to-cache-data-for-use-offline-or-on-a-server"></a>Procedimiento Almacenar en caché datos para su uso sin conexión o en un servidor
  Puede marcar un elemento de datos en la memoria caché en el documento, por lo que esté disponible sin conexión. Esto también permite para los datos en el documento que se va a ser manipulados por otro código cuando el documento está almacenado en un servidor.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Puede marcar un elemento de datos en la memoria caché cuando se declara el elemento de datos en el código o, si está utilizando un <xref:System.Data.DataSet>, estableciendo una propiedad el **propiedades** ventana. Si se almacenan en caché un elemento de datos que no es un <xref:System.Data.DataSet> o <xref:System.Data.DataTable>, asegúrese de que cumple los criterios para que se va a almacenar en caché en el documento. Para obtener más información, consulte [almacenar en caché datos](../vsto/caching-data.md).

> [!NOTE]
>  Los conjuntos de datos creados con Visual Basic que están marcados como **Cached** y **WithEvents** (incluidos los conjuntos de datos que se arrastran desde el **orígenes de datos** ventana o **Cuadro de herramientas** que tienen el **CacheInDocument** propiedad establecida en **True**) tiene un carácter de subrayado en sus nombres en la memoria caché. Por ejemplo, si crea un conjunto de datos y asígnele el nombre **clientes**, <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> nombre será **_Customers** en la memoria caché. Cuando usas <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> para acceder a esta elemento almacenado en caché, debe especificar **_Customers** en lugar de **clientes**.

### <a name="to-cache-data-in-the-document-using-code"></a>Para almacenar datos en caché en el documento mediante código

1.  Declarar un campo público o propiedad del elemento de datos como un miembro de una clase de elemento host en el proyecto, como el `ThisDocumen`clase t en un proyecto de Word o el `ThisWorkbook` clase en un proyecto de Excel.

2.  Aplicar el <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atributo al miembro para marcar el elemento de datos se almacenen en caché de datos del documento. El ejemplo siguiente aplica este atributo a una declaración de campo para un <xref:System.Data.DataSet>.

     [!code-csharp[Trin_VstcoreDataExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreDataExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#11)]

3.  Agregue código para crear una instancia del elemento de datos y, si procede, realizar la carga desde la base de datos.

     El elemento de datos solo se carga cuando se crea por primera vez; a partir de entonces, la memoria caché permanece con el documento y se debe escribir otro código para actualizarlo.

### <a name="to-cache-a-dataset-in-the-document-by-using-the-properties-window"></a>Para almacenar en caché un conjunto de datos en el documento mediante el uso de la ventana Propiedades

1.  Agregar el conjunto de datos al proyecto mediante el uso de herramientas del Diseñador de Visual Studio, por ejemplo, mediante la adición de un origen de datos al proyecto mediante el **orígenes de datos** ventana.

2.  Cree una instancia del conjunto de datos si aún no tiene uno y seleccione la instancia en el diseñador.

3.  En el **propiedades** ventana, establezca el **CacheInDocument** propiedad **True**.

     Para obtener más información, consulte [propiedades en proyectos de Office](../vsto/properties-in-office-projects.md).

4.  En el **propiedades** ventana, establezca el **modificadores** propiedad **pública** (de forma predeterminada es **interno**).

## <a name="see-also"></a>Vea también
 [Almacenar en caché datos](../vsto/caching-data.md) [Cómo: Almacenar en caché mediante programación un origen de datos en un documento de Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md) [Cómo: Almacenar en caché datos en un documento protegido por contraseña](../vsto/how-to-cache-data-in-a-password-protected-document.md) [tener acceso a datos de documentos en el servidor](../vsto/accessing-data-in-documents-on-the-server.md) [guardar los datos](../data-tools/saving-data.md)
