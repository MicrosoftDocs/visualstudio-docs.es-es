---
title: Editar datos en conjuntos de datos | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- datasets [Visual Basic], editing data
- data [Visual Studio], editing in datasets
ms.assetid: 50d5c580-fbf7-408f-be70-e63ac4f4d0eb
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9962bb1dbeef089d409cbe100daa37777b45e67d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63425383"
---
# <a name="edit-data-in-datasets"></a>Editar datos en conjuntos de datos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Editar tablas de datos al igual que editar los datos en una tabla en cualquier base de datos. El proceso puede incluir insertar, actualizar y eliminar registros en la tabla. En un formulario enlazado a datos, puede especificar cuáles son los campos editables del usuario. En esos casos, la infraestructura de enlace de datos controla todo el seguimiento de cambios para que los cambios se puedan enviar a la base de datos más adelante. Si realiza ediciones mediante programación a los datos y tiene pensado enviar los cambios a la base de datos, debe usar los objetos y métodos que realizan el seguimiento de cambios para usted.  
  
 Además de cambiar los datos reales, también puede consultar un <xref:System.Data.DataTable> para devolver filas específicas de datos. Por ejemplo, podría consultar filas individuales, versiones específicas de filas (originales y propuestas), las filas que han cambiado o filas con errores.  
  
## <a name="to-edit-rows-in-a-dataset"></a>Editar filas en un conjunto de datos  
 Para editar una fila existente en un <xref:System.Data.DataTable>, será preciso que encuentre el <xref:System.Data.DataRow> que desea editar y, a continuación, asignar los valores actualizados a las columnas que desee.  
  
 Si no conoce el índice de la fila que desea editar, utilice el `FindBy` para buscar la clave principal:  
  
 [!code-csharp[VbRaddataEditing#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#3)]
 [!code-vb[VbRaddataEditing#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#3)]  
  
 Si conoce el índice de fila, que puede tener acceso a y edita filas como sigue:  
  
 [!code-csharp[VbRaddataEditing#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#5)]
 [!code-vb[VbRaddataEditing#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#5)]  
  
## <a name="to-insert-new-rows-into-a-dataset"></a>Para insertar nuevas filas en un conjunto de datos  
 Las aplicaciones que usan los controles enlazados a datos normalmente agregan nuevos registros a través de la **Agregar nuevo** situado en un [BindingNavigator Control](http://msdn.microsoft.com/library/18c1e2a5-9834-40d3-9b2e-2b545e4e769e).  
  
 Para agregar manualmente los nuevos registros a un conjunto de datos, cree una nueva fila de datos llamando al método en la tabla de datos. A continuación, agregue la fila a la <xref:System.Data.DataRow> colección (<xref:System.Data.DataTable.Rows%2A>) de la <xref:System.Data.DataTable>:  
  
 [!code-csharp[VbRaddataEditing#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#1)]
 [!code-vb[VbRaddataEditing#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#1)]  
  
 Fin de conservar la información que necesita el conjunto de datos enviar actualizaciones al origen de datos, utilice el <xref:System.Data.DataRow.Delete%2A> método para quitar las filas en una tabla de datos. Por ejemplo, si la aplicación utiliza un TableAdapter (o <xref:System.Data.Common.DataAdapter>), lo TableAdapter `Update` método elimina filas de la base de datos que tienen un <xref:System.Data.DataRow.RowState%2A> de <xref:System.Data.DataRowState>.  
  
 Si la aplicación no necesita enviar actualizaciones a un origen de datos, a continuación, es posible quitar registros accediendo directamente a la colección de filas de datos (<xref:System.Data.DataRowCollection.Remove%2A>).  
  
#### <a name="to-delete-records-from-a-data-table"></a>Para eliminar registros de una tabla de datos  
  
- Llame a la <xref:System.Data.DataRow.Delete%2A> método de un <xref:System.Data.DataRow>.  
  
     Este método no quita físicamente el registro. En su lugar, marca el registro para su eliminación.  
  
    > [!NOTE]
    > Si obtiene la propiedad count de un <xref:System.Data.DataRowCollection>, el recuento resultante incluye los registros que se han marcado para su eliminación. Para obtener un recuento exacto de registros que no están marcados para su eliminación, puede recorrer la colección observando la <xref:System.Data.DataRow.RowState%2A> propiedad de cada registro. (Los registros marcados para su eliminación tienen un <xref:System.Data.DataRow.RowState%2A> de <xref:System.Data.DataRowState>.) Como alternativa, puede crear una vista de datos de un conjunto de datos que se filtra según el estado de fila y obtener la propiedad de recuento a partir de ahí.  
  
     El ejemplo siguiente muestra cómo llamar a la <xref:System.Data.DataRow.Delete%2A> método para marcar la primera fila de la `Customers` como eliminado de la tabla:  
  
     [!code-csharp[VbRaddataEditing#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#8)]
     [!code-vb[VbRaddataEditing#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#8)]  
  
## <a name="determine-if-there-are-changed-rows"></a>Determinar si hay filas modificadas  
 Cuando se realizan cambios en los registros de un conjunto de datos, se almacena información sobre dichos cambios hasta que los confirme Confirmar los cambios cuando se llama a la `AcceptChanges` método de una conjunto de datos o tabla de datos, o cuando se llama a la `Update` método de un TableAdapter o adaptador de datos.  
  
 Los cambios son dos formas sometidas a seguimiento en cada fila de datos:  
  
- Cada fila de datos contiene información relacionada con su <xref:System.Data.DataRow.RowState%2A> (por ejemplo, <xref:System.Data.DataRowState>, <xref:System.Data.DataRowState>, <xref:System.Data.DataRowState>, o <xref:System.Data.DataRowState>).  
  
- Cada fila de datos modificada contiene varias versiones de fila (<xref:System.Data.DataRowVersion>), la versión original (antes de que cambie) y la versión actual (después de los cambios). Durante el período de un cambio está pendiente (el tiempo cuando responda a la <xref:System.Data.DataTable.RowChanging> eventos), una tercera versión: la versión propuesta, también está disponible.
  
  El método <xref:System.Data.DataSet.HasChanges%2A> de un conjunto de datos devuelve `true` si se han realizado modificaciones en el mismo. Después de determinar que las filas modificadas existen, puede llamar al método `GetChanges` de un control <xref:System.Data.DataSet> o <xref:System.Data.DataTable> para devolver un conjunto de filas cambiadas. Para obtener más información, vea [Cómo: Recuperar filas modificadas](http://msdn.microsoft.com/library/6ff0cbd0-5253-48e7-888a-144d56c2e0a9).  
  
#### <a name="to-determine-if-changes-have-been-made-to-any-rows"></a>Para determinar si se han realizado cambios en las filas  
  
- Llame al método <xref:System.Data.DataSet.HasChanges%2A> de un conjunto de datos para comprobar si hay filas modificadas.  
  
     En el ejemplo siguiente, se muestra cómo comprobar el valor devuelto del método <xref:System.Data.DataSet.HasChanges%2A> para detectar si hay filas modificadas en un conjunto de datos denominado `NorthwindDataset1`:  
  
     [!code-csharp[VbRaddataEditing#12](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#12)]
     [!code-vb[VbRaddataEditing#12](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#12)]  
  
## <a name="determine-the-type-of-changes"></a>Determinar el tipo de cambios  
 También puede comprobar ver qué tipo de cambios se realizaron en un conjunto de datos, pasando el valor de la <xref:System.Data.DataRowState> enumeración para el <xref:System.Data.DataSet.HasChanges%2A> método.  
  
#### <a name="to-determine-what-type-of-changes-have-been-made-to-a-row"></a>Para determinar el tipo de cambios realizados en una fila  
  
- Pase un valor <xref:System.Data.DataRowState> al método <xref:System.Data.DataSet.HasChanges%2A>.  
  
     El ejemplo siguiente muestra cómo comprobar un conjunto de datos denominado `NorthwindDataset1` para determinar si se agregaron las nuevas filas en ella:  
  
     [!code-csharp[VbRaddataEditing#13](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#13)]
     [!code-vb[VbRaddataEditing#13](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#13)]  
  
## <a name="to-locate-rows-that-have-errors"></a>Para buscar las filas con errores  
 Al trabajar con columnas individuales y las filas de datos, pueden producirse errores. Puede comprobar el `HasErrors` propiedad para determinar si hay errores en un <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, o <xref:System.Data.DataRow>.  
  
1. Compruebe el `HasErrors` propiedad para ver si hay errores en el conjunto de datos.  
  
2. Si el `HasErrors` propiedad es `true`, recorrer en iteración las colecciones de tablas y, a continuación, el a través de las filas, que se va a buscar la fila con el error.  
  
     [!code-csharp[VbRaddataEditing#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#23)]
     [!code-vb[VbRaddataEditing#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#23)]
