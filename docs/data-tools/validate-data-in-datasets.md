---
title: Validar datos en conjuntos de datos
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DataTable.ColumnChanging
- System.Data.DataTable.ColumnChanging
- System.Data.DataTable.RowChanging
- DataTable.RowChanging
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data validation, datasets
- data validation
- validating data, datasets
- updating datasets, validating data
ms.assetid: 79500596-1e4d-478e-a991-a636fd73a622
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: f370e55c600baa3f017f6bbb58feab38c23e51ab
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648111"
---
# <a name="validate-data-in-datasets"></a>Validar datos en conjuntos de datos
La validación de datos es el proceso de confirmar que los valores que se especifican en los objetos de datos cumplen las restricciones del esquema de un conjunto de datos. El proceso de validación también confirma que estos valores siguen las reglas establecidas para la aplicación. Se recomienda validar los datos antes de enviar las actualizaciones a la base de datos subyacente. Esto reduce los errores, así como el número potencial de recorridos de ida y vuelta entre una aplicación y la base de datos.

Puede confirmar que los datos que se escriben en un conjunto de datos son válidos compilando las comprobaciones de validación en el propio conjunto de datos. El conjunto de datos puede comprobar los datos independientemente de cómo se realice la actualización, ya sea directamente mediante los controles de un formulario, dentro de un componente, o de alguna otra manera. Dado que el conjunto de datos forma parte de la aplicación (a diferencia del back-end de base de datos), es un lugar lógico para compilar la validación específica de la aplicación.

El mejor lugar para agregar la validación a la aplicación es el archivo de clase parcial del conjunto de aplicaciones. En [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] o [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], abra el **Diseñador de DataSet** y haga doble clic en la columna o la tabla para la que desea crear la validación. Esta acción crea automáticamente un controlador de eventos <xref:System.Data.DataTable.ColumnChanging> o <xref:System.Data.DataTable.RowChanging>.

## <a name="validate-data"></a>Validar datos
La validación dentro de un conjunto de DataSet se realiza de las siguientes maneras:

- Mediante la creación de su propia validación específica de la aplicación que puede comprobar los valores de una columna de datos individual durante los cambios. Para obtener más información, vea [Cómo: validar datos durante los cambios de columna](validate-data-in-datasets.md).

- Mediante la creación de su propia validación específica de la aplicación que puede comprobar los datos de los valores mientras se modifica una fila de datos completa. Para obtener más información, vea [Cómo: validar datos durante los cambios de fila](validate-data-in-datasets.md).

- Mediante la creación de claves, restricciones UNIQUE, etc. como parte de la definición de esquema real del conjunto de datos.

- Mediante el establecimiento de las propiedades del <xref:System.Data.DataColumn> del objeto, como <xref:System.Data.DataColumn.MaxLength%2A>, <xref:System.Data.DataColumn.AllowDBNull%2A> y <xref:System.Data.DataColumn.Unique%2A>.

El objeto <xref:System.Data.DataTable> genera varios eventos cuando se produce un cambio en un registro:

- Los eventos <xref:System.Data.DataTable.ColumnChanging> y <xref:System.Data.DataTable.ColumnChanged> se generan durante y después de cada cambio en una columna individual. El evento <xref:System.Data.DataTable.ColumnChanging> resulta útil cuando se desea validar cambios en columnas específicas. La información sobre el cambio propuesto se pasa como argumento con el evento.
- Los eventos <xref:System.Data.DataTable.RowChanging> y <xref:System.Data.DataTable.RowChanged> se generan durante y después de cualquier cambio en una fila. El evento <xref:System.Data.DataTable.RowChanging> es más general. Indica que se está produciendo un cambio en algún lugar de la fila, pero no sabe qué columna ha cambiado.

De forma predeterminada, cada cambio en una columna genera cuatro eventos. La primera es la <xref:System.Data.DataTable.ColumnChanging> y <xref:System.Data.DataTable.ColumnChanged> eventos para la columna específica que se va a cambiar. A continuación se muestran los eventos <xref:System.Data.DataTable.RowChanging> y <xref:System.Data.DataTable.RowChanged>. Si se realizan varios cambios en la fila, los eventos se generarán para cada cambio.

