---
title: Desactivar restricciones al llenar un conjunto de DataSet | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6646f669bf2c465d8e0f705f8fba956b979952ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667163"
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>Desactivar restricciones al llenar un conjunto de datos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si un conjunto de DataSet contiene restricciones (como las restricciones Foreign Key), Theycan genera errores relacionados con el orden de las operaciones que se realizan en el conjunto de DataSet. Por ejemplo, la carga de registros secundarios antes de los registros primarios de loadingrelated puede infringir una restricción y producir un error. Tan pronto como se carga un registro secundario, la restricción comprueba el registro principal existente y produce un error.

 Si no hubiera ningún mecanismo para permitir la suspensión temporal de la restricción, se produciría un error cada vez que se intentara cargar un registro en la tabla secundaria. Otra manera de suspender todas las restricciones de un conjunto de datos es mediante las propiedades <xref:System.Data.DataRow.BeginEdit%2A> y <xref:System.Data.DataRow.EndEdit%2A>.

> [!NOTE]
> Los eventos de validación (por ejemplo, <xref:System.Data.DataTable.ColumnChanging> y <xref:System.Data.DataTable.RowChanging> ) no se generarán cuando se desactiven las restricciones.

### <a name="to-suspend-update-constraints-programmatically"></a>Para suspender las restricciones de actualización mediante programación

- En el ejemplo siguiente se muestra cómo desactivar temporalmente la comprobación de restricciones de un conjunto de datos:

     [!code-csharp[VbRaddataEditing#10](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#10)]
     [!code-vb[VbRaddataEditing#10](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#10)]

### <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>Para suspender las restricciones de actualización mediante el Diseñador de DataSet

1. Abra su conjunto de datos en el Diseñador de Dataset. Para obtener más información, consulte [Cómo: abrir un conjunto de datos en el diseñador de DataSet](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).

2. En la ventana **Propiedades** , establezca la propiedad <xref:System.Data.DataSet.EnforceConstraints%2A> en `false`.

## <a name="see-also"></a>Consulte también
 [Rellenar conjuntos de valores mediante](../data-tools/fill-datasets-by-using-tableadapters.md) [relaciones de TableAdapter en conjuntos de](../data-tools/relationships-in-datasets.md) objetos
