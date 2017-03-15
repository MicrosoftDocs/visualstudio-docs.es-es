---
title: "C&#243;mo: Agregar validaci&#243;n a un conjunto de datos con n niveles | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "aplicaciones con n capas, validar"
  - "validar aplicaciones de datos con n niveles"
  - "validación [Visual Basic], aplicaciones de datos con n niveles"
ms.assetid: 34ce4db6-09bb-4b46-b435-b2514aac52d3
caps.latest.revision: 23
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Agregar validaci&#243;n a un conjunto de datos con n niveles
Agregar validación a un conjunto de datos separado en una solución de n niveles es básicamente igual que agregar validación a un conjunto de datos de un solo archivo \(un conjunto de datos en un único proyecto\).  La ubicación sugerida para realizar la validación en datos está durante <xref:System.Data.DataTable.ColumnChanging> y\/o los eventos <xref:System.Data.DataTable.RowChanging> de una tabla de datos.  
  
 [Crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md) proporciona la funcionalidad para crear clases parciales a las que puede agregar el código de usuario a los eventos que modifican la columna y la fila de las tablas de datos en el conjunto de datos.  Para obtener más información sobre cómo agregar código a un conjunto de datos en una solución de n niveles, vea [Cómo: Agregar código a conjuntos de datos en aplicaciones con n niveles](../data-tools/add-code-to-datasets-in-n-tier-applications.md) y [Cómo: Agregar código a TableAdapters en aplicaciones con n niveles](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md).  Para obtener más información acerca de las clases parciales, consulte [How to: Split a Class into Partial Classes \(Class Designer\)](../ide/how-to-split-a-class-into-partial-classes-class-designer.md) o [Clases y métodos parciales](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).  
  
> [!NOTE]
>  Cuando los conjuntos de datos se separan de los TableAdapters \(estableciendo la propiedad **DataSet Project**\), las clases de conjunto de datos parciales existentes no se trasladarán automáticamente.  Las clases de conjunto de datos parciales existentes se deberán trasladar manualmente al proyecto de conjunto de datos.  
  
> [!NOTE]
>  El Diseñador de Dataset no crea automáticamente un controlador de eventos en C\# para los eventos <xref:System.Data.DataTable.ColumnChanging> y <xref:System.Data.DataTable.RowChanging>.  Debe crear manualmente un controlador de eventos y enlazarlo hasta el evento subyacente.  Los procedimientos siguientes proporcionan los pasos para crear los controladores de eventos necesarios en Visual Basic y C\#.  
  
## Validar cambios para columnas individuales  
 Valide los valores en columnas individual administrando el evento <xref:System.Data.DataTable.ColumnChanging>.  El evento <xref:System.Data.DataTable.ColumnChanging> se produce cuando se modifica el valor de una columna.  Cree un controlador de eventos para el evento <xref:System.Data.DataTable.ColumnChanging> haciendo doble clic en la columna que desee en el [Crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md).  
  
 La primera vez que se hace doble clic en una columna, el diseñador genera un controlador de eventos para el evento <xref:System.Data.DataTable.ColumnChanging>.  Además del evento <xref:System.Data.DataTable.ColumnChanging>, también se crea una instrucción `If…Then` que realiza pruebas para la columna concreta.  Por ejemplo, se genera el código siguiente cuando se hace doble clic en la columna RequiredDate de la tabla Orders de Northwind:  
  
```vb#  
Private Sub OrdersDataTable_ColumnChanging(ByVal sender As System.Object, ByVal e As System.Data.DataColumnChangeEventArgs) Handles Me.ColumnChanging  
    If (e.Column.ColumnName = Me.RequiredDateColumn.ColumnName) Then  
        ' Add validation code here.  
    End If  
End Sub  
```  
  
> [!NOTE]
>  En proyectos C\#, el Diseñador de DataSet crea únicamente las clases parciales para el conjunto de datos y las tablas individuales en el conjunto de datos.  El Diseñador de DataSet no crea automáticamente los controladores de eventos para los eventos <xref:System.Data.DataTable.ColumnChanging> y <xref:System.Data.DataTable.RowChanging> en C\#, como lo hace en Visual Basic.  En proyectos C\#, tiene que construir manualmente un método para administrar el evento y enlazar el método hasta el evento subyacente.  El procedimiento siguiente proporciona los pasos para crear los controladores de eventos necesarios tanto en Visual Basic como en C\#.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### Para agregar la validación durante los cambios a los valores de columna individuales  
  
1.  Abra el conjunto de datos en el [Crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md) haciendo doble clic en el archivo **.xsd** en el Explorador de soluciones.  Para obtener más información, vea [Cómo: Abrir un objeto Dataset en el Diseñador de Dataset](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Haga doble clic en la columna que desee validar.  Esta acción crea el controlador de eventos <xref:System.Data.DataTable.ColumnChanging>.  
  
    > [!NOTE]
    >  El Diseñador de DataSet no crea ningún controlador de eventos automáticamente para el evento de C\#.  El código necesario para controlar el evento en C\# se incluye a continuación.  Se crea `SampleColumnChangingEvent` y, a continuación, se enlaza al evento <xref:System.Data.DataTable.ColumnChanging> en el método <xref:System.Data.DataTable.EndInit%2A>.  
  
3.  Agregue el código para comprobar que `e.ProposedValue` contiene datos que son compatibles con los requisitos de la aplicación.  Si el valor propuesto no es aceptable, establezca la columna para indicar que contiene un error.  
  
     En el siguiente ejemplo de código se valida que la columna Quantity contiene más de 0.  Si la Quantity es menor o igual que 0, la columna se establece en un error.  La cláusula `Else` borra el error si la cantidad es mayor que 0.  El código del controlador de eventos de la columna que cambia debe presentar un aspecto similar al siguiente:  
  
    ```vb#  
    If (e.Column.ColumnName = Me.QuantityColumn.ColumnName) Then  
        If CType(e.ProposedValue, Short) <= 0 Then  
            e.Row.SetColumnError(e.Column, "Quantity must be greater than 0")  
        Else  
            e.Row.SetColumnError(e.Column, "")  
        End If  
    End If  
    ```  
  
    ```c#  
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
  
## Validar cambios para filas completas  
 Valide los valores en filas completas administrando el evento <xref:System.Data.DataTable.RowChanging>.  Se produce el evento <xref:System.Data.DataTable.RowChanging> cuando se confirman los valores en todas las columnas.  Esto es necesario para validar en el evento <xref:System.Data.DataTable.RowChanging> cuando el valor en una columna depende del valor en otra columna.  Por ejemplo, tenga en cuenta OrderDate y RequiredDate en la tabla Orders en Northwind.  Cuando se incluyen los pedidos, la validación garantiza que un pedido no se escribe en la fecha requerida \(RequiredDate\) ni antes de la fecha de pedido \(OrderDate\).  En este ejemplo, los valores para ambas columnas RequiredDate y OrderDate necesitan compararse, por ello no tiene sentido validar un cambio en una columna individual.  
  
 Cree un controlador de eventos para el evento <xref:System.Data.DataTable.RowChanging> haciendo doble clic en el nombre de la tabla en la barra de título de la tabla del [Crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md).  
  
#### Para agregar la validación durante los cambios en las filas completas  
  
1.  Abra el conjunto de datos en el [Crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md) haciendo doble clic en el archivo **.xsd** en el Explorador de soluciones.  Para obtener más información, vea [Cómo: Abrir un objeto Dataset en el Diseñador de Dataset](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Haga doble clic en la barra de título de la tabla de datos en el diseñador.  
  
     Se crea una clase parcial con un controlador de eventos `RowChanging` y se abre en el Editor de código.  
  
    > [!NOTE]
    >  El Diseñador de DataSet no crea automáticamente un controlador para el evento <xref:System.Data.DataTable.RowChanging> en proyectos escritos en C\#.  Debe crear un método para controlar el evento <xref:System.Data.DataTable.RowChanging> y ejecutar el código para enlazar el evento en el método de inicialización de la tabla.  
  
3.  Agregue el código de usuario dentro de la declaración de clase parcial.  
  
4.  El código siguiente muestra dónde agregar el código de usuario para validar durante el evento <xref:System.Data.DataTable.RowChanging> para Visual Basic:  
  
    ```vb#  
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
  
5.  El código siguiente muestra cómo crear el controlador de eventos `RowChanging` y dónde agregar el código de usuario para validar durante el evento <xref:System.Data.DataTable.RowChanging> para C\#:  
  
    ```c#  
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
            // Perfom the validation logic.  
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
  
## Vea también  
 [Información general sobre aplicaciones de datos con n capas](../data-tools/n-tier-data-applications-overview.md)   
 [Tutorial: Crear una aplicación de datos con n niveles](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
 [Validar los datos en conjuntos de datos](../data-tools/validate-data-in-datasets.md)