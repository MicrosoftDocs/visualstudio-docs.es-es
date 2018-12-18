---
title: 'Cómo: rellenar un conjunto de datos | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- TableAdapter.GetData
- TableAdapter.Fill
- datasets [Visual Basic], filling
- DataTable objects, loading
- data [Visual Basic], loading into datasets
ms.assetid: 7ab436d4-54ba-4621-902f-3f193279e18c
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: f36aa2dac656f6fd27b656d0ddfb58a758eb6487
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49296002"
---
# <a name="how-to-fill-a-dataset-with-data"></a>Cómo: rellenar un conjunto de datos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La frase "rellenar un conjunto de datos con datos" hace referencia al cargar datos en el individuo <xref:System.Data.DataTable> objetos que componen el conjunto de datos. Rellenar las tablas de datos mediante la ejecución de consultas de TableAdapter o ejecutando el adaptador de datos (por ejemplo, <xref:System.Data.SqlClient.SqlDataAdapter>) comandos.  
  
 Si debe utilizar TableAdapters o adaptadores de datos depende de cómo haya creado el conjunto de datos. Si ha utilizado las herramientas de diseño en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], como el [Asistente para configuración de origen de datos](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f), el conjunto de datos contiene los TableAdapters. Para obtener más información sobre los TableAdapters, vea [información general sobre TableAdapter](../data-tools/tableadapter-overview.md). Si ha creado el conjunto de datos mediante programación, normalmente deberá crear adaptadores de datos para cargar datos en las tablas de datos.  
  
> [!NOTE]
>  Al arrastrar elementos desde el [ventana Orígenes de datos](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) en un formulario, el código para rellenar la tabla de datos con los datos se agrega automáticamente a la `Form_Load` controlador de eventos. Abrir el formulario en el editor de código para ver la sintaxis exacta para rellenar las tablas específicas. Si no desea rellenar la tabla cuando se carga el formulario, puede mover este código a algún otro método o quítelo totalmente.  
  
## <a name="filling-a-dataset-using-a-tableadapter"></a>Rellenar un conjunto de datos mediante un TableAdapter  
 Puede llamar a una consulta de TableAdapter para cargar datos en tablas de datos en un conjunto de datos. Pase el <xref:System.Data.DataTable> desea rellenar a la consulta de TableAdapter. Si la consulta acepta parámetros, pasarlas al método así. Si el conjunto de datos contiene varias tablas, debe tener los TableAdapters independientes para cada tabla y, por tanto, debe rellenar cada tabla por separado.  
  
> [!NOTE]
>  De forma predeterminada, cada vez que ejecute una consulta de TableAdapter, se borran los datos de la tabla antes de los resultados de la consulta que se va a cargar en la tabla. Puede mantener los datos existentes en la tabla y anexar los resultados estableciendo el TableAdapter `ClearBeforeFill` propiedad `false`.  
  
#### <a name="to-fill-a-dataset-with-data-using-a-tableadapter"></a>Para rellenar un conjunto de datos con datos mediante un TableAdapter  
  
1.  Abra el formulario o componente en el **Editor de código**.  
  
2.  Agregue el código en cualquier lugar en su aplicación donde necesite cargar una tabla con datos. Si la consulta no toma parámetros, pase el <xref:System.Data.DataTable> que desea rellenar. El código debe ser similar al siguiente:  
  
     [!code-csharp[VbRaddataFillingAndExecuting#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#4)]
     [!code-vb[VbRaddataFillingAndExecuting#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#4)]  
  
3.  Si la consulta acepta parámetros, pase el <xref:System.Data.DataTable> desea relleno y los parámetros esperados por la consulta. Dependiendo de los parámetros reales en la consulta, el código tendría un aspecto similar a los siguientes ejemplos:  
  
     [!code-csharp[VbRaddataFillingAndExecuting#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#5)]
     [!code-vb[VbRaddataFillingAndExecuting#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#5)]  
  
## <a name="filling-a-dataset-using-a-dataadapter"></a>Rellenar un conjunto de datos mediante un objeto DataAdapter  
 Se llama el adaptador de datos `Fill` método. Esto hace que el adaptador ejecutar la instrucción SQL o procedimiento almacenado hace referencia en su `SelectCommand` propiedad y colocar los resultados en una tabla en el conjunto de datos. Si el conjunto de datos contiene varias tablas, debe tener adaptadores de datos independiente para cada tabla y, por tanto, debe rellenar cada tabla por separado.  
  
#### <a name="to-fill-a-dataset-with-data-using-a-dataadapter"></a>Para rellenar un conjunto de datos con datos mediante un objeto DataAdapter  
  
-   Llame a la <xref:System.Data.Common.DataAdapter.Fill%2A> método de la <xref:System.Data.Common.DataAdapter>, pasando el <xref:System.Data.DataSet> o <xref:System.Data.DataTable> para cargar los datos. Por ejemplo:  
  
     [!code-csharp[VbRaddataFillingAndExecuting#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#6)]
     [!code-vb[VbRaddataFillingAndExecuting#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#6)]  
  
     Normalmente, debe proporcionar el nombre de la <xref:System.Data.DataTable> para cargar los datos. Si se pasa el nombre de un <xref:System.Data.DataSet> en lugar de una tabla de datos específica, un <xref:System.Data.DataTable> denominado `Table1` se agrega al conjunto de datos y se cargan con los resultados de la base de datos (en lugar de cargar los datos en una existente <xref:System.Data.DataTable> del conjunto de datos). Para obtener más información, consulte [llenar un DataSet desde un objeto DataAdapter](http://msdn.microsoft.com/library/3fa0ac7d-e266-4954-bfac-3fbe2f913153).  
  
## <a name="see-also"></a>Vea también  
 [Llenar conjuntos de datos mediante TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Captura de datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Preparar su aplicación para recibir datos](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Edición de datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validación de datos](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Guardar datos](../data-tools/saving-data.md)