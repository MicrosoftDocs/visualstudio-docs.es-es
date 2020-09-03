---
title: Validar datos en conjuntos de datos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- DataTable.ColumnChanging
- System.Data.DataTable.ColumnChanging
- System.Data.DataTable.RowChanging
- DataTable.RowChanging
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data validation, datasets
- data validation
- validating data, datasets
- updating datasets, validating data
ms.assetid: 79500596-1e4d-478e-a991-a636fd73a622
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8d42553fbee6de6a89e16716a191db8a3d9fb883
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72621067"
---
# <a name="validate-data-in-datasets"></a>Validar datos en conjuntos de datos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La validación de datos es el proceso de confirmar que los valores que se especifican en los objetos de datos cumplen las restricciones del esquema de un conjunto de datos. El proceso de validación también confirma que estos valores siguen las reglas establecidas para la aplicación. Se recomienda validar los datos antes de enviar las actualizaciones a la base de datos subyacente. Esto reduce los errores, así como el número potencial de recorridos de ida y vuelta entre una aplicación y la base de datos.

 Puede confirmar que los datos que se escriben en un conjunto de datos son válidos compilando las comprobaciones de validación en el propio conjunto de datos. El conjunto de datos puede comprobar los datos independientemente de cómo se realice la actualización, ya sea directamente mediante los controles de un formulario, dentro de un componente, o de alguna otra manera. Dado que el conjunto de datos forma parte de la aplicación (a diferencia del back-end de base de datos), es un lugar lógico para compilar la validación específica de la aplicación.

 El mejor lugar para agregar la validación a la aplicación es el archivo de clase parcial del conjunto de aplicaciones. En [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] o [!INCLUDE[csprcs](../includes/csprcs-md.md)] , abra el **Diseñador de DataSet** y haga doble clic en la columna o tabla para la que desea crear la validación. Esta acción crea automáticamente un <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> controlador de eventos o. Para obtener más información, vea [Cómo: validar datos durante los cambios de columna](https://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5) o [Cómo: validar datos durante los cambios de filas](https://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc). Para obtener un ejemplo completo, vea [Tutorial: agregar validación a un conjunto de DataSet](https://msdn.microsoft.com/library/09351fab-d670-45e3-b53a-a944eff717e7).

## <a name="validate-data"></a>Validación de datos
 La validación dentro de un conjunto de DataSet se puede realizar de las siguientes maneras:

- Mediante la creación de su propia validación específica de la aplicación que puede comprobar los valores de una columna de datos individual durante los cambios.  Para obtener más información, vea [Cómo: validar datos durante los cambios de columna](https://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5).

- Mediante la creación de su propia validación específica de la aplicación que puede comprobar los datos de los valores mientras se modifica una fila de datos completa. Para obtener más información, vea [Cómo: validar datos durante los cambios de fila](https://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc).

- Mediante la creación de claves, restricciones UNIQUE, etc. como parte de la definición de esquema real del conjunto de datos. Para obtener más información sobre cómo incorporar la validación en la definición de esquema, vea [restringir un DataColumn para que contenga valores únicos](https://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df).

- Estableciendo las propiedades de la propiedad <xref:System.Data.DataColumn> del objeto, como <xref:System.Data.DataColumn.MaxLength%2A> , <xref:System.Data.DataColumn.AllowDBNull%2A> y <xref:System.Data.DataColumn.Unique%2A> .

  El objeto genera varios eventos <xref:System.Data.DataTable> cuando se produce un cambio en un registro:

- Los <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.ColumnChanged> eventos y se generan durante y después de cada cambio en una columna individual. El <xref:System.Data.DataTable.ColumnChanging> evento es útil cuando se desea validar cambios en columnas específicas. La información sobre el cambio propuesto se pasa como argumento con el evento. Para obtener más información, vea [Cómo: validar datos durante los cambios de columna](https://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5).

- Los <xref:System.Data.DataTable.RowChanging> <xref:System.Data.DataTable.RowChanged> eventos y se generan durante y después de cualquier cambio en una fila. El <xref:System.Data.DataTable.RowChanging> evento es más general. Indica que se está produciendo un cambio en algún lugar de la fila, pero no sabe qué columna ha cambiado. Para obtener más información, vea [Cómo: validar datos durante los cambios de fila](https://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc).

  De forma predeterminada, cada cambio en una columna genera cuatro eventos. La primera es la <xref:System.Data.DataTable.ColumnChanging> y los <xref:System.Data.DataTable.ColumnChanged> eventos de la columna específica que se va a cambiar. A continuación se encuentran los <xref:System.Data.DataTable.RowChanging> <xref:System.Data.DataTable.RowChanged> eventos y. Si se realizan varios cambios en la fila, los eventos se generarán para cada cambio.

> [!NOTE]
> El método de la fila de datos <xref:System.Data.DataRow.BeginEdit%2A> desactiva <xref:System.Data.DataTable.RowChanging> los <xref:System.Data.DataTable.RowChanged> eventos y después de cada cambio de columna individual. En ese caso, el evento no se genera hasta que se haya <xref:System.Data.DataRow.EndEdit%2A> llamado al método, cuando <xref:System.Data.DataTable.RowChanging> los <xref:System.Data.DataTable.RowChanged> eventos y se generan una sola vez. Para obtener más información, vea [desactivar restricciones al llenar un conjunto](../data-tools/turn-off-constraints-while-filling-a-dataset.md)de datos.

 El evento que elija dependerá de la granularidad que desee para la validación. Si es importante que detecte un error inmediatamente cuando una columna cambie, compile la validación mediante el <xref:System.Data.DataTable.ColumnChanging> evento. De lo contrario, use el <xref:System.Data.DataTable.RowChanging> evento, lo que podría provocar la detección de varios errores a la vez. Además, si los datos están estructurados para que el valor de una columna se valide en función del contenido de otra columna, realice la validación durante el <xref:System.Data.DataTable.RowChanging> evento.

 Cuando se actualizan los registros, el <xref:System.Data.DataTable> objeto genera eventos a los que puede responder a medida que se producen cambios y después de que se realicen cambios.

 Si la aplicación utiliza un conjunto de un DataSet con tipo, puede crear controladores de eventos fuertemente tipados. Esto agregará cuatro eventos con tipo adicionales para los que se pueden crear controladores: `dataTableNameRowChanging` , `dataTableNameRowChanged` , `dataTableNameRowDeleting` y `dataTableNameRowDeleted` . Estos controladores de eventos con tipo pasan un argumento que incluye los nombres de columna de la tabla que facilitan la escritura y la lectura del código.

## <a name="data-update-events"></a>Eventos de actualización de datos

|Evento|Descripción|
|-----------|-----------------|
|<xref:System.Data.DataTable.ColumnChanging>|Se está cambiando el valor de una columna. El evento le pasa la fila y la columna, junto con el nuevo valor propuesto.|
|<xref:System.Data.DataTable.ColumnChanged>|Se ha cambiado el valor de una columna. El evento le pasa la fila y la columna, junto con el valor propuesto.|
|<xref:System.Data.DataTable.RowChanging>|Los cambios que se realizaron en un <xref:System.Data.DataRow> objeto están a punto de confirmarse en el conjunto de datos. Si no se ha llamado al <xref:System.Data.DataRow.BeginEdit%2A> método, <xref:System.Data.DataTable.RowChanging> se genera el evento para cada cambio en una columna inmediatamente después de que se haya <xref:System.Data.DataTable.ColumnChanging> producido el evento. Si llamó <xref:System.Data.DataRow.BeginEdit%2A> antes de realizar cambios, el <xref:System.Data.DataTable.RowChanging> evento solo se desencadena cuando se llama al <xref:System.Data.DataRow.EndEdit%2A> método.<br /><br /> El evento le pasa la fila, junto con un valor que indica qué tipo de acción (cambio, inserción, etc.) se está llevando a cabo.|
|<xref:System.Data.DataTable.RowChanged>|Se ha cambiado una fila. El evento le pasa la fila, junto con un valor que indica qué tipo de acción (cambio, inserción, etc.) se está llevando a cabo.|
|<xref:System.Data.DataTable.RowDeleting>|Se está eliminando una fila. El evento le pasa la fila, junto con un valor que indica qué tipo de acción (eliminar) se está llevando a cabo.|
|<xref:System.Data.DataTable.RowDeleted>|Se ha eliminado una fila. El evento le pasa la fila, junto con un valor que indica qué tipo de acción (eliminar) se está llevando a cabo.|

 Los <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> eventos, y <xref:System.Data.DataTable.RowDeleting> se generan durante el proceso de actualización. Puede utilizar estos eventos para validar datos o realizar otros tipos de procesamiento. Dado que la actualización está en curso durante estos eventos, puede cancelarla iniciando una excepción, lo que evita que finalice la actualización.

 Los <xref:System.Data.DataTable.ColumnChanged> <xref:System.Data.DataTable.RowChanged> eventos, y <xref:System.Data.DataTable.RowDeleted> son eventos de notificación que se producen cuando la actualización ha finalizado correctamente. Estos eventos son útiles cuando se desea realizar otras acciones en función de una actualización correcta.

## <a name="validate-data-during-column-changes"></a>Validar datos durante los cambios de columna

> [!NOTE]
> El **Diseñador de DataSet** crea una clase parcial en la que se puede Agregar la lógica de validación a un conjunto de DataSet. El DataSet generado por el diseñador no elimina ni cambia ningún código de la clase parcial.

 Puede validar los datos cuando el valor de una columna de datos cambia respondiendo al <xref:System.Data.DataTable.ColumnChanging> evento. Cuando se produce, este evento pasa un argumento de evento ( <xref:System.Data.DataColumnChangeEventArgs.ProposedValue%2A> ) que contiene el valor propuesto para la columna actual. En función del contenido de `e.ProposedValue` , puede:

- Aceptar el valor propuesto sin hacer nada.

- Rechace el valor propuesto estableciendo el error de columna ( <xref:System.Data.DataRow.SetColumnError%2A> ) desde dentro del controlador de eventos de cambio de columna.

- Utilizar opcionalmente un control <xref:System.Windows.Forms.ErrorProvider> para mostrar un mensaje de error al usuario. Para obtener más información, vea [ErrorProvider (componente](https://msdn.microsoft.com/library/c0f2e231-c5c9-413d-a507-75af2db499b6)).

  También se puede realizar la validación durante el <xref:System.Data.DataTable.RowChanging> evento. Para obtener más información, vea [Cómo: validar datos durante los cambios de fila](https://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc).

## <a name="validate-data-during-row-changes"></a>Validar datos durante los cambios de fila
 Puede escribir código para comprobar que cada columna que desee validar contiene datos que cumplen los requisitos de la aplicación. Para ello, establezca la columna para indicar que contiene un error si un valor propuesto no es aceptable. Los ejemplos siguientes establecen un error de la columna cuando la columna `Quantity` es igual o menor que 0. Los controladores de eventos que modifican la fila se parecerán a los ejemplos siguientes.

#### <a name="to-validate-data-when-a-row-changes-visual-basic"></a>Para validar los datos cuando se modifica una fila (Visual Basic)

1. Abra su conjunto de datos en el **Diseñador de Dataset**. Para obtener más información, consulte [Cómo: abrir un conjunto de datos en el diseñador de DataSet](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).

2. Haga doble clic en la barra de título de la tabla que desee validar. Esta acción crea automáticamente el controlador de eventos <xref:System.Data.DataTable.RowChanging> del control <xref:System.Data.DataTable> en el archivo de clase parcial del conjunto de datos.

    > [!TIP]
    > Haga doble clic a la izquierda del nombre de la tabla para crear el controlador de eventos que modifique la fila. Si hace doble clic en el nombre de la tabla, puede editarlo.

     [!code-vb[VbRaddataValidating#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataValidating/VB/NorthwindDataSet.vb#3)]

#### <a name="to-validate-data-when-a-row-changes-c"></a>Para validar los datos cuando se modifica una fila (C#)

1. Abra su conjunto de datos en el **Diseñador de Dataset**. Para obtener más información, consulte [Cómo: abrir un conjunto de datos en el diseñador de DataSet](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).

2. Haga doble clic en la barra de título de la tabla que desee validar. Esta acción crea un archivo de clase parcial para el control <xref:System.Data.DataTable>.

    > [!NOTE]
    > El **Diseñador de DataSet** no crea automáticamente un controlador de eventos para el evento <xref:System.Data.DataTable.RowChanging>. Tiene que crear un método para controlar el <xref:System.Data.DataTable.RowChanging> evento y ejecutar el código para enlazar el evento en el método de inicialización de la tabla.

3. Copie el código siguiente en la clase parcial:

    ```
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
 Cada fila de una tabla de datos tiene una <xref:System.Data.DataRow.RowState%2A> propiedad que realiza un seguimiento del estado actual de esa fila usando los valores de la <xref:System.Data.DataRowState> enumeración. Puede devolver filas modificadas de un conjunto de datos o una tabla de datos llamando al `GetChanges` método de <xref:System.Data.DataSet> o <xref:System.Data.DataTable> . Puede comprobar que los cambios existen antes de llamar a llamando `GetChanges` al <xref:System.Data.DataSet.HasChanges%2A> método de un conjunto de DataSet. Para obtener más información acerca de <xref:System.Data.DataSet.HasChanges%2A> , consulte [Cómo: comprobar las filas modificadas](https://msdn.microsoft.com/library/af160d20-472b-4c13-8f15-75480c39a653).

> [!NOTE]
> Después de confirmar los cambios en un conjunto de datos o en una tabla de datos (llamando al <xref:System.Data.DataSet.AcceptChanges%2A> método), el `GetChanges` método no devuelve ningún dato. Si la aplicación necesita procesar filas cambiadas, debe procesar los cambios antes de llamar al `AcceptChanges` método.

 Al llamar al <xref:System.Data.DataSet.GetChanges%2A> método de un conjunto de datos o una tabla de datos, se devuelve un nuevo conjunto de datos o una tabla de datos que solo contiene los registros que se han modificado. Si desea obtener registros específicos, por ejemplo, solo registros nuevos o solo registros modificados, puede pasar un valor de la <xref:System.Data.DataRowState> enumeración como un parámetro al `GetChanges` método.

 Utilice la <xref:System.Data.DataRowVersion> enumeración para tener acceso a las diferentes versiones de una fila (por ejemplo, los valores originales que estaban en una fila antes de procesarla).

#### <a name="to-get-all-changed-records-from-a-dataset"></a>Para obtener todos los registros modificados de un conjunto de cambios

- Llame al <xref:System.Data.DataSet.GetChanges%2A> método de un conjunto de DataSet.

     En el ejemplo siguiente se crea un nuevo conjunto `changedRecords` de documentos denominado y se rellena con todos los registros modificados de otro conjunto de archivos denominado `dataSet1` .

     [!code-csharp[VbRaddataEditing#14](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#14)]
     [!code-vb[VbRaddataEditing#14](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#14)]

#### <a name="to-get-all-changed-records-from-a-data-table"></a>Para obtener todos los registros cambiados de una tabla de datos

- Llame al <xref:System.Data.DataTable.GetChanges%2A> método de una DataTable.

     En el ejemplo siguiente se crea una nueva tabla `changedRecordsTable` de datos denominada y se rellena con todos los registros modificados de otra tabla de datos denominada `dataTable1` .

     [!code-csharp[VbRaddataEditing#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#15)]
     [!code-vb[VbRaddataEditing#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#15)]

#### <a name="to-get-all-records-that-have-a-specific-row-state"></a>Para obtener todos los registros que tienen un estado de fila específico

- Llame al `GetChanges` método de un conjunto de datos o una tabla de datos y pase un <xref:System.Data.DataRowState> valor de enumeración como argumento.

     En el ejemplo siguiente se muestra cómo crear un nuevo conjunto de elementos denominado `addedRecords` y rellenarlo solo con los registros que se han agregado al conjunto de elementos `dataSet1` .

     [!code-csharp[VbRaddataEditing#16](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#16)]
     [!code-vb[VbRaddataEditing#16](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#16)]

- En el ejemplo siguiente se muestra cómo devolver todos los registros que se agregaron recientemente a la `Customers` tabla:

     [!code-csharp[VbRaddataEditing#17](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#17)]
     [!code-vb[VbRaddataEditing#17](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#17)]

## <a name="access-the-original-version-of-a-datarow"></a>Obtener acceso a la versión original de una DataRow
 Cuando los cambios se realizan en las filas de datos, el conjunto de datos retiene tanto la versión original (<xref:System.Data.DataRowVersion>) como las versiones nuevas (<xref:System.Data.DataRowVersion>) de la fila. Por ejemplo, antes de llamar al método `AcceptChanges`, su aplicación puede tener acceso a las distintas versiones de un registro (según se defina en la enumeración <xref:System.Data.DataRowVersion>) y procesar los cambios según corresponda.

> [!NOTE]
> Las versiones diferentes de una fila solo existen después de haberla editado y antes de que se haya `AcceptChanges` llamado al método. Una vez que se ha llamado al método `AcceptChanges`, las versiones actual y original son iguales.

 Si se pasa el valor <xref:System.Data.DataRowVersion> junto con el índice de la columna (o el nombre de la columna como cadena), se devuelve el valor de la versión de fila concreta de esa columna. La columna cambiada se identifica durante <xref:System.Data.DataTable.ColumnChanging> los <xref:System.Data.DataTable.ColumnChanged> eventos y. Es un buen momento para inspeccionar las diferentes versiones de fila con fines de validación. Sin embargo, si ha suspendido temporalmente las restricciones, dichos eventos no se generarán y tendrá que identificar mediante programación Qué columnas han cambiado. Para ello, recorra en iteración la colección <xref:System.Data.DataTable.Columns%2A> y compare los distintos valores de <xref:System.Data.DataRowVersion>.

#### <a name="to-get-the-original-version-of-a-record"></a>Para obtener la versión original de un registro

- Obtenga acceso al valor de una columna pasando el <xref:System.Data.DataRowVersion> de la fila que desea devolver.

     En el ejemplo siguiente se muestra cómo utilizar un <xref:System.Data.DataRowVersion> valor para obtener el valor original de un `CompanyName` campo en un <xref:System.Data.DataRow> :

     [!code-csharp[VbRaddataEditing#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#21)]
     [!code-vb[VbRaddataEditing#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#21)]

## <a name="access-the-current-version-of-a-datarow"></a>Obtener acceso a la versión actual de una DataRow

#### <a name="to-get-the-current-version-of-a-record"></a>Para obtener la versión actual de un registro

- Obtenga acceso al valor de una columna y, a continuación, agregue un parámetro al índice que indica qué versión de una fila desea devolver.

     En el ejemplo siguiente se muestra cómo utilizar un <xref:System.Data.DataRowVersion> valor para obtener el valor actual de un `CompanyName` campo en un <xref:System.Data.DataRow> :

     [!code-csharp[VbRaddataEditing#22](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#22)]
     [!code-vb[VbRaddataEditing#22](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#22)]

## <a name="see-also"></a>Consulte también

- [Procedimiento para validar datos en el control DataGridView de formularios Windows Forms](https://msdn.microsoft.com/library/d10aef35-701e-4a3c-a684-2a2ed1aeaca6)
- [Procedimiento para mostrar iconos de error para la validación de formularios con el componente ErrorProvider de formularios Windows Forms](https://msdn.microsoft.com/library/3b681a32-9db4-497b-a34b-34980eabee46)