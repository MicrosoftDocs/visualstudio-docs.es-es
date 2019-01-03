---
title: Agregar validación a un conjunto de datos de n niveles
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, validating
- validation [Visual Basic], n-tier data applications
- validating n-tier data applications
ms.assetid: 34ce4db6-09bb-4b46-b435-b2514aac52d3
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 20a1cd033763e7aa98eb2798357109e300deaff1
ms.sourcegitcommit: 159ed9d4f56cdc1dff2fd19d9dffafe77e46cd4e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2018
ms.locfileid: "53739473"
---
# <a name="add-validation-to-an-n-tier-dataset"></a>Agregar validación a un conjunto de datos de n niveles
Agregar validación a un conjunto de datos separado en una solución de n niveles es básicamente igual que agregar validación a un conjunto de datos de un solo archivo (un conjunto de datos en un único proyecto). La ubicación sugerida para realizar la validación en datos está durante <xref:System.Data.DataTable.ColumnChanging> y/o los eventos <xref:System.Data.DataTable.RowChanging> de una tabla de datos.

 El conjunto de datos proporciona la funcionalidad para crear clases parciales a los que puede agregar código de usuario a los eventos de cambio de columna y fila de las tablas de datos del conjunto de datos. Para obtener más información sobre cómo agregar código a un conjunto de datos en una solución de n niveles, vea [agregar código a conjuntos de datos en aplicaciones de n niveles](../data-tools/add-code-to-datasets-in-n-tier-applications.md), y [agregar código a TableAdapters en aplicaciones de n niveles](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md). Para obtener más información acerca de las clases parciales, vea [Cómo: Dividir una clase en clases parciales (Diseñador de clases)](../ide/class-designer/how-to-split-a-class-into-partial-classes.md) o [clases y métodos parciales](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).

> [!NOTE]
>  Al separar conjuntos de datos de los TableAdapters (estableciendo la **DataSet Project** propiedad), las clases de conjunto de datos parciales existentes en el proyecto no se moverá automáticamente. Las clases de conjunto de datos parciales existentes se deben mover manualmente al proyecto de conjunto de datos.

> [!NOTE]
>  El Diseñador de Dataset no crea automáticamente un controlador de eventos en C# para los eventos <xref:System.Data.DataTable.ColumnChanging> y <xref:System.Data.DataTable.RowChanging>. Tendrá que crear un controlador de eventos manualmente y enlazar el controlador de eventos al evento subyacente. Los procedimientos siguientes describen cómo crear los controladores de eventos necesaria en Visual Basic y C#.

## <a name="validate-changes-to-individual-columns"></a>Validar cambios para columnas individuales
 Valide los valores en columnas individual administrando el evento <xref:System.Data.DataTable.ColumnChanging>. El <xref:System.Data.DataTable.ColumnChanging> evento se desencadena cuando se modifica un valor en una columna. Crear un controlador de eventos para el <xref:System.Data.DataTable.ColumnChanging> eventos haciendo doble clic en la columna que desee en el **Diseñador de Dataset**.

 La primera vez que se hace doble clic en una columna, el diseñador genera un controlador de eventos para el evento <xref:System.Data.DataTable.ColumnChanging>. Un `If...Then` instrucción también se crea que comprueba la columna concreta. Por ejemplo, el código siguiente se genera al hacer doble clic el **RequiredDate** columna en la tabla Orders de Northwind:

```vb
Private Sub OrdersDataTable_ColumnChanging(ByVal sender As System.Object, ByVal e As System.Data.DataColumnChangeEventArgs) Handles Me.ColumnChanging
    If (e.Column.ColumnName = Me.RequiredDateColumn.ColumnName) Then
        ' Add validation code here.
    End If
End Sub
```

> [!NOTE]
>  En proyectos C#, el Diseñador de DataSet crea únicamente las clases parciales para el conjunto de datos y las tablas individuales en el conjunto de datos. El Diseñador de DataSet no crea automáticamente los controladores de eventos para los eventos <xref:System.Data.DataTable.ColumnChanging> y <xref:System.Data.DataTable.RowChanging> en C#, como lo hace en Visual Basic. En los proyectos de C#, tendrá que construir manualmente un método para controlar el evento y enlazar el método para el evento subyacente. El procedimiento siguiente proporciona los pasos para crear los controladores de eventos necesarios tanto en Visual Basic como en C#.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-add-validation-during-changes-to-individual-column-values"></a>Para agregar la validación durante los cambios a los valores de columna individuales

