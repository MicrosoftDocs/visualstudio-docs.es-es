---
title: Agregar validación a un conjunto de datos de n niveles
description: Agregar validación a un conjunto de elementos de n niveles en Visual Studio. Validar cambios en columnas individuales o filas completas.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, validating
- validation [Visual Basic], n-tier data applications
- validating n-tier data applications
ms.assetid: 34ce4db6-09bb-4b46-b435-b2514aac52d3
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 4c7891df6de9f12df324c8d79eed5dda0e091d9a
ms.sourcegitcommit: 63ff7cb85b3baeeb713240d17bb2a18497f3741d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/11/2020
ms.locfileid: "94518757"
---
# <a name="add-validation-to-an-n-tier-dataset"></a>Agregar validación a un conjunto de datos de n niveles
Agregar validación a un conjunto de datos separado en una solución de n niveles es básicamente igual que agregar validación a un conjunto de datos de un solo archivo (un conjunto de datos en un único proyecto). La ubicación sugerida para realizar la validación en datos está durante <xref:System.Data.DataTable.ColumnChanging> y/o los eventos <xref:System.Data.DataTable.RowChanging> de una tabla de datos.

El conjunto de datos proporciona la funcionalidad para crear clases parciales a las que se puede agregar código de usuario a los eventos de cambio de columna y fila de las tablas de datos del conjunto de datos. Para obtener más información sobre cómo agregar código a un conjunto de datos en una solución de n niveles, vea [Agregar código a conjuntos de datos en aplicaciones de n niveles](../data-tools/add-code-to-datasets-in-n-tier-applications.md)y [Agregar código a TableAdapters en aplicaciones de n niveles](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md). Para obtener más información sobre las clases parciales, vea [Cómo: dividir una clase en clases parciales (diseñador de clases)](../ide/class-designer/how-to-split-a-class-into-partial-classes.md) o [clases y métodos parciales](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).

> [!NOTE]
> Cuando se separan los conjuntos de valores de los TableAdapters (estableciendo la propiedad **DataSet Project** ), las clases de conjunto de tipos parciales existentes en el proyecto no se moverán automáticamente. Las clases de conjunto de tipos parciales existentes deben moverse manualmente al proyecto de conjunto de DataSet.

> [!NOTE]
> El Diseñador de Dataset no crea automáticamente un controlador de eventos en C# para los eventos <xref:System.Data.DataTable.ColumnChanging> y <xref:System.Data.DataTable.RowChanging>. Tiene que crear manualmente un controlador de eventos y enlazar el controlador de eventos al evento subyacente. En los procedimientos siguientes se describe cómo crear los controladores de eventos necesarios tanto en Visual Basic como en C#.

## <a name="validate-changes-to-individual-columns"></a>Validar cambios en columnas individuales
Valide los valores en columnas individual administrando el evento <xref:System.Data.DataTable.ColumnChanging>. El <xref:System.Data.DataTable.ColumnChanging> evento se desencadena cuando se modifica un valor de una columna. Cree un controlador de eventos para el <xref:System.Data.DataTable.ColumnChanging> evento haciendo doble clic en la columna que desee en el **Diseñador de DataSet**.

La primera vez que se hace doble clic en una columna, el diseñador genera un controlador de eventos para el evento <xref:System.Data.DataTable.ColumnChanging>. `If...Then`También se crea una instrucción que comprueba la columna específica. Por ejemplo, el código siguiente se genera al hacer doble clic en la columna **FechaRequerida** de la tabla Orders de Northwind:

```vb
Private Sub OrdersDataTable_ColumnChanging(ByVal sender As System.Object, ByVal e As System.Data.DataColumnChangeEventArgs) Handles Me.ColumnChanging
    If (e.Column.ColumnName = Me.RequiredDateColumn.ColumnName) Then
        ' Add validation code here.
    End If
End Sub
```

> [!NOTE]
> En proyectos C#, el Diseñador de DataSet crea únicamente las clases parciales para el conjunto de datos y las tablas individuales en el conjunto de datos. El Diseñador de DataSet no crea automáticamente los controladores de eventos para los eventos <xref:System.Data.DataTable.ColumnChanging> y <xref:System.Data.DataTable.RowChanging> en C#, como lo hace en Visual Basic. En los proyectos de C#, tiene que crear manualmente un método para controlar el evento y enlazar el método al evento subyacente. El procedimiento siguiente proporciona los pasos para crear los controladores de eventos necesarios tanto en Visual Basic como en C#.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-add-validation-during-changes-to-individual-column-values"></a>Para agregar la validación durante los cambios a los valores de columna individuales