> [!NOTE]
> El método <xref:System.Data.DataRow.BeginEdit%2A> de la fila de datos desactiva los eventos <xref:System.Data.DataTable.RowChanging> y <xref:System.Data.DataTable.RowChanged> después de cada cambio de columna individual. En ese caso, el evento no se genera hasta que se haya llamado al método <xref:System.Data.DataRow.EndEdit%2A>, cuando los eventos <xref:System.Data.DataTable.RowChanging> y <xref:System.Data.DataTable.RowChanged> se producen una sola vez. Para obtener más información, vea [desactivar restricciones al llenar un conjunto](../data-tools/turn-off-constraints-while-filling-a-dataset.md)de datos.

El evento que elija dependerá de la granularidad que desee para la validación. Si es importante que detecte un error inmediatamente cuando una columna cambie, compile la validación mediante el evento <xref:System.Data.DataTable.ColumnChanging>. De lo contrario, use el evento <xref:System.Data.DataTable.RowChanging>, que podría provocar la detección de varios errores a la vez. Además, si los datos están estructurados para que el valor de una columna se valide en función del contenido de otra columna, realice la validación durante el evento <xref:System.Data.DataTable.RowChanging>.

Cuando se actualizan los registros, el objeto <xref:System.Data.DataTable> desencadena eventos a los que se puede responder a medida que se producen cambios y después de que se realicen cambios.

Si la aplicación utiliza un conjunto de un DataSet con tipo, puede crear controladores de eventos fuertemente tipados. Esto agrega cuatro eventos con tipo adicionales para los que se pueden crear controladores: `dataTableNameRowChanging`, `dataTableNameRowChanged`, `dataTableNameRowDeleting` y `dataTableNameRowDeleted`. Estos controladores de eventos con tipo pasan un argumento que incluye los nombres de columna de la tabla que facilitan la escritura y la lectura del código.

## <a name="data-update-events"></a>Eventos de actualización de datos

|evento|Descripción|
|-----------|-----------------|
|<xref:System.Data.DataTable.ColumnChanging>|Se está cambiando el valor de una columna. El evento le pasa la fila y la columna, junto con el nuevo valor propuesto.|
|<xref:System.Data.DataTable.ColumnChanged>|Se ha cambiado el valor de una columna. El evento le pasa la fila y la columna, junto con el valor propuesto.|
|<xref:System.Data.DataTable.RowChanging>|Los cambios que se realizaron en un objeto de <xref:System.Data.DataRow> están a punto de confirmarse en el conjunto de datos. Si no se ha llamado al método <xref:System.Data.DataRow.BeginEdit%2A>, se genera el evento <xref:System.Data.DataTable.RowChanging> para cada cambio en una columna inmediatamente después de que se haya producido el evento <xref:System.Data.DataTable.ColumnChanging>. Si llamó a <xref:System.Data.DataRow.BeginEdit%2A> antes de realizar los cambios, el evento de <xref:System.Data.DataTable.RowChanging> se genera solo cuando se llama al método <xref:System.Data.DataRow.EndEdit%2A>.<br /><br /> El evento le pasa la fila, junto con un valor que indica qué tipo de acción (cambio, inserción, etc.) se está llevando a cabo.|
|<xref:System.Data.DataTable.RowChanged>|Se ha cambiado una fila. El evento le pasa la fila, junto con un valor que indica qué tipo de acción (cambio, inserción, etc.) se está llevando a cabo.|
|<xref:System.Data.DataTable.RowDeleting>|Se está eliminando una fila. El evento le pasa la fila, junto con un valor que indica qué tipo de acción (eliminar) se está llevando a cabo.|
|<xref:System.Data.DataTable.RowDeleted>|Se ha eliminado una fila. El evento le pasa la fila, junto con un valor que indica qué tipo de acción (eliminar) se está llevando a cabo.|

