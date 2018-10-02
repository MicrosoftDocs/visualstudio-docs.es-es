---
title: Desactivar restricciones al llenar un conjunto de datos | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DataRow.BeginEdit
- DataRow.EndEdit
- DataRow.CancelEdit
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- updating datasets, constraints
- constraints [Visual Basic], datasets
- datasets [Visual Basic], constraints
- constraints [Visual Basic], suspending during dataset update
ms.assetid: 553f7d0c-2faa-4c17-b226-dd02855bf1dc
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4b14830b7ed4922b4e383ef245c0366c184b606e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47575516"
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>Desactivar restricciones al llenar un conjunto de datos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [desactivar restricciones al llenar un conjunto de datos](https://docs.microsoft.com/visualstudio/data-tools/turn-off-constraints-while-filling-a-dataset).  
  
  
Si un conjunto de datos contiene restricciones (como las restricciones de clave externa), sino generar errores relacionados con el orden de las operaciones que se realizan en el conjunto de datos. Por ejemplo, el cargar registros secundarios antes de los registros primarios de loadingrelated puede infringen una restricción y producir un error. Tan pronto como se carga un registro secundario, la restricción comprueba el registro principal existente y genera un error.  
  
 Si no hubiera ningún mecanismo para permitir la suspensión temporal de la restricción, se produciría un error cada vez que se intentara cargar un registro en la tabla secundaria. Otra manera de suspender todas las restricciones de un conjunto de datos es mediante las propiedades <xref:System.Data.DataRow.BeginEdit%2A> y <xref:System.Data.DataRow.EndEdit%2A>.  
  
> [!NOTE]
>  Eventos de validación (por ejemplo, <xref:System.Data.DataTable.ColumnChanging> y<xref:System.Data.DataTable.RowChanging>) no se genera cuando las restricciones están desactivadas.  
  
### <a name="to-suspend-update-constraints-programmatically"></a>Para suspender las restricciones de actualización mediante programación  
  
-   En el ejemplo siguiente se muestra cómo desactivar temporalmente la comprobación de restricciones de un conjunto de datos:  
  
     [!code-csharp[VbRaddataEditing#10](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#10)]
     [!code-vb[VbRaddataEditing#10](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#10)]  
  
### <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>Para suspender las restricciones de actualización mediante el Diseñador de DataSet  
  
1.  Abra el conjunto de datos en el [crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md). Para obtener más información, consulte [Cómo: abrir un conjunto de datos en el Diseñador de Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  En el **propiedades** ventana, establezca el <xref:System.Data.DataSet.EnforceConstraints%2A> propiedad `false`.  
  
## <a name="see-also"></a>Vea también  
 [Llenar conjuntos de datos mediante TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Relaciones en conjuntos de datos](../data-tools/relationships-in-datasets.md)

