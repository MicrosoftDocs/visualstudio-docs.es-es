---
title: 'Cómo: almacenar datos en caché para su uso sin conexión o en un servidor'
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ce295e299e4accb2d79655675f6264a1497b8d69
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546190"
---
# <a name="how-to-cache-data-for-use-offline-or-on-a-server"></a>Cómo: almacenar datos en caché para su uso sin conexión o en un servidor
  Puede marcar un elemento de datos para almacenarlo en la caché del documento, de modo que esté disponible sin conexión. Esto también permite que otros códigos manipulen los datos del documento cuando el documento se almacena en un servidor.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Puede marcar un elemento de datos para almacenarlo en la memoria caché cuando el elemento de datos se declara en el código, o bien, si está utilizando <xref:System.Data.DataSet> , estableciendo una propiedad en la ventana **propiedades** . Si está almacenando en caché un elemento de datos que no es <xref:System.Data.DataSet> o <xref:System.Data.DataTable> , asegúrese de que cumple los criterios para almacenar en caché en el documento. Para obtener más información, vea [almacenar datos en caché](../vsto/caching-data.md).

> [!NOTE]
> Los conjuntos de datos creados con Visual Basic marcados como **Cached** y **WithEvents** (incluidos los conjuntos de datos que se arrastran desde la ventana **orígenes de datos** o el cuadro de **herramientas** que tienen la propiedad **CacheInDocument** establecida en **true**) tienen un carácter de subrayado como prefijo en sus nombres en la memoria caché. Por ejemplo, si crea un conjunto de DataSet y le asigna el nombre **Customers**, el <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> nombre se **_Customersrá** en la memoria caché. Al utilizar <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> para tener acceso a este elemento almacenado en caché, debe especificar **_Customers** en lugar de **los clientes**.

### <a name="to-cache-data-in-the-document-using-code"></a>Para almacenar en caché los datos del documento mediante código

1. Declare un campo público o una propiedad para el elemento de datos como miembro de una clase de elemento host del proyecto, como la `ThisDocumen` clase t en un proyecto de Word o la `ThisWorkbook` clase en un proyecto de Excel.

2. Aplique el <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atributo al miembro para marcar el elemento de datos que se va a almacenar en la memoria caché de datos del documento. En el ejemplo siguiente se aplica este atributo a una declaración de campo para <xref:System.Data.DataSet> .

     [!code-csharp[Trin_VstcoreDataExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreDataExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#11)]

3. Agregue código para crear una instancia del elemento de datos y, si procede, para cargarla desde la base de datos.

     El elemento de datos solo se carga cuando se crea por primera vez; a partir de ese momento, la caché permanece con el documento y debe escribir otro código para actualizarlo.

### <a name="to-cache-a-dataset-in-the-document-by-using-the-properties-window"></a>Para almacenar en caché un conjunto de documentos en el documento mediante el ventana Propiedades

1. Agregue el conjunto de datos al proyecto mediante herramientas en el diseñador de Visual Studio, por ejemplo, agregando un origen de datos al proyecto mediante la ventana **orígenes de datos** .

2. Cree una instancia del conjunto de información si aún no tiene una, y seleccione la instancia en el diseñador.

3. En la ventana **propiedades** , establezca la propiedad **CacheInDocument** en **true**.

     Para obtener más información, vea [propiedades en proyectos de Office](../vsto/properties-in-office-projects.md).

4. En la ventana **propiedades** , establezca la propiedad **Modifiers** en **Public** (de forma predeterminada, es **Internal**).

## <a name="see-also"></a>Consulte también
- [Datos de caché](../vsto/caching-data.md)
- [Cómo: almacenar en caché un origen de datos en un documento de Office mediante programación](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
- [Cómo: almacenar datos en caché en un documento protegido mediante contraseña](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [Acceder a los datos de documentos en el servidor](../vsto/accessing-data-in-documents-on-the-server.md)
- [Guardar datos](../data-tools/save-data-back-to-the-database.md)
