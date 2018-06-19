---
title: Validar los datos en conjuntos de datos
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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c8986ce9e2ee1ff171a524b0a402a1e44b70ca06
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31927473"
---
# <a name="validate-data-in-datasets"></a>Validar los datos en conjuntos de datos
Validación de datos es el proceso de confirmar que los valores que se especifican en los objetos de datos se ajustan a las restricciones de esquema de un conjunto de datos. El proceso de validación también confirma que estos valores son siguiendo las reglas establecidas para la aplicación. Es una buena práctica para validar los datos antes de enviar actualizaciones a la base de datos subyacente. Esto reduce los errores, así como el número de viajes de ida y vuelta entre una aplicación y la base de datos.

Puede confirmar que los datos que se está escribiendo en un conjunto de datos están válidos mediante la creación de comprobaciones de validación en el conjunto de datos. El conjunto de datos puede comprobar los datos independientemente de cómo se realiza la actualización, ya sea directamente mediante los controles en un formulario, dentro de un componente o de alguna otra manera. Dado que el conjunto de datos es parte de la aplicación (a diferencia de la base de datos de back-end), es un lugar lógico para compilar la validación específica de la aplicación.

Es el mejor lugar para agregar validación a la aplicación en el archivo de clase parcial del conjunto de datos. En [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] o [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], abra el **Diseñador de Dataset** y haga doble clic en la columna o tabla para la que desea crear la validación. Esta acción crea automáticamente un <xref:System.Data.DataTable.ColumnChanging> o <xref:System.Data.DataTable.RowChanging> controlador de eventos.

## <a name="validate-data"></a>Validar datos
 Validación dentro de un conjunto de datos se puede lograr de las maneras siguientes:

-   Mediante la creación de su propia validación específica de la aplicación que puede comprobar los valores de una columna de datos individuales durante los cambios.  Para obtener más información, consulte [Cómo: validar datos durante la columna cambios](validate-data-in-datasets.md).

-   Mediante la creación de su propia validación específica de la aplicación que pueda comprobar los datos a los valores mientras un completo de datos está cambiando la fila. Para obtener más información, consulte [Cómo: validar datos durante la fila cambios](validate-data-in-datasets.md).

-   Mediante la creación de claves, restricciones unique, y así sucesivamente como parte de la definición de esquema real del conjunto de datos.

-   Al establecer las propiedades de la <xref:System.Data.DataColumn> objeto, como <xref:System.Data.DataColumn.MaxLength%2A>, <xref:System.Data.DataColumn.AllowDBNull%2A>, y <xref:System.Data.DataColumn.Unique%2A>.

Varios eventos generados por la <xref:System.Data.DataTable> cuando se está produciendo un cambio en un registro de objeto:

-   El <xref:System.Data.DataTable.ColumnChanging> y <xref:System.Data.DataTable.ColumnChanged> se generan eventos durante y después de cada cambio realizado en una columna individual. El <xref:System.Data.DataTable.ColumnChanging> evento es útil cuando desea validar cambios en columnas específicas. Información sobre el cambio propuesto se pasa como un argumento con el evento.
-   El <xref:System.Data.DataTable.RowChanging> y <xref:System.Data.DataTable.RowChanged> se generan eventos durante y después de un cambio en una fila. El <xref:System.Data.DataTable.RowChanging> evento es más general. Indica que se está produciendo un cambio en alguna parte de la fila, pero no se sabe qué columna ha cambiado.

De forma predeterminada, cada cambio realizado en una columna, por tanto, genera cuatro eventos. La primera es la <xref:System.Data.DataTable.ColumnChanging> y <xref:System.Data.DataTable.ColumnChanged> eventos para la columna específica que se va a cambiar. A continuación, están los <xref:System.Data.DataTable.RowChanging> y <xref:System.Data.DataTable.RowChanged> eventos. Si se se realizan varios cambios en la fila, los eventos se generan para cada cambio.

> [!NOTE]
>  La fila de datos <xref:System.Data.DataRow.BeginEdit%2A> método desactiva el <xref:System.Data.DataTable.RowChanging> y <xref:System.Data.DataTable.RowChanged> eventos después de cada cambio de columna individual. En ese caso, el evento no se produce hasta que el <xref:System.Data.DataRow.EndEdit%2A> se ha llamado un método, cuando el <xref:System.Data.DataTable.RowChanging> y <xref:System.Data.DataTable.RowChanged> se generan eventos una sola vez. Para obtener más información, consulte [desactivar restricciones al llenar un conjunto de datos](../data-tools/turn-off-constraints-while-filling-a-dataset.md).

