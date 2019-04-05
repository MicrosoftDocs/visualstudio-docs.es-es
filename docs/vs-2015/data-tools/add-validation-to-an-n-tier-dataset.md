---
title: Agregar validación a un conjunto de datos con n niveles | Documentos de Microsoft
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
- n-tier applications, validating
- validation [Visual Basic], n-tier data applications
- validating n-tier data applications
ms.assetid: 34ce4db6-09bb-4b46-b435-b2514aac52d3
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 94a8f4f8fe0d1f93ce3467291a20377234db29f4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58998103"
---
# <a name="add-validation-to-an-n-tier-dataset"></a>Agregar validación a un conjunto de datos de n niveles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Agregar validación a un conjunto de datos separado en una solución de n niveles es básicamente igual que agregar validación a un conjunto de datos de un solo archivo (un conjunto de datos en un único proyecto). La ubicación sugerida para realizar la validación en datos está durante <xref:System.Data.DataTable.ColumnChanging> y/o los eventos <xref:System.Data.DataTable.RowChanging> de una tabla de datos.  
  
El Diseñador de DataSet proporciona la funcionalidad para crear clases parciales a los que puede agregar código de usuario para la columna y fila eventos de las tablas de datos del conjunto de datos de cambio. Para obtener más información sobre cómo agregar código a un conjunto de datos en una solución de n niveles, vea [agregar código a conjuntos de datos en aplicaciones de n niveles](../data-tools/add-code-to-datasets-in-n-tier-applications.md), y [agregar código a TableAdapters en aplicaciones de n niveles](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md). Para obtener más información acerca de las clases parciales, vea [Cómo: Dividir una clase en clases parciales (Diseñador de clases)](../ide/how-to-split-a-class-into-partial-classes-class-designer.md) o [clases y métodos parciales](http://msdn.microsoft.com/library/804cecb7-62db-4f97-a99f-60975bd59fa1).  
  
> [!NOTE]
>  Al separar conjuntos de datos de los TableAdapters (estableciendo la **DataSet Project** propiedad), las clases de conjunto de datos parciales existentes en el proyecto no se moverá automáticamente. Las clases de conjunto de datos parciales existentes se deberán trasladar manualmente al proyecto de conjunto de datos.  
  
> [!NOTE]
>  El Diseñador de Dataset no crea automáticamente un controlador de eventos en C# para los eventos <xref:System.Data.DataTable.ColumnChanging> y <xref:System.Data.DataTable.RowChanging>. Tendrá que crear un controlador de eventos manualmente y enlazar el controlador de eventos al evento subyacente. Los procedimientos siguientes describen cómo crear los controladores de eventos necesaria en Visual Basic y C#.  
  
## <a name="validatechanges-to-individual-columns"></a>Validatechanges para columnas individuales  
 Valide los valores en columnas individual administrando el evento <xref:System.Data.DataTable.ColumnChanging>. El <xref:System.Data.DataTable.ColumnChanging> evento se desencadena cuando se modifica un valor en una columna. Crear un controlador de eventos para el <xref:System.Data.DataTable.ColumnChanging> eventos haciendo doble clic en la columna que desee en el conjunto de datos.  
  
 La primera vez que se hace doble clic en una columna, el diseñador genera un controlador de eventos para el evento <xref:System.Data.DataTable.ColumnChanging>. Un `If…Then` instrucción también se crea que comprueba la columna concreta. Por ejemplo, el código siguiente se genera cuando se hace doble clic en la columna RequiredDate de la tabla Orders de Northwind:  
  
```vb  
Private Sub OrdersDataTable_ColumnChanging(ByVal sender As System.Object, ByVal e As System.Data.DataColumnChangeEventArgs) Handles Me.ColumnChanging  
    If (e.Column.ColumnName = Me.RequiredDateColumn.ColumnName) Then  
        ' Add validation code here.  
    End If  
End Sub  
```  
  
> [!NOTE]
>  En proyectos C#, el Diseñador de DataSet crea únicamente las clases parciales para el conjunto de datos y las tablas individuales en el conjunto de datos. El Diseñador de DataSet no crea automáticamente los controladores de eventos para los eventos <xref:System.Data.DataTable.ColumnChanging> y <xref:System.Data.DataTable.RowChanging> en C#, como lo hace en Visual Basic. En los proyectos de C#, tendrá que construir manualmente un método para controlar el evento y enlazar el método para el evento subyacente. El procedimiento siguiente proporciona los pasos para crear los controladores de eventos necesarios tanto en Visual Basic como en C#.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-add-validation-during-changes-to-individual-column-values"></a>Para agregar la validación durante los cambios a los valores de columna individuales  
  
1.  Abra el conjunto de datos en el diseñador haciendo doble clic en el **.xsd** archivo **el Explorador de soluciones**. Para obtener más información, vea [Cómo: Abrir un conjunto de datos en el Diseñador de Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Haga doble clic en la columna que desee validar. Esta acción crea el controlador de eventos <xref:System.Data.DataTable.ColumnChanging>.  
  
    > [!NOTE]
    >  El Diseñador de DataSet no crea ningún controlador de eventos automáticamente para el evento de C#. El código que es necesario para controlar el evento en C# se incluye en la sección siguiente. `SampleColumnChangingEvent` se crea y, a continuación, vincula la <xref:System.Data.DataTable.ColumnChanging> eventos en el <xref:System.Data.DataTable.EndInit%2A> método.  
  
3.  Agregue el código para comprobar que `e.ProposedValue` contiene datos que son compatibles con los requisitos de la aplicación. Si el valor propuesto no es aceptable, establezca la columna para indicar que contiene un error.  
  
     El siguiente ejemplo de código que valida la **cantidad** columna contiene más de 0. Si **cantidad** es menor o igual a 0, la columna se establece en un error. El `Else` cláusula borra el error si **cantidad** es mayor que 0. El código del controlador de eventos de la columna que cambia debe presentar un aspecto similar al siguiente:  
  
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
    // C#  
    // Add this code to the DataTable   
    // partial class.  
  
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
  
## <a name="validatechanges-to-whole-rows"></a>Validatechanges para filas completas  
 Valide los valores en filas completas administrando el evento <xref:System.Data.DataTable.RowChanging>. Se produce el evento <xref:System.Data.DataTable.RowChanging> cuando se confirman los valores en todas las columnas. Esto es necesario para validar en el evento <xref:System.Data.DataTable.RowChanging> cuando el valor en una columna depende del valor en otra columna. Por ejemplo, tenga en cuenta OrderDate y RequiredDate en la tabla Orders en Northwind.  
  
 Cuando se incluyen los pedidos, la validación garantiza que un pedido no se escribe en la fecha requerida (RequiredDate) ni antes de la fecha de pedido (OrderDate). En este ejemplo, los valores para ambas columnas RequiredDate y OrderDate necesitan compararse, por ello no tiene sentido validar un cambio en una columna individual.  
  
 Crear un controlador de eventos para el <xref:System.Data.DataTable.RowChanging> eventos haciendo doble clic en el nombre de tabla en la barra de título de la tabla.  
  
#### <a name="to-add-validation-during-changes-to-whole-rows"></a>Para agregar la validación durante los cambios en las filas completas  
  
1.  Abra el conjunto de datos en el diseñador haciendo doble clic en el **.xsd** archivo **el Explorador de soluciones**. Para obtener más información, vea [Cómo: Abrir un conjunto de datos en el Diseñador de Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Haga doble clic en la barra de título de la tabla de datos en el diseñador.  
  
     Se crea una clase parcial con un controlador de eventos `RowChanging` y se abre en el Editor de código.  
  
    > [!NOTE]
    >  El Diseñador de DataSet no crea automáticamente un controlador para el evento <xref:System.Data.DataTable.RowChanging> en proyectos escritos en C#. Tendrá que crear un método para controlar la <xref:System.Data.DataTable.RowChanging> eventos y ejecutar código para enlazar el evento en el método de inicialización de la tabla.  
  
3.  Agregue el código de usuario dentro de la declaración de clase parcial.  
  
4.  El código siguiente muestra dónde agregar el código de usuario para validar durante el evento <xref:System.Data.DataTable.RowChanging> para Visual Basic:  
  
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
  
5.  El código siguiente muestra cómo crear el controlador de eventos `RowChanging` y dónde agregar el código de usuario para validar durante el evento <xref:System.Data.DataTable.RowChanging> para C#:  
  
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
 [Introducción a las aplicaciones de datos con N niveles](../data-tools/n-tier-data-applications-overview.md)   
 [Tutorial: Crear una aplicación de datos con N niveles](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
 [Validar los datos en conjuntos de datos](../data-tools/validate-data-in-datasets.md)