1. Abra el conjunto de archivos haciendo doble clic en el archivo *. xsd* en **Explorador de soluciones**. Para obtener más información, vea [Tutorial: crear un conjunto de datos en el diseñador de DataSet](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Haga doble clic en la columna que desee validar. Esta acción crea el controlador de eventos <xref:System.Data.DataTable.ColumnChanging>.

    > [!NOTE]
    > El Diseñador de DataSet no crea ningún controlador de eventos automáticamente para el evento de C#. El código necesario para controlar el evento en C# se incluye en la sección siguiente. `SampleColumnChangingEvent` se crea y, a continuación, se enlaza al <xref:System.Data.DataTable.ColumnChanging> evento en el <xref:System.Data.DataTable.EndInit%2A> método.

3. Agregue el código para comprobar que `e.ProposedValue` contiene datos que son compatibles con los requisitos de la aplicación. Si el valor propuesto no es aceptable, establezca la columna para indicar que contiene un error.

     En el ejemplo de código siguiente se valida que la columna **Quantity** contiene un valor mayor que 0. Si **Quantity** es menor o igual que 0, la columna se establece en un error. La `Else` cláusula borra el error si la **cantidad** es superior a 0. El código del controlador de eventos de la columna que cambia debe presentar un aspecto similar al siguiente:

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

## <a name="validate-changes-to-whole-rows"></a>Validar cambios en filas completas
Valide los valores en filas completas administrando el evento <xref:System.Data.DataTable.RowChanging>. Se produce el evento <xref:System.Data.DataTable.RowChanging> cuando se confirman los valores en todas las columnas. Esto es necesario para validar en el evento <xref:System.Data.DataTable.RowChanging> cuando el valor en una columna depende del valor en otra columna. Por ejemplo, tenga en cuenta OrderDate y RequiredDate en la tabla Orders en Northwind.

Cuando se incluyen los pedidos, la validación garantiza que un pedido no se escribe en la fecha requerida (RequiredDate) ni antes de la fecha de pedido (OrderDate). En este ejemplo, los valores para ambas columnas RequiredDate y OrderDate necesitan compararse, por ello no tiene sentido validar un cambio en una columna individual.

Cree un controlador de eventos para el <xref:System.Data.DataTable.RowChanging> evento haciendo doble clic en el nombre de la tabla en la barra de título de la tabla en el **Diseñador de DataSet**.

#### <a name="to-add-validation-during-changes-to-whole-rows"></a>Para agregar la validación durante los cambios en las filas completas

1. Abra el conjunto de archivos haciendo doble clic en el archivo *. xsd* en **Explorador de soluciones**. Para obtener más información, vea [Tutorial: crear un conjunto de datos en el diseñador de DataSet](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Haga doble clic en la barra de título de la tabla de datos en el diseñador.

     Se crea una clase parcial con un controlador de eventos `RowChanging` y se abre en el Editor de código.

    > [!NOTE]
    > El Diseñador de DataSet no crea automáticamente un controlador para el evento <xref:System.Data.DataTable.RowChanging> en proyectos escritos en C#. Tiene que crear un método para controlar el <xref:System.Data.DataTable.RowChanging> evento y ejecutar el código enlazando el evento en el método de inicialización de la tabla.

3. Agregue el código de usuario dentro de la declaración de clase parcial.

4. En el código siguiente se muestra dónde agregar el código de usuario que se va a validar durante el <xref:System.Data.DataTable.RowChanging> evento. En el ejemplo de C# también se incluye código para enlazar el método de control de eventos al `OrdersRowChanging` evento.

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

## <a name="see-also"></a>Consulte también

- [Información general sobre las aplicaciones de datos con N niveles](../data-tools/n-tier-data-applications-overview.md)
- [Tutorial: crear una aplicación de datos de N niveles](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Validar los datos en conjuntos de datos](../data-tools/validate-data-in-datasets.md)