El evento que elija depende en el nivel de granularidad desea que la validación sea. Si es importante detectar un error inmediatamente cuando se cambia una columna, construya la validación mediante el uso de la <xref:System.Data.DataTable.ColumnChanging> eventos. De lo contrario, utilice la <xref:System.Data.DataTable.RowChanging> eventos, lo que podrían ocasionar detectar varios errores al mismo tiempo. Además, si los datos están estructurados para que el valor de una columna se valida basándose en el contenido de otra columna, a continuación, realizar la validación durante la <xref:System.Data.DataTable.RowChanging> eventos.

Cuando se actualizan registros, la <xref:System.Data.DataTable> objeto provoca eventos que se pueden responder a medida que se realizan cambios y después de realizar cambios.

Si la aplicación utiliza un conjunto de datos con tipo, puede crear controladores de eventos fuertemente tipados. Esto agregará cuatro eventos con tipo adicionales que puede crear controladores para: `dataTableNameRowChanging`, `dataTableNameRowChanged`, `dataTableNameRowDeleting`, y `dataTableNameRowDeleted`. Estos controladores de eventos con tipo pasan un argumento que incluye los nombres de columna de la tabla que facilitan la lectura y escritura de código.

## <a name="data-update-events"></a>Eventos de actualización de datos

|evento|Descripción|
|-----------|-----------------|
|<xref:System.Data.DataTable.ColumnChanging>|Se está cambiando el valor de una columna. El evento pasa la fila y columna, junto con el nuevo valor propuesto.|
|<xref:System.Data.DataTable.ColumnChanged>|Se cambió el valor de una columna. El evento pasa la fila y columna, junto con el valor propuesto.|
|<xref:System.Data.DataTable.RowChanging>|Los cambios realizados en un <xref:System.Data.DataRow> objeto están a punto de confirmarse en el conjunto de datos. Si no ha llamado el <xref:System.Data.DataRow.BeginEdit%2A> método, el <xref:System.Data.DataTable.RowChanging> evento se desencadena para cada cambio realizado en una columna inmediatamente después de la <xref:System.Data.DataTable.ColumnChanging> se ha producido el evento. Si llama a <xref:System.Data.DataRow.BeginEdit%2A> antes de realizar cambios, el <xref:System.Data.DataTable.RowChanging> evento sólo se desencadena cuando se llama a la <xref:System.Data.DataRow.EndEdit%2A> método.<br /><br /> El evento pasa la fila, junto con un valor que indica qué tipo de acción (cambio, inserción etc.) se está realizando.|
|<xref:System.Data.DataTable.RowChanged>|Una fila ha cambiado. El evento pasa la fila, junto con un valor que indica qué tipo de acción (cambio, inserción etc.) se está realizando.|
|<xref:System.Data.DataTable.RowDeleting>|Se está eliminando una fila. El evento pasa la fila, junto con un valor que indica qué tipo de acción (delete) se está realizando.|
|<xref:System.Data.DataTable.RowDeleted>|Se ha eliminado una fila. El evento pasa la fila, junto con un valor que indica qué tipo de acción (delete) se está realizando.|

El <xref:System.Data.DataTable.ColumnChanging>, <xref:System.Data.DataTable.RowChanging>, y <xref:System.Data.DataTable.RowDeleting> eventos se generan durante el proceso de actualización. Puede usar estos eventos para validar datos o realizar otros tipos de procesamiento. Dado que la actualización está en curso durante estos eventos, puede cancelar iniciando una excepción, lo que impide que la actualización de acabado.

El <xref:System.Data.DataTable.ColumnChanged>, <xref:System.Data.DataTable.RowChanged> y <xref:System.Data.DataTable.RowDeleted> son eventos de notificación que se producen cuando la actualización ha finalizado correctamente. Estos eventos son útiles cuando desea realizar una acción en función de una actualización correcta.

## <a name="validate-data-during-column-changes"></a>Validar datos durante los cambios de columna

> [!NOTE]
>  El **Diseñador de Dataset** crea una clase parcial en qué validación lógica se puede agregar a un conjunto de datos. El conjunto de datos generado por el diseñador no eliminar o modificar cualquier código en la clase parcial.

Puede validar los datos cuando cambia el valor de una columna de datos al responder a las <xref:System.Data.DataTable.ColumnChanging> eventos. Cuando se provoca, este evento pasa un argumento de evento (<xref:System.Data.DataColumnChangeEventArgs.ProposedValue%2A>) que contiene el valor propuesto para la columna actual. En función del contenido de `e.ProposedValue`, puede:

-   Aceptar el valor propuesto sin hacer nada.

-   Rechazar el valor propuesto estableciendo el error de la columna (<xref:System.Data.DataRow.SetColumnError%2A>) desde dentro del controlador de eventos de cambio de columna.

-   Utilizar opcionalmente un control <xref:System.Windows.Forms.ErrorProvider> para mostrar un mensaje de error al usuario. Para obtener más información, consulte [ErrorProvider (componente)](/dotnet/framework/winforms/controls/errorprovider-component-windows-forms).

