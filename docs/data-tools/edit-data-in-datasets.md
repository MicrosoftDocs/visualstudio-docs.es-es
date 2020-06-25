---
title: Editar datos en conjuntos de datos
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- datasets [Visual Basic], editing data
- data [Visual Studio], editing in datasets
ms.assetid: 50d5c580-fbf7-408f-be70-e63ac4f4d0eb
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: fe59b30e9af7ee1d98c0aba65339af1d53cba8fb
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/23/2020
ms.locfileid: "85282467"
---
# <a name="edit-data-in-datasets"></a>Editar datos en conjuntos de datos
Los datos de las tablas de datos se modifican de forma muy similar a como se modifican los datos de una tabla en cualquier base de datos. El proceso puede incluir la inserción, actualización y eliminación de registros en la tabla. En un formulario enlazado a datos, puede especificar qué campos son editables por el usuario. En esos casos, la infraestructura de enlace de datos controla todo el seguimiento de cambios para que los cambios se puedan devolver a la base de datos más adelante. Si realiza modificaciones en los datos mediante programación y pretende enviarlos de nuevo a la base de datos, debe utilizar los objetos y métodos que realizan el seguimiento de cambios.

Además de cambiar los datos reales, también puede consultar un <xref:System.Data.DataTable> para devolver filas específicas de datos. Por ejemplo, puede consultar filas individuales, versiones específicas de filas (original y propuesta), filas que han cambiado o filas con errores.

## <a name="to-edit-rows-in-a-dataset"></a>Para editar las filas de un conjunto de filas
Para editar una fila existente en una <xref:System.Data.DataTable> , debe buscar el <xref:System.Data.DataRow> que desea editar y, a continuación, asignar los valores actualizados a las columnas deseadas.

Si no conoce el índice de la fila que desea editar, use el `FindBy` método para buscar por la clave principal:

[!code-csharp[VbRaddataEditing#3](../data-tools/codesnippet/CSharp/edit-data-in-datasets_1.cs)]
[!code-vb[VbRaddataEditing#3](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_1.vb)]

Si conoce el índice de fila, puede tener acceso a las filas y modificarlas de la manera siguiente:

[!code-csharp[VbRaddataEditing#5](../data-tools/codesnippet/CSharp/edit-data-in-datasets_2.cs)]
[!code-vb[VbRaddataEditing#5](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_2.vb)]

## <a name="to-insert-new-rows-into-a-dataset"></a>Para insertar nuevas filas en un conjunto de filas
Las aplicaciones que usan controles enlazados a datos normalmente agregan nuevos registros a través del botón **Agregar nuevo** en un [control BindingNavigator](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms).

Para agregar manualmente nuevos registros a un conjunto de datos, cree una nueva fila de datos llamando al método en DataTable. A continuación, agregue la fila a la <xref:System.Data.DataRow> colección ( <xref:System.Data.DataTable.Rows%2A> ) de <xref:System.Data.DataTable> :

[!code-csharp[VbRaddataEditing#1](../data-tools/codesnippet/CSharp/edit-data-in-datasets_3.cs)]
[!code-vb[VbRaddataEditing#1](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_3.vb)]

Para conservar la información que el conjunto de datos necesita para enviar actualizaciones al origen de datos, utilice el <xref:System.Data.DataRow.Delete%2A> método para quitar las filas de una tabla de datos. Por ejemplo, si la aplicación utiliza un TableAdapter (o <xref:System.Data.Common.DataAdapter> ), el método del TableAdapter `Update` elimina las filas de la base de datos que tienen un <xref:System.Data.DataRow.RowState%2A> de <xref:System.Data.DataRowState.Deleted> .

Si la aplicación no necesita volver a enviar las actualizaciones a un origen de datos, es posible quitar los registros accediendo directamente a la colección de filas de datos ( <xref:System.Data.DataRowCollection.Remove%2A> ).

#### <a name="to-delete-records-from-a-data-table"></a>Para eliminar registros de una tabla de datos

- Llame al <xref:System.Data.DataRow.Delete%2A> método de <xref:System.Data.DataRow> .

     Este método no quita físicamente el registro. En su lugar, marca el registro para su eliminación.

    > [!NOTE]
    > Si obtiene la propiedad Count de un <xref:System.Data.DataRowCollection> , el recuento resultante incluye los registros que se han marcado para su eliminación. Para obtener un recuento exacto de registros que no están marcados para su eliminación, puede recorrer en iteración la colección en la que se examina la <xref:System.Data.DataRow.RowState%2A> propiedad de cada registro. (Los registros marcados para su eliminación tienen un <xref:System.Data.DataRow.RowState%2A> de <xref:System.Data.DataRowState.Deleted> ). Como alternativa, puede crear una vista de datos de un conjunto de datos que filtre según el estado de fila y obtener la propiedad Count de allí.

En el ejemplo siguiente se muestra cómo llamar al <xref:System.Data.DataRow.Delete%2A> método para marcar la primera fila de la `Customers` tabla como eliminada:

[!code-csharp[VbRaddataEditing#8](../data-tools/codesnippet/CSharp/edit-data-in-datasets_4.cs)]
[!code-vb[VbRaddataEditing#8](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_4.vb)]

## <a name="determine-if-there-are-changed-rows"></a>Determinar si hay filas modificadas
Cuando se realizan cambios en los registros de un conjunto de datos, se almacena información sobre dichos cambios hasta que los confirme Los cambios se confirman cuando se llama al `AcceptChanges` método de un conjunto de datos o una tabla de datos, o cuando se llama al `Update` método de un TableAdapter o adaptador de datos.

Se realiza un seguimiento de los cambios de dos maneras en cada fila de datos:

- Cada fila de datos contiene información relacionada con su <xref:System.Data.DataRow.RowState%2A> (por ejemplo,,, <xref:System.Data.DataRowState.Added> <xref:System.Data.DataRowState.Modified> <xref:System.Data.DataRowState.Deleted> o <xref:System.Data.DataRowState.Unchanged> ).

- Cada fila de datos cambiada contiene varias versiones de esa fila ( <xref:System.Data.DataRowVersion> ), la versión original (antes de los cambios) y la versión actual (después de los cambios). Durante el período en el que hay un cambio pendiente (el momento en que se puede responder al <xref:System.Data.DataTable.RowChanging> evento), también está disponible una tercera versión (la versión propuesta).

El método <xref:System.Data.DataSet.HasChanges%2A> de un conjunto de datos devuelve `true` si se han realizado modificaciones en el mismo. Después de determinar que las filas modificadas existen, puede llamar al método `GetChanges` de un control <xref:System.Data.DataSet> o <xref:System.Data.DataTable> para devolver un conjunto de filas cambiadas.

#### <a name="to-determine-if-changes-have-been-made-to-any-rows"></a>Para determinar si se han realizado cambios en las filas

- Llame al método <xref:System.Data.DataSet.HasChanges%2A> de un conjunto de datos para comprobar si hay filas modificadas.

En el ejemplo siguiente, se muestra cómo comprobar el valor devuelto del método <xref:System.Data.DataSet.HasChanges%2A> para detectar si hay filas modificadas en un conjunto de datos denominado `NorthwindDataset1`:

[!code-csharp[VbRaddataEditing#12](../data-tools/codesnippet/CSharp/edit-data-in-datasets_5.cs)]
[!code-vb[VbRaddataEditing#12](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_5.vb)]

## <a name="determine-the-type-of-changes"></a>Determinar el tipo de cambios
También puede comprobar qué tipo de cambios se realizaron en un conjunto de elementos pasando un valor de la <xref:System.Data.DataRowState> enumeración al <xref:System.Data.DataSet.HasChanges%2A> método.

#### <a name="to-determine-what-type-of-changes-have-been-made-to-a-row"></a>Para determinar el tipo de cambios realizados en una fila

- Pase un valor <xref:System.Data.DataRowState> al método <xref:System.Data.DataSet.HasChanges%2A>.

En el ejemplo siguiente se muestra cómo comprobar un conjunto de `NorthwindDataset1` filas denominado para determinar si se ha agregado alguna fila nueva:

[!code-csharp[VbRaddataEditing#13](../data-tools/codesnippet/CSharp/edit-data-in-datasets_6.cs)]
[!code-vb[VbRaddataEditing#13](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_6.vb)]

## <a name="to-locate-rows-that-have-errors"></a>Para buscar las filas que tienen errores
Al trabajar con columnas y filas de datos individuales, es posible que se produzcan errores. Puede comprobar la `HasErrors` propiedad para determinar si existen errores en <xref:System.Data.DataSet> , <xref:System.Data.DataTable> o <xref:System.Data.DataRow> .

1. Compruebe la `HasErrors` propiedad para ver si hay algún error en el conjunto de DataSet.

2. Si la `HasErrors` propiedad es `true` , recorra en iteración las colecciones de tablas y, a continuación, a través de las filas, para buscar la fila con el error.

[!code-csharp[VbRaddataEditing#23](../data-tools/codesnippet/CSharp/edit-data-in-datasets_7.cs)]
[!code-vb[VbRaddataEditing#23](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_7.vb)]

## <a name="see-also"></a>Vea también

- [Herramientas de conjunto de herramientas en Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
