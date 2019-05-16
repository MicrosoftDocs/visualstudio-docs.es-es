---
title: Validar datos en conjuntos de datos | Documentos de Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2a6993d241f49261131ffad76dc50534ac8e1591
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65694875"
---
# <a name="validate-data-in-datasets"></a>Validar datos en conjuntos de datos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Validación de datos es el proceso de confirmar que los valores que se especifican en los objetos de datos se ajustan a las restricciones de esquema de un conjunto de datos. El proceso de validación también confirma que estos valores están siguiendo las reglas que se han establecido para la aplicación. Es una buena práctica para validar los datos antes de enviar actualizaciones a la base de datos subyacente. Esto reduce los errores, así como el número de viajes de ida y vuelta entre una aplicación y la base de datos.  
  
 Puede confirmar que los datos que se escriben en un conjunto de datos están válidos mediante la creación de comprobaciones de validación en el conjunto de datos. El conjunto de datos puede comprobar los datos independientemente de cómo se realiza la actualización, ya sea directamente mediante los controles en un formulario, dentro de un componente, o en alguna otra manera. Dado que el conjunto de datos es parte de la aplicación (a diferencia de la base de datos de back-end), es un lugar lógico para compilar la validación específica de la aplicación.  
  
 Es el mejor lugar para agregar validación a la aplicación en el archivo de clase parcial del conjunto de datos. En [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] o [!INCLUDE[csprcs](../includes/csprcs-md.md)], abra el **Diseñador de Dataset** y haga doble clic en la columna o tabla para la que desea crear la validación. Esta acción crea automáticamente un <xref:System.Data.DataTable.ColumnChanging> o <xref:System.Data.DataTable.RowChanging> controlador de eventos. Para obtener más información, vea [Cómo: Validar los datos durante los cambios de columna](https://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5) o [Cómo: Validar los datos durante los cambios de fila](https://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc). Para obtener un ejemplo completo, vea [Tutorial: Agregar validación a un conjunto de datos](https://msdn.microsoft.com/library/09351fab-d670-45e3-b53a-a944eff717e7).  
  
## <a name="validate-data"></a>Validar datos  
 Validación dentro de un conjunto de datos puede realizarse en las siguientes maneras:  
  
- Mediante la creación de su propia validación específica de la aplicación puede comprobar los valores en una columna de datos individuales durante los cambios.  Para obtener más información, vea [Cómo: Validar los datos durante los cambios de columna](https://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5).  
  
- Creando su propia validación específica de la aplicación que puede comprobar los datos a los valores mientras un completo de datos está cambiando la fila. Para obtener más información, vea [Cómo: Validar los datos durante los cambios de fila](https://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc).  
  
- Mediante la creación de claves, restricciones únicas, y así sucesivamente como parte de la definición de esquema real del conjunto de datos. Para obtener más información sobre cómo incorporar la validación a la definición de esquema, vea [restringir un objeto DataColumn para contener valores únicos](https://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df).  
  
- Al establecer las propiedades de la <xref:System.Data.DataColumn> objeto, como <xref:System.Data.DataColumn.MaxLength%2A>, <xref:System.Data.DataColumn.AllowDBNull%2A>, y <xref:System.Data.DataColumn.Unique%2A>.  
  
  Varios eventos generados por el <xref:System.Data.DataTable> objeto cuando se produce un cambio en un registro:  
  
- El <xref:System.Data.DataTable.ColumnChanging> y <xref:System.Data.DataTable.ColumnChanged> eventos se producen durante y después de cada cambio realizado en una columna individual. El <xref:System.Data.DataTable.ColumnChanging> evento es útil cuando desea validar los cambios en columnas específicas. Información sobre el cambio propuesto se pasa como un argumento con el evento. Para obtener más información, vea [Cómo: Validar los datos durante los cambios de columna](https://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5).  
  
- El <xref:System.Data.DataTable.RowChanging> y <xref:System.Data.DataTable.RowChanged> eventos se producen durante y después de cualquier cambio en una fila. El <xref:System.Data.DataTable.RowChanging> eventos es más general. Indica que se está produciendo un cambio en alguna parte de la fila, pero no sabe qué columna ha cambiado. Para obtener más información, vea [Cómo: Validar los datos durante los cambios de fila](https://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc).  
  
  De forma predeterminada, cada cambio realizado en una columna produce cuatro eventos. La primera es la <xref:System.Data.DataTable.ColumnChanging> y <xref:System.Data.DataTable.ColumnChanged> eventos para la columna que se va a cambiar. A continuación se encuentran los <xref:System.Data.DataTable.RowChanging> y <xref:System.Data.DataTable.RowChanged> eventos. Si se realizan varios cambios a la fila, los eventos se generan para cada cambio.  
  
> [!NOTE]
> La fila de datos <xref:System.Data.DataRow.BeginEdit%2A> método desactiva el <xref:System.Data.DataTable.RowChanging> y <xref:System.Data.DataTable.RowChanged> eventos después de cada cambio de columna individual. En ese caso, el evento no se produce hasta que el <xref:System.Data.DataRow.EndEdit%2A> se ha llamado al método, cuando el <xref:System.Data.DataTable.RowChanging> y <xref:System.Data.DataTable.RowChanged> se generan eventos una sola vez. Para obtener más información, consulte [desactivar restricciones al llenar un conjunto de datos](../data-tools/turn-off-constraints-while-filling-a-dataset.md).  
  
 El evento que elija depende de cómo de pormenorizado desea que la validación que se va. Si es importante detectar un error inmediatamente cuando se cambia una columna, compilar la validación mediante el uso de la <xref:System.Data.DataTable.ColumnChanging> eventos. En caso contrario, use el <xref:System.Data.DataTable.RowChanging> eventos, lo que podrían ocasionar detectar varios errores al mismo tiempo. Además, si los datos están estructurados para que se valida el valor de una columna en función del contenido de otra columna, a continuación, realizar la validación durante la <xref:System.Data.DataTable.RowChanging> eventos.  
  
 Cuando se actualizan registros, la <xref:System.Data.DataTable> objeto provoca eventos que se pueden responder a medida que se realizan cambios y después de realizar cambios.  
  
 Si la aplicación utiliza un conjunto de datos con tipo, puede crear controladores de eventos fuertemente tipados. Esto agregará cuatro eventos con tipo adicionales que se pueden crear controladores para: `dataTableNameRowChanging`, `dataTableNameRowChanged`, `dataTableNameRowDeleting`, y `dataTableNameRowDeleted`. Estos controladores de eventos con tipo pasan un argumento que incluye los nombres de columna de la tabla que resulte más fácil leer y escribir código.  
  
## <a name="data-update-events"></a>Eventos de actualización de datos  
  
|evento|Descripción|  
|-----------|-----------------|  
|<xref:System.Data.DataTable.ColumnChanging>|Se está cambiando el valor de una columna. El evento pasa la fila y columna, junto con el nuevo valor propuesto.|  
|<xref:System.Data.DataTable.ColumnChanged>|Se cambió el valor de una columna. El evento pasa la fila y columna, junto con el valor propuesto.|  
|<xref:System.Data.DataTable.RowChanging>|Los cambios realizados en un <xref:System.Data.DataRow> objeto están a punto de confirmarse en el conjunto de datos. Si no ha llamado el <xref:System.Data.DataRow.BeginEdit%2A> método, el <xref:System.Data.DataTable.RowChanging> evento se desencadena para cada cambio realizado en una columna inmediatamente después de la <xref:System.Data.DataTable.ColumnChanging> ha generado el evento. Si llama a <xref:System.Data.DataRow.BeginEdit%2A> antes de realizar cambios, el <xref:System.Data.DataTable.RowChanging> evento se produce únicamente cuando se llama el <xref:System.Data.DataRow.EndEdit%2A> método.<br /><br /> El evento pasa la fila, junto con un valor que indica qué tipo de acción (cambio, inserción etc.) se está realizando.|  
|<xref:System.Data.DataTable.RowChanged>|Ha cambiado una fila. El evento pasa la fila, junto con un valor que indica qué tipo de acción (cambio, inserción etc.) se está realizando.|  
|<xref:System.Data.DataTable.RowDeleting>|Se está eliminando una fila. El evento pasa la fila, junto con un valor que indica qué tipo de acción (eliminar) se está realizando.|  
|<xref:System.Data.DataTable.RowDeleted>|Se ha eliminado una fila. El evento pasa la fila, junto con un valor que indica qué tipo de acción (eliminar) se está realizando.|  
  
 El <xref:System.Data.DataTable.ColumnChanging>, <xref:System.Data.DataTable.RowChanging>, y <xref:System.Data.DataTable.RowDeleting> eventos se generan durante el proceso de actualización. Puede usar estos eventos para validar los datos o realizar otros tipos de procesamiento. Dado que la actualización está en curso durante estos eventos, puede cancelar iniciando una excepción, lo que impide que la actualización de acabado.  
  
 El <xref:System.Data.DataTable.ColumnChanged>, <xref:System.Data.DataTable.RowChanged> y <xref:System.Data.DataTable.RowDeleted> son eventos de notificación que se producen cuando la actualización ha finalizado correctamente. Estos eventos son útiles cuando desea realizar una acción en función de una actualización correcta.  
  
## <a name="validate-data-during-column-changes"></a>Validar los datos durante los cambios de columna  
  
> [!NOTE]
> El **Diseñador de Dataset** crea una clase parcial en la validación de que se puede agregar lógica a un conjunto de datos. El conjunto de datos generado por el diseñador no eliminar o cambiar el código de la clase parcial.  
  
 Puede validar los datos cuando cambia el valor en una columna de datos respondiendo a las <xref:System.Data.DataTable.ColumnChanging> eventos. Cuando se genera, este evento pasa un argumento de evento (<xref:System.Data.DataColumnChangeEventArgs.ProposedValue%2A>) que contiene el valor propuesto para la columna actual. Según el contenido de `e.ProposedValue`, puede:  
  
- Aceptar el valor propuesto sin hacer nada.  
  
- Rechazar el valor propuesto estableciendo el error de la columna (<xref:System.Data.DataRow.SetColumnError%2A>) desde dentro del controlador de eventos de cambio de columna.  
  
- Utilizar opcionalmente un control <xref:System.Windows.Forms.ErrorProvider> para mostrar un mensaje de error al usuario. Para obtener más información, consulte [del componente ErrorProvider](https://msdn.microsoft.com/library/c0f2e231-c5c9-413d-a507-75af2db499b6).  
  
  También se puede realizar la validación durante la <xref:System.Data.DataTable.RowChanging> eventos. Para obtener más información, vea [Cómo: Validar los datos durante los cambios de fila](https://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc).  
  
## <a name="validate-data-during-row-changes"></a>Validar los datos durante los cambios de fila  
 Puede escribir código para comprobar que cada columna que desee validar contiene datos que cumplen los requisitos de la aplicación. Para ello, establezca la columna para indicar que contiene un error si un valor propuesto no es aceptable. Los ejemplos siguientes establecen un error de la columna cuando la columna `Quantity` es igual o menor que 0. Los controladores de eventos que modifican la fila se parecerán a los ejemplos siguientes.  
  
#### <a name="to-validate-data-when-a-row-changes-visual-basic"></a>Para validar los datos cuando se modifica una fila (Visual Basic)  
  
1. Abra su conjunto de datos en el **Diseñador de Dataset**. Para obtener más información, vea [Cómo: Abrir un conjunto de datos en el Diseñador de Dataset](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2. Haga doble clic en la barra de título de la tabla que desee validar. Esta acción crea automáticamente el controlador de eventos <xref:System.Data.DataTable.RowChanging> del control <xref:System.Data.DataTable> en el archivo de clase parcial del conjunto de datos.  
  
    > [!TIP]
    > Haga doble clic a la izquierda del nombre de la tabla para crear el controlador de eventos que modifique la fila. Si hace doble clic en el nombre de tabla, se puede modificar.  
  
     [!code-vb[VbRaddataValidating#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataValidating/VB/NorthwindDataSet.vb#3)]  
  
#### <a name="to-validate-data-when-a-row-changes-c"></a>Para validar los datos cuando se modifica una fila (C#)  
  
1. Abra su conjunto de datos en el **Diseñador de Dataset**. Para obtener más información, vea [Cómo: Abrir un conjunto de datos en el Diseñador de Dataset](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2. Haga doble clic en la barra de título de la tabla que desee validar. Esta acción crea un archivo de clase parcial para el control <xref:System.Data.DataTable>.  
  
    > [!NOTE]
    > El **Diseñador de DataSet** no crea automáticamente un controlador de eventos para el evento <xref:System.Data.DataTable.RowChanging>. Tendrá que crear un método para controlar la <xref:System.Data.DataTable.RowChanging> eventos y ejecutar código para enlazar el evento en el método de inicialización de la tabla.  
  
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
 Cada fila de una tabla de datos tiene un <xref:System.Data.DataRow.RowState%2A> propiedad que se realiza un seguimiento de estado actual de esa fila mediante el uso de los valores de la <xref:System.Data.DataRowState> enumeración. Puede devolver las filas modificadas desde una conjunto de datos o tabla de datos mediante una llamada a la `GetChanges` método de un <xref:System.Data.DataSet> o <xref:System.Data.DataTable>. Puede comprobar que existen cambios antes de llamar a `GetChanges` mediante una llamada a la <xref:System.Data.DataSet.HasChanges%2A> método de un conjunto de datos. Para más información sobre <xref:System.Data.DataSet.HasChanges%2A>, vea [Cómo: Compruebe si hay filas modificadas](https://msdn.microsoft.com/library/af160d20-472b-4c13-8f15-75480c39a653).  
  
> [!NOTE]
> Después de confirmar los cambios a una conjunto de datos o tabla de datos (mediante una llamada a la <xref:System.Data.DataSet.AcceptChanges%2A> método), el `GetChanges` método no devuelve ningún dato. Si la aplicación necesita procesar las filas modificadas, debe procesar los cambios antes de llamar a la `AcceptChanges` método.  
  
 Una llamada a la <xref:System.Data.DataSet.GetChanges%2A> método de una conjunto de datos o tabla de datos devuelve una nueva tabla de datos o conjunto de datos que contiene solo los registros que se han cambiado. Si desea obtener registros específicos, por ejemplo, solo los registros nuevos o sólo los registros modificados, puede pasar un valor de la <xref:System.Data.DataRowState> enumeración como un parámetro a la `GetChanges` método.  
  
 Use el <xref:System.Data.DataRowVersion> enumeración para tener acceso a las distintas versiones de una fila (por ejemplo, los valores originales que se encontraban en una fila antes de procesarlo).  
  
#### <a name="to-get-all-changed-records-from-a-dataset"></a>Para obtener todos los registros modificados de un conjunto de datos  
  
- Llame a la <xref:System.Data.DataSet.GetChanges%2A> método de un conjunto de datos.  
  
     En el ejemplo siguiente se crea un nuevo conjunto de datos denominado `changedRecords` y lo rellena con todos los registros modificados desde otro conjunto de datos denominado `dataSet1`.  
  
     [!code-csharp[VbRaddataEditing#14](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#14)]
     [!code-vb[VbRaddataEditing#14](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#14)]  
  
#### <a name="to-get-all-changed-records-from-a-data-table"></a>Para obtener todos los registros modificados desde una tabla de datos  
  
- Llame a la <xref:System.Data.DataTable.GetChanges%2A> método de una DataTable.  
  
     En el ejemplo siguiente se crea una nueva tabla de datos denominada `changedRecordsTable` y lo rellena con todos los registros modificados de otra tabla de datos denominada `dataTable1`.  
  
     [!code-csharp[VbRaddataEditing#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#15)]
     [!code-vb[VbRaddataEditing#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#15)]  
  
#### <a name="to-get-all-records-that-have-a-specific-row-state"></a>Para obtener todos los registros que tienen un estado específico  
  
- Llame a la `GetChanges` método de un conjunto de datos o tabla de datos y pase un <xref:System.Data.DataRowState> valor de enumeración como argumento.  
  
     El ejemplo siguiente muestra cómo crear un nuevo conjunto de datos denominado `addedRecords` y rellenarla solo con los registros que se han agregado a la `dataSet1` conjunto de datos.  
  
     [!code-csharp[VbRaddataEditing#16](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#16)]
     [!code-vb[VbRaddataEditing#16](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#16)]  
  
- El ejemplo siguiente muestra cómo devolver todos los registros que se agregaron recientemente a la `Customers` tabla:  
  
     [!code-csharp[VbRaddataEditing#17](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#17)]
     [!code-vb[VbRaddataEditing#17](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#17)]  
  
## <a name="access-the-original-version-of-a-datarow"></a>Acceso a la versión original de un objeto DataRow  
 Cuando los cambios se realizan en las filas de datos, el conjunto de datos retiene tanto la versión original (<xref:System.Data.DataRowVersion>) como las versiones nuevas (<xref:System.Data.DataRowVersion>) de la fila. Por ejemplo, antes de llamar al método `AcceptChanges`, su aplicación puede tener acceso a las distintas versiones de un registro (según se defina en la enumeración <xref:System.Data.DataRowVersion>) y procesar los cambios según corresponda.  
  
> [!NOTE]
> Versiones diferentes de una fila existen solo una vez que se ha editado y antes de que el `AcceptChanges` ha llamado al método. Una vez que se ha llamado al método `AcceptChanges`, las versiones actual y original son iguales.  
  
 Si se pasa el valor <xref:System.Data.DataRowVersion> junto con el índice de la columna (o el nombre de la columna como cadena), se devuelve el valor de la versión de fila concreta de esa columna. La columna modificada se identifica durante la <xref:System.Data.DataTable.ColumnChanging> y <xref:System.Data.DataTable.ColumnChanged> eventos. Esto es un buen momento para examinar las versiones de fila diferente para la validación. Sin embargo, si ha suspendido las restricciones temporalmente, esos eventos no se generará y deberá mediante programación es identificar las columnas que han cambiado. Para ello, recorra en iteración la colección <xref:System.Data.DataTable.Columns%2A> y compare los distintos valores de <xref:System.Data.DataRowVersion>.  
  
#### <a name="to-get-the-original-version-of-a-record"></a>Para obtener la versión original de un registro  
  
- Obtener acceso al valor de una columna pasando el <xref:System.Data.DataRowVersion> de la fila que desea devolver.  
  
     El ejemplo siguiente muestra cómo usar un <xref:System.Data.DataRowVersion> para obtener el valor original de un `CompanyName` campo un <xref:System.Data.DataRow>:  
  
     [!code-csharp[VbRaddataEditing#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#21)]
     [!code-vb[VbRaddataEditing#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#21)]  
  
## <a name="access-the-current-version-of-a-datarow"></a>Acceso a la versión actual de un objeto DataRow  
  
#### <a name="to-get-the-current-version-of-a-record"></a>Para obtener la versión actual de un registro  
  
- Obtener acceso al valor de una columna y, a continuación, agregue un parámetro al índice que indica qué versión de una fila que desea devolver.  
  
     El ejemplo siguiente muestra cómo usar un <xref:System.Data.DataRowVersion> para obtener el valor actual de un `CompanyName` campo un <xref:System.Data.DataRow>:  
  
     [!code-csharp[VbRaddataEditing#22](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#22)]
     [!code-vb[VbRaddataEditing#22](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#22)]  
  
## <a name="see-also"></a>Vea también

- [Cómo: Validar datos en el Control DataGridView de formularios de Windows](https://msdn.microsoft.com/library/d10aef35-701e-4a3c-a684-2a2ed1aeaca6)   
- [Cómo: Mostrar iconos de Error de validación de formularios con el componente ErrorProvider de formularios Windows Forms](https://msdn.microsoft.com/library/3b681a32-9db4-497b-a34b-34980eabee46)