También se puede realizar la validación durante la <xref:System.Data.DataTable.RowChanging> eventos.

## <a name="validate-data-during-row-changes"></a>Validar datos durante los cambios de fila
Puede escribir código para comprobar que cada columna que desee validar contiene datos que cumplen los requisitos de la aplicación. Para ello, establezca la columna para indicar que contiene un error si un valor propuesto no es aceptable. Los ejemplos siguientes establecen un error de la columna cuando la columna `Quantity` es igual o menor que 0. Los controladores de eventos que modifican la fila se parecerán a los ejemplos siguientes.

#### <a name="to-validate-data-when-a-row-changes-visual-basic"></a>Para validar los datos cuando se modifica una fila (Visual Basic)

1.  Abra su conjunto de datos en el **Diseñador de Dataset**. Para obtener más información, consulte [Tutorial: crear un conjunto de datos en el Diseñador de Dataset](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2.  Haga doble clic en la barra de título de la tabla que desee validar. Esta acción crea automáticamente el controlador de eventos <xref:System.Data.DataTable.RowChanging> del control <xref:System.Data.DataTable> en el archivo de clase parcial del conjunto de datos.

    > [!TIP]
    >  Haga doble clic a la izquierda del nombre de la tabla para crear el controlador de eventos que modifique la fila. Si hace doble clic en el nombre de tabla, se puede editar.

     [!code-vb[VbRaddataValidating#3](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_1.vb)]

#### <a name="to-validate-data-when-a-row-changes-c"></a>Para validar los datos cuando se modifica una fila (C#)

1.  Abra su conjunto de datos en el **Diseñador de Dataset**. Para obtener más información, consulte [Tutorial: crear un conjunto de datos en el Diseñador de dataset](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2.  Haga doble clic en la barra de título de la tabla que desee validar. Esta acción crea un archivo de clase parcial para el control <xref:System.Data.DataTable>.

    > [!NOTE]
    >  El **Diseñador de Dataset** no crea automáticamente un controlador de eventos para el <xref:System.Data.DataTable.RowChanging> eventos. Debe crear un método para controlar la <xref:System.Data.DataTable.RowChanging> eventos y ejecutar código para enlazar el evento en el método de inicialización de la tabla.

3.  Copie el código siguiente en la clase parcial:

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

## <a name="to-retrieve-changed-rows"></a>Para recuperar filas modificadas
Cada fila de una tabla de datos tiene un <xref:System.Data.DataRow.RowState%2A> propiedad que realiza un seguimiento del estado actual de esa fila mediante los valores en el <xref:System.Data.DataRowState> enumeración. Puede devolver filas modificadas desde una conjunto de datos o tabla de datos mediante una llamada a la `GetChanges` método de un <xref:System.Data.DataSet> o <xref:System.Data.DataTable>. Puede comprobar la existen de cambios antes de llamar a `GetChanges` mediante una llamada a la <xref:System.Data.DataSet.HasChanges%2A> método de un conjunto de datos.

> [!NOTE]
>  Después de confirmar los cambios a una conjunto de datos o tabla de datos (mediante una llamada a la <xref:System.Data.DataSet.AcceptChanges%2A> método), el `GetChanges` método no devuelve ningún dato. Si la aplicación necesita procesar las filas modificadas, debe procesar los cambios antes de llamar a la `AcceptChanges` método.

Llamar a la <xref:System.Data.DataSet.GetChanges%2A> método de una conjunto de datos o tabla de datos devuelve una nuevo conjunto de datos o tabla de datos que contiene solamente los registros que se han cambiado. Si desea obtener registros específicos: por ejemplo, sólo nuevos registros o sólo los registros modificados, puede pasar un valor de la <xref:System.Data.DataRowState> enumeración como un parámetro a la `GetChanges` método.

Use la <xref:System.Data.DataRowVersion> enumeración para tener acceso a las distintas versiones de una fila (por ejemplo, los valores originales que se encontraban en una fila antes de procesarla).

#### <a name="to-get-all-changed-records-from-a-dataset"></a>Para obtener todos los cambios en los registros de un conjunto de datos

-   Llame a la <xref:System.Data.DataSet.GetChanges%2A> método de un conjunto de datos.

     En el ejemplo siguiente se crea un nuevo conjunto de datos denominado `changedRecords` y lo rellena con todos los registros modificados de otro conjunto de datos denominado `dataSet1`.

     [!code-csharp[VbRaddataEditing#14](../data-tools/codesnippet/CSharp/validate-data-in-datasets_2.cs)]
     [!code-vb[VbRaddataEditing#14](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_2.vb)]

#### <a name="to-get-all-changed-records-from-a-data-table"></a>Para obtener todos los cambios en los registros de una tabla de datos

-   Llame a la <xref:System.Data.DataTable.GetChanges%2A> método de un objeto DataTable.

     En el ejemplo siguiente se crea una nueva tabla de datos denominada `changedRecordsTable` y lo rellena con todos los registros modificados de otra tabla de datos denominada `dataTable1`.

     [!code-csharp[VbRaddataEditing#15](../data-tools/codesnippet/CSharp/validate-data-in-datasets_3.cs)]
     [!code-vb[VbRaddataEditing#15](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_3.vb)]

#### <a name="to-get-all-records-that-have-a-specific-row-state"></a>Para obtener todos los registros que tienen un estado de fila específica

-   Llame a la `GetChanges` método de un conjunto de datos o tabla de datos y pase un <xref:System.Data.DataRowState> valor de enumeración como argumento.

     En el ejemplo siguiente se muestra cómo crear un nuevo conjunto de datos denominado `addedRecords` y rellenarla solo con los registros que se han agregado a la `dataSet1` conjunto de datos.

     [!code-csharp[VbRaddataEditing#16](../data-tools/codesnippet/CSharp/validate-data-in-datasets_4.cs)]
     [!code-vb[VbRaddataEditing#16](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_4.vb)]

     En el ejemplo siguiente se muestra cómo devolver todos los registros que se agregaron recientemente a la `Customers` tabla:

     [!code-csharp[VbRaddataEditing#17](../data-tools/codesnippet/CSharp/validate-data-in-datasets_5.cs)]
     [!code-vb[VbRaddataEditing#17](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_5.vb)]

## <a name="access-the-original-version-of-a-datarow"></a>Obtener acceso a la versión original de un objeto DataRow
Cuando los cambios se realizan en las filas de datos, el conjunto de datos retiene tanto la versión original (<xref:System.Data.DataRowVersion.Original>) como las versiones nuevas (<xref:System.Data.DataRowVersion.Current>) de la fila. Por ejemplo, antes de llamar al método `AcceptChanges`, su aplicación puede tener acceso a las distintas versiones de un registro (según se defina en la enumeración <xref:System.Data.DataRowVersion>) y procesar los cambios según corresponda.

> [!NOTE]
>  Versiones diferentes de una fila existen sólo después de que ésta haya sido revisada y antes de que el `AcceptChanges` ha llamado al método. Una vez que se ha llamado al método `AcceptChanges`, las versiones actual y original son iguales.

Si se pasa el valor <xref:System.Data.DataRowVersion> junto con el índice de la columna (o el nombre de la columna como cadena), se devuelve el valor de la versión de fila concreta de esa columna. La columna modificada se identifica durante la <xref:System.Data.DataTable.ColumnChanging> y <xref:System.Data.DataTable.ColumnChanged> eventos. Se trata de un buen momento para examinar las versiones de fila diferente para la validación. Sin embargo, si ha suspendido las restricciones temporalmente, esos eventos no se producen y deberá mediante programación identificar qué columnas han cambiado. Para ello, recorra en iteración la colección <xref:System.Data.DataTable.Columns%2A> y compare los distintos valores de <xref:System.Data.DataRowVersion>.

#### <a name="to-get-the-original-version-of-a-record"></a>Para obtener la versión original de un registro

-   Obtener acceso al valor de una columna pasando el <xref:System.Data.DataRowVersion> de la fila que desea devolver.

     En el ejemplo siguiente se muestra cómo utilizar un <xref:System.Data.DataRowVersion> para obtener el valor original de un `CompanyName` campo en un <xref:System.Data.DataRow>:

     [!code-csharp[VbRaddataEditing#21](../data-tools/codesnippet/CSharp/validate-data-in-datasets_6.cs)]
     [!code-vb[VbRaddataEditing#21](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_6.vb)]

## <a name="access-the-current-version-of-a-datarow"></a>Obtener acceso a la versión actual de un objeto DataRow

#### <a name="to-get-the-current-version-of-a-record"></a>Para obtener la versión actual de un registro

-   Obtener acceso al valor de una columna y, a continuación, agregue un parámetro al índice que indica qué versión de una fila que desea devolver.

     En el ejemplo siguiente se muestra cómo utilizar un <xref:System.Data.DataRowVersion> para obtener el valor actual de un `CompanyName` campo en un <xref:System.Data.DataRow>:

     [!code-csharp[VbRaddataEditing#22](../data-tools/codesnippet/CSharp/validate-data-in-datasets_7.cs)]
     [!code-vb[VbRaddataEditing#22](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_7.vb)]

## <a name="see-also"></a>Vea también

- [Herramientas de conjunto de datos en Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Validar datos en el control DataGridView de formularios Windows Forms](/dotnet/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control)
- [Mostrar iconos de error para la validación de formularios con el componente ErrorProvider de formularios Windows Forms](/dotnet/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider)