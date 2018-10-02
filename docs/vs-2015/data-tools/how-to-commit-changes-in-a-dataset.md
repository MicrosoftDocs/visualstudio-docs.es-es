---
title: 'Cómo: Confirmar cambios en un conjunto de datos | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DataSet.AcceptChanges
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- datasets [Visual Basic], committing changes
ms.assetid: 51931353-4d22-4e35-a9ef-6f2b44e1f7d9
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 40acd2a706ef7bc00ea1f90e51e90705be5658c3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47577981"
---
# <a name="how-to-commit-changes-in-a-dataset"></a>Cómo: Confirmar cambios en un conjunto de datos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cuando realice cambios a los registros en un conjunto de datos mediante la actualización, inserción y eliminación de registros, el conjunto de datos mantiene versiones originales y actuales de los registros. Además, cada fila del <xref:System.Data.DataRow.RowState%2A> realiza un seguimiento de la propiedad si los registros están en su estado original o han sido actualizados, insertados o eliminadas. Esta información es útil cuando necesita encontrar una versión concreta de una fila. Normalmente, obtendría un subconjunto de todos los registros modificados para enviarlo a otro proceso. Para obtener más información, consulte [Cómo: recuperar filas modificadas](http://msdn.microsoft.com/library/6ff0cbd0-5253-48e7-888a-144d56c2e0a9). Después de haber procesado todas las filas modificadas, puede confirmar los cambios mediante una llamada a la `AcceptChanges` método de la <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, o <xref:System.Data.DataRow>. El `AcceptChanges` método se llama automáticamente al llamar a los métodos de actualización de un [TableAdapter](../data-tools/tableadapter-overview.md) o adaptador de datos. Llamar a `AcceptChanges` después de enviar los cambios realizados en una base de datos.  
  
 Cuando se llama a <xref:System.Data.DataSet.AcceptChanges%2A> en el <xref:System.Data.DataSet>, cualquier <xref:System.Data.DataRow> objetos todavía en modo de edición finalización correctamente sus modificaciones. El <xref:System.Data.DataRow.RowState%2A> propiedad de cada uno <xref:System.Data.DataRow> también cambia; <xref:System.Data.DataRowState> y <xref:System.Data.DataRowState> filas se convierten en <xref:System.Data.DataRowState>, y <xref:System.Data.DataRowState> se quitan las filas.  
  
 Si el <xref:System.Data.DataSet> contiene <xref:System.Data.ForeignKeyConstraint> objetos, invocar el <xref:System.Data.DataSet.AcceptChanges%2A> también hace que el método la <xref:System.Data.AcceptRejectRule> aplicándose.  
  
### <a name="to-commit-changes-in-a-dataset"></a>Para confirmar los cambios en un conjunto de datos  
  
-   Llamar a la `AcceptChanges` método ya sea un <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, o <xref:System.Data.DataRow> para confirmar los cambios en los objetos.  
  
     El ejemplo siguiente muestra cómo llamar a la `AcceptChanges` método para confirmar los cambios en el `Customers` tabla después de actualizar un origen de datos:  
  
     [!code-csharp[VbRaddataEditing#11](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#11)]
     [!code-vb[VbRaddataEditing#11](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#11)]  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>   
 <xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>   
 <xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>   
 [Guardar datos](../data-tools/saving-data.md)   
 [Cómo: recuperar las filas modificadas](http://msdn.microsoft.com/library/6ff0cbd0-5253-48e7-888a-144d56c2e0a9)