Los eventos <xref:System.Data.DataTable.ColumnChanging>, <xref:System.Data.DataTable.RowChanging> y <xref:System.Data.DataTable.RowDeleting> se generan durante el proceso de actualización. Puede utilizar estos eventos para validar datos o realizar otros tipos de procesamiento. Dado que la actualización está en curso durante estos eventos, puede cancelarla iniciando una excepción, lo que evita que finalice la actualización.

Los eventos <xref:System.Data.DataTable.ColumnChanged>, <xref:System.Data.DataTable.RowChanged> y <xref:System.Data.DataTable.RowDeleted> son eventos de notificación que se producen cuando la actualización ha finalizado correctamente. Estos eventos son útiles cuando se desea realizar otras acciones en función de una actualización correcta.

## <a name="validate-data-during-column-changes"></a>Validar datos durante los cambios de columna

> [!NOTE]
> El **Diseñador de DataSet** crea una clase parcial en la que se puede Agregar la lógica de validación a un conjunto de DataSet. El DataSet generado por el diseñador no elimina ni cambia ningún código de la clase parcial.

Puede validar los datos cuando el valor de una columna de datos cambia respondiendo al evento <xref:System.Data.DataTable.ColumnChanging>. Cuando se produce, este evento pasa un argumento de evento (<xref:System.Data.DataColumnChangeEventArgs.ProposedValue%2A>) que contiene el valor propuesto para la columna actual. En función del contenido de `e.ProposedValue`, puede:

- Aceptar el valor propuesto sin hacer nada.

- Rechace el valor propuesto estableciendo el error de columna (<xref:System.Data.DataRow.SetColumnError%2A>) desde dentro del controlador de eventos de cambio de columna.

- Utilizar opcionalmente un control <xref:System.Windows.Forms.ErrorProvider> para mostrar un mensaje de error al usuario. Para obtener más información, vea [ErrorProvider (Componente)](/dotnet/framework/winforms/controls/errorprovider-component-windows-forms).

La validación también puede realizarse durante el evento <xref:System.Data.DataTable.RowChanging>.

## <a name="validate-data-during-row-changes"></a>Validar datos durante los cambios de fila
Puede escribir código para comprobar que cada columna que desee validar contiene datos que cumplen los requisitos de la aplicación. Para ello, establezca la columna para indicar que contiene un error si un valor propuesto no es aceptable. Los ejemplos siguientes establecen un error de la columna cuando la columna `Quantity` es igual o menor que 0. Los controladores de eventos que modifican la fila se parecerán a los ejemplos siguientes.

### <a name="to-validate-data-when-a-row-changes-visual-basic"></a>Para validar los datos cuando se modifica una fila (Visual Basic)

