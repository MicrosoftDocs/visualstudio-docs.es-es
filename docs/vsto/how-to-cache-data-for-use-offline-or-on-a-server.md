---
title: 'Cómo: Almacenar en caché datos para su uso sin conexión o en un servidor'
description: Marque un elemento de datos que se almacenará en caché en el documento para que esté disponible sin conexión. Esto permite que otros código manipulen los datos del documento.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 07d7a33d90fd9d05c041ddc27f92a5b6a59bb75e
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825997"
---
# <a name="how-to-cache-data-for-use-offline-or-on-a-server"></a>Cómo: Almacenar en caché datos para su uso sin conexión o en un servidor
  Puede marcar un elemento de datos que se almacenará en caché en el documento para que esté disponible sin conexión. Esto también permite que otros código manipulen los datos del documento cuando el documento se almacena en un servidor.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Puede marcar un elemento de datos que se almacenará en caché cuando el elemento de datos se declare en el código o, si usa , estableciendo una propiedad en la <xref:System.Data.DataSet> **ventana** Propiedades. Si va a almacenar en caché un elemento de datos que no es o , asegúrese de que cumple los criterios para almacenar en caché <xref:System.Data.DataSet> <xref:System.Data.DataTable> en el documento. Para obtener más información, vea Almacenar [en caché los datos](../vsto/caching-data.md).

> [!NOTE]
> Los conjuntos de datos creados mediante Visual Basic marcados como **Cached** y **WithEvents** (incluidos los conjuntos de datos que se arrastran desde la ventana Orígenes de datos o el Cuadro de herramientas que tienen la propiedad  **CacheInDocument** establecida en **True)** tienen un carácter de subrayado precedido por sus nombres en la memoria caché.  Por ejemplo, si crea un conjunto de datos y lo llama **Customers**, el nombre se <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> **_Customers** en la memoria caché. Cuando se usa <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> para acceder a  este elemento almacenado en caché, debe especificar _Customers en lugar de **Customers**.

### <a name="to-cache-data-in-the-document-using-code"></a>Para almacenar en caché los datos del documento mediante código

1. Declare un campo o propiedad público para el elemento de datos como miembro de una clase de elemento host en el proyecto, como la clase t en un proyecto de Word o la clase de un proyecto `ThisDocumen` `ThisWorkbook` de Excel.

2. Aplique el atributo al miembro para marcar el elemento de datos que se <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> va a almacenar en la caché de datos del documento. En el ejemplo siguiente se aplica este atributo a una declaración de campo para <xref:System.Data.DataSet> .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet11":::

3. Agregue código para crear una instancia del elemento de datos y, si procede, para cargarlo desde la base de datos.

     El elemento de datos solo se carga cuando se crea por primera vez; a partir de ese momento, la memoria caché permanece con el documento y debe escribir otro código para actualizarlo.

### <a name="to-cache-a-dataset-in-the-document-by-using-the-properties-window"></a>Para almacenar en caché un conjunto de datos en el documento mediante el ventana Propiedades

1. Agregue el conjunto de datos al proyecto mediante herramientas del diseñador de Visual Studio, por ejemplo, agregando un origen de datos al proyecto mediante la **ventana Orígenes de** datos.

2. Cree una instancia del conjunto de datos si aún no tiene una y seleccione la instancia en el diseñador.

3. En la **ventana** Propiedades, establezca la **propiedad CacheInDocument** en **True.**

     Para obtener más información, vea [Propiedades en proyectos de Office.](../vsto/properties-in-office-projects.md)

4. En la **ventana** Propiedades, establezca la propiedad **Modificadores** en **Público** (de forma predeterminada es **Interna).**

## <a name="see-also"></a>Consulte también
- [Datos de caché](../vsto/caching-data.md)
- [Cómo: Almacenar en caché mediante programación un origen de datos en un documento de Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
- [Cómo: Almacenar en caché datos en un documento protegido con contraseña](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [Acceso a datos en documentos en el servidor](../vsto/accessing-data-in-documents-on-the-server.md)
- [Guardar datos](../data-tools/save-data-back-to-the-database.md)