1.  Abra el conjunto de datos haciendo doble clic en el *.xsd* archivo **el Explorador de soluciones**. Para obtener más información, vea [Tutorial: Creación de un conjunto de datos en el Diseñador de Dataset](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2.  Haga doble clic en la columna que desee validar. Esta acción crea el controlador de eventos <xref:System.Data.DataTable.ColumnChanging>.

    > [!NOTE]
    >  El Diseñador de DataSet no crea ningún controlador de eventos automáticamente para el evento de C#. El código que es necesario para controlar el evento en C# se incluye en la sección siguiente. `SampleColumnChangingEvent` se crea y, a continuación, vincula la <xref:System.Data.DataTable.ColumnChanging> eventos en el <xref:System.Data.DataTable.EndInit%2A> método.

3.  Agregue el código para comprobar que `e.ProposedValue` contiene datos que son compatibles con los requisitos de la aplicación. Si el valor propuesto no es aceptable, establezca la columna para indicar que contiene un error.

     El siguiente ejemplo de código que valida la **cantidad** columna contiene un valor mayor que 0. Si **cantidad** es menor o igual a 0, la columna se establece en un error. El `Else` cláusula borra el error si **cantidad** es mayor que 0. El código del controlador de eventos de la columna que cambia debe presentar un aspecto similar al siguiente:

    ```vb
    If (e.Column.ColumnName = Me.QuantityColumn.ColumnName) Then
        If CType(e.ProposedValue, Short) <= 0 Then
            e.Row.SetColumnError(e.Column, "Quantity must be greater than 0")
        Else
            e.Row.SetColumnError(e.Column, "")
        End If
    End If
    ```
    ```csharp
    // Add this code to the DataTable partial class.

    public override void EndInit()
    {
        base.EndInit();
        // Hook up the ColumnChanging event
        // to call the SampleColumnChangingEvent method.
        ColumnChanging += SampleColumnChangingEvent;
    }

    public void SampleColumnChangingEvent(object sender, System.Data.DataColumnChangeEventArgs e)
    {
        if (e.Column.ColumnName == QuantityColumn.ColumnName)
        {
            if ((short)e.ProposedValue <= 0)
            {
                e.Row.SetColumnError("Quantity", "Quantity must be greater than 0");
            }
            else
            {
                e.Row.SetColumnError("Quantity", "");
            }
        }
    }
    ```

## <a name="validate-changes-to-whole-rows"></a>Validar cambios para filas completas
 Valide los valores en filas completas administrando el evento <xref:System.Data.DataTable.RowChanging>. Se produce el evento <xref:System.Data.DataTable.RowChanging> cuando se confirman los valores en todas las columnas. Esto es necesario para validar en el evento <xref:System.Data.DataTable.RowChanging> cuando el valor en una columna depende del valor en otra columna. Por ejemplo, tenga en cuenta OrderDate y RequiredDate en la tabla Orders en Northwind.

 Cuando se incluyen los pedidos, la validación garantiza que un pedido no se escribe en la fecha requerida (RequiredDate) ni antes de la fecha de pedido (OrderDate). En este ejemplo, los valores para ambas columnas RequiredDate y OrderDate necesitan compararse, por ello no tiene sentido validar un cambio en una columna individual.

 Crear un controlador de eventos para el <xref:System.Data.DataTable.RowChanging> eventos haciendo doble clic en el nombre de tabla en la barra de título de la tabla en la **Diseñador de Dataset**.

#### <a name="to-add-validation-during-changes-to-whole-rows"></a>Para agregar la validación durante los cambios en las filas completas

1.  Abra el conjunto de datos haciendo doble clic en el *.xsd* archivo **el Explorador de soluciones**. Para obtener más información, vea [Tutorial: Creación de un conjunto de datos en el Diseñador de Dataset](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2.  Haga doble clic en la barra de título de la tabla de datos en el diseñador.

     Se crea una clase parcial con un controlador de eventos `RowChanging` y se abre en el Editor de código.

    > [!NOTE]
    >  El Diseñador de DataSet no crea automáticamente un controlador para el evento <xref:System.Data.DataTable.RowChanging> en proyectos escritos en C#. Tendrá que crear un método para controlar la <xref:System.Data.DataTable.RowChanging> eventos y ejecutar código, a continuación, enlazar el evento en el método de inicialización de la tabla.

3.  Agregue el código de usuario dentro de la declaración de clase parcial.

4.  El código siguiente muestra dónde agregar código de usuario para validar durante el <xref:System.Data.DataTable.RowChanging> eventos. El ejemplo de C# también incluye código para enlazar el método de controlador de eventos hasta el `OrdersRowChanging` eventos.

    ```vb
    Partial Class OrdersDataTable
        Private Sub OrdersDataTable_OrdersRowChanging(ByVal sender As System.Object, ByVal e As OrdersRowChangeEvent) Handles Me.OrdersRowChanging
            ' Add logic to validate columns here.
            If e.Row.RequiredDate <= e.Row.OrderDate Then
                ' Set the RowError if validation fails.
                e.Row.RowError = "Required Date cannot be on or before the OrderDate"
            Else
                ' Clear the RowError when validation passes.
                e.Row.RowError = ""
            End If
        End Sub
    End Class
    ```
    ```csharp
    partial class OrdersDataTable
    {
        public override void EndInit()
        {
            base.EndInit();
            // Hook up the event to the
            // RowChangingEvent method.
            OrdersRowChanging += RowChangingEvent;
        }

        public void RowChangingEvent(object sender, OrdersRowChangeEvent e)
        {
            // Perform the validation logic.
            if (e.Row.RequiredDate <= e.Row.OrderDate)
            {
                // Set the row to an error when validation fails.
                e.Row.RowError = "Required Date cannot be on or before the OrderDate";
            }
            else
            {
                // Clear the RowError if validation passes.
                e.Row.RowError = "";
            }
        }
    }
    ```

## <a name="see-also"></a>Vea también

- [Introducción a las aplicaciones de datos de n niveles](../data-tools/n-tier-data-applications-overview.md)
- [Tutorial: Creación de una aplicación de datos con N niveles](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Validar los datos en conjuntos de datos](../data-tools/validate-data-in-datasets.md)