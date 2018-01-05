---
title: Desactivar restricciones al llenar un conjunto de datos | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DataRow.BeginEdit
- DataRow.EndEdit
- DataRow.CancelEdit
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- updating datasets, constraints
- constraints [Visual Basic], datasets
- datasets [Visual Basic], constraints
- constraints [Visual Basic], suspending during dataset update
ms.assetid: 553f7d0c-2faa-4c17-b226-dd02855bf1dc
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 88c8687511dd600802cc7c6ecdc12f0827fd7f6f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>Desactivar restricciones al llenar un conjunto de datos
Si un conjunto de datos contiene restricciones (como las restricciones de clave externa), pueden producir errores relacionados con el orden de las operaciones que se realizan en el conjunto de datos. Por ejemplo, cargar registros secundarios antes de la carga relaciona los registros primarios pueden infringen una restricción y se producirá un error. Tan pronto como se carga un registro secundario, la restricción comprueba el registro principal existente y genera un error.  
  
 Si no hubiera ningún mecanismo para permitir la suspensión temporal de la restricción, se produciría un error cada vez que se intentara cargar un registro en la tabla secundaria. Otra manera de suspender todas las restricciones de un conjunto de datos es mediante las propiedades <xref:System.Data.DataRow.BeginEdit%2A> y <xref:System.Data.DataRow.EndEdit%2A>.  
  
> [!NOTE]
>  Eventos de validación (por ejemplo, <xref:System.Data.DataTable.ColumnChanging> y<xref:System.Data.DataTable.RowChanging>) no se producen cuando las restricciones están desactivadas.  
  
### <a name="to-suspend-update-constraints-programmatically"></a>Para suspender las restricciones de actualización mediante programación  
  
-   En el ejemplo siguiente se muestra cómo desactivar temporalmente la comprobación de restricciones de un conjunto de datos:  
  
     [!code-csharp[VbRaddataEditing#10](../data-tools/codesnippet/CSharp/turn-off-constraints-while-filling-a-dataset_1.cs)]
     [!code-vb[VbRaddataEditing#10](../data-tools/codesnippet/VisualBasic/turn-off-constraints-while-filling-a-dataset_1.vb)]  
  
### <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>Para suspender las restricciones de actualización mediante el Diseñador de DataSet  
  
1.  Abra su conjunto de datos en el **Diseñador de Dataset**. Para obtener más información, consulte [Tutorial: crear un conjunto de datos en el Diseñador de Dataset](walkthrough-creating-a-dataset-with-the-dataset-designer.md).  
  
2.  En el **propiedades** ventana, establezca el <xref:System.Data.DataSet.EnforceConstraints%2A> propiedad `false`.  
  
## <a name="see-also"></a>Vea también  
 [Rellenar conjuntos de datos mediante el uso de los TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Relaciones en conjuntos de datos](../data-tools/relationships-in-datasets.md)