1. Abra su conjunto de datos en el **Diseñador de Dataset**. Para obtener más información, vea [Tutorial: crear un conjunto de datos en el diseñador de DataSet](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Haga doble clic en la barra de título de la tabla que desee validar. Esta acción crea automáticamente el controlador de eventos <xref:System.Data.DataTable.RowChanging> del control <xref:System.Data.DataTable> en el archivo de clase parcial del conjunto de datos.

    > [!TIP]
    > Haga doble clic a la izquierda del nombre de la tabla para crear el controlador de eventos que modifique la fila. Si hace doble clic en el nombre de la tabla, puede editarlo.

     [!code-vb[VbRaddataValidating#3](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_1.vb)]

### <a name="to-validate-data-when-a-row-changes-c"></a>Para validar los datos cuando se modifica una fila (C#)

1. Abra su conjunto de datos en el **Diseñador de Dataset**. Para obtener más información, vea [Tutorial: crear un conjunto de datos en el diseñador de DataSet](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Haga doble clic en la barra de título de la tabla que desee validar. Esta acción crea un archivo de clase parcial para el control <xref:System.Data.DataTable>.

    > [!NOTE]
    > El **Diseñador de DataSet** no crea automáticamente un controlador de eventos para el evento <xref:System.Data.DataTable.RowChanging>. Tiene que crear un método para controlar el evento de <xref:System.Data.DataTable.RowChanging> y ejecutar el código para enlazar el evento en el método de inicialización de la tabla.

3. Copie el código siguiente en la clase parcial:

    ```csharp
    public override void EndInit()
    {
        base.EndInit();
        Order_DetailsRowChanging += TestRowChangeEvent;
    }

    public void TestRowChangeEvent(object sender, Order_DetailsRowChangeEvent e)
    {
        if ((short)e.Row.Quantity <= 0)
        {
            e.Row.SetColumnError("Quantity", "Quantity must be greater than 0");
        }
        else
        {
            e.Row.SetColumnError("Quantity", "");
        }
    }
    ```

## <a name="to-retrieve-changed-rows"></a>Para recuperar las filas modificadas
Cada fila de una tabla de datos tiene una propiedad <xref:System.Data.DataRow.RowState%2A> que realiza un seguimiento del estado actual de esa fila usando los valores de la enumeración <xref:System.Data.DataRowState>. Puede devolver filas modificadas de un conjunto de datos o una tabla de datos llamando al método `GetChanges` de un <xref:System.Data.DataSet> o <xref:System.Data.DataTable>. Puede comprobar que existen cambios antes de llamar a `GetChanges` llamando al método <xref:System.Data.DataSet.HasChanges%2A> de un conjunto de DataSet.

> [!NOTE]
> Después de confirmar los cambios en un conjunto de datos o en una tabla de datos (llamando al método <xref:System.Data.DataSet.AcceptChanges%2A>), el método `GetChanges` no devuelve ningún dato. Si la aplicación necesita procesar filas cambiadas, debe procesar los cambios antes de llamar al método `AcceptChanges`.

Al llamar al método <xref:System.Data.DataSet.GetChanges%2A> de un conjunto de datos o una tabla de datos, se devuelve un nuevo conjunto de datos o una tabla de datos que solo contiene los registros que han cambiado. Si desea obtener registros específicos, por ejemplo, solo registros nuevos o solo registros modificados, puede pasar un valor de la enumeración <xref:System.Data.DataRowState> como un parámetro al método `GetChanges`.

Utilice la enumeración <xref:System.Data.DataRowVersion> para tener acceso a las distintas versiones de una fila (por ejemplo, los valores originales que estaban en una fila antes de procesarla).

### <a name="to-get-all-changed-records-from-a-dataset"></a>Para obtener todos los registros modificados de un conjunto de cambios

- Llame al método <xref:System.Data.DataSet.GetChanges%2A> de un conjunto de DataSet.

     En el ejemplo siguiente se crea un nuevo conjunto de documentos denominado `changedRecords` y se rellena con todos los registros modificados de otro conjunto de archivos denominado `dataSet1`.

     [!code-csharp[VbRaddataEditing#14](../data-tools/codesnippet/CSharp/validate-data-in-datasets_2.cs)]
     [!code-vb[VbRaddataEditing#14](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_2.vb)]

### <a name="to-get-all-changed-records-from-a-data-table"></a>Para obtener todos los registros cambiados de una tabla de datos

- Llame al método <xref:System.Data.DataTable.GetChanges%2A> de una DataTable.

     En el ejemplo siguiente se crea una nueva tabla de datos denominada `changedRecordsTable` y se rellena con todos los registros modificados de otra tabla de datos denominada `dataTable1`.

     [!code-csharp[VbRaddataEditing#15](../data-tools/codesnippet/CSharp/validate-data-in-datasets_3.cs)]
     [!code-vb[VbRaddataEditing#15](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_3.vb)]

### <a name="to-get-all-records-that-have-a-specific-row-state"></a>Para obtener todos los registros que tienen un estado de fila específico

- Llame al método `GetChanges` de un conjunto de datos o una tabla de datos y pase un valor de enumeración <xref:System.Data.DataRowState> como un argumento.

     En el ejemplo siguiente se muestra cómo crear un nuevo conjunto de documentos denominado `addedRecords` y rellenarlo solo con los registros que se han agregado al conjunto de `dataSet1`.

     [!code-csharp[VbRaddataEditing#16](../data-tools/codesnippet/CSharp/validate-data-in-datasets_4.cs)]
     [!code-vb[VbRaddataEditing#16](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_4.vb)]

     En el ejemplo siguiente se muestra cómo devolver todos los registros que se agregaron recientemente a la tabla `Customers`:

     [!code-csharp[VbRaddataEditing#17](../data-tools/codesnippet/CSharp/validate-data-in-datasets_5.cs)]
     [!code-vb[VbRaddataEditing#17](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_5.vb)]

## <a name="access-the-original-version-of-a-datarow"></a>Obtener acceso a la versión original de una DataRow
Cuando los cambios se realizan en las filas de datos, el conjunto de datos retiene tanto la versión original (<xref:System.Data.DataRowVersion.Original>) como las versiones nuevas (<xref:System.Data.DataRowVersion.Current>) de la fila. Por ejemplo, antes de llamar al método `AcceptChanges`, su aplicación puede tener acceso a las distintas versiones de un registro (según se defina en la enumeración <xref:System.Data.DataRowVersion>) y procesar los cambios según corresponda.

> [!NOTE]
> Las versiones diferentes de una fila solo existen después de haberla editado y antes de que se haya llamado al método `AcceptChanges`. Una vez que se ha llamado al método `AcceptChanges`, las versiones actual y original son iguales.

Si se pasa el valor <xref:System.Data.DataRowVersion> junto con el índice de la columna (o el nombre de la columna como cadena), se devuelve el valor de la versión de fila concreta de esa columna. La columna cambiada se identifica durante los eventos <xref:System.Data.DataTable.ColumnChanging> y <xref:System.Data.DataTable.ColumnChanged>. Es un buen momento para inspeccionar las diferentes versiones de fila con fines de validación. Sin embargo, si ha suspendido temporalmente las restricciones, dichos eventos no se generarán y tendrá que identificar mediante programación Qué columnas han cambiado. Para ello, recorra en iteración la colección <xref:System.Data.DataTable.Columns%2A> y compare los distintos valores de <xref:System.Data.DataRowVersion>.

### <a name="to-get-the-original-version-of-a-record"></a>Para obtener la versión original de un registro

- Obtenga acceso al valor de una columna pasando el <xref:System.Data.DataRowVersion> de la fila que desea devolver.

     En el ejemplo siguiente se muestra cómo usar un valor <xref:System.Data.DataRowVersion> para obtener el valor original de un campo `CompanyName` en un <xref:System.Data.DataRow>:

     [!code-csharp[VbRaddataEditing#21](../data-tools/codesnippet/CSharp/validate-data-in-datasets_6.cs)]
     [!code-vb[VbRaddataEditing#21](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_6.vb)]

## <a name="access-the-current-version-of-a-datarow"></a>Obtener acceso a la versión actual de una DataRow

### <a name="to-get-the-current-version-of-a-record"></a>Para obtener la versión actual de un registro

- Obtenga acceso al valor de una columna y, a continuación, agregue un parámetro al índice que indica qué versión de una fila desea devolver.

     En el ejemplo siguiente se muestra cómo usar un valor <xref:System.Data.DataRowVersion> para obtener el valor actual de un campo `CompanyName` en un <xref:System.Data.DataRow>:

     [!code-csharp[VbRaddataEditing#22](../data-tools/codesnippet/CSharp/validate-data-in-datasets_7.cs)]
     [!code-vb[VbRaddataEditing#22](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_7.vb)]

## <a name="see-also"></a>Vea también

- [Herramientas de conjunto de datos en Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Procedimiento para validar datos en el control DataGridView de Windows Forms](/dotnet/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control)
- [Procedimiento para mostrar iconos de error para la validación de formularios con el componente ErrorProvider de Windows Forms](/dotnet/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider)