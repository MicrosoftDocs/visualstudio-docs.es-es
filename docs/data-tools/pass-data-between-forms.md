---
title: Pasar datos de un formulario a otro
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- walkthroughs [Windows Forms], data
- walkthroughs [Visual Studio], data
- data [Visual Studio], passing between forms
- forms, passing data between
- Windows Forms, walkthroughs
ms.assetid: 78bf038b-9296-4fbf-b0e8-d881d1aff0df
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c8d400f8fa46fa10876d1827205671b6d90a3e33
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089443"
---
# <a name="pass-data-between-forms"></a>Pasar datos de un formulario a otro
En este tutorial se proporcionan instrucciones paso a paso para pasar datos de un formulario a otro. Con las tablas customers y orders de Northwind, un formulario permite a los usuarios seleccionar a un cliente y un segundo formulario muestra los pedidos del cliente seleccionado. Este tutorial muestra cómo crear un método en el segundo formulario que recibe los datos del primer formulario.

> [!NOTE]
>  En este tutorial solo se muestra una manera de pasar datos de un formulario a otro. Hay otras opciones para pasar datos a un formulario, incluida la creación de un segundo constructor para recibir datos, o crear una propiedad pública que se puede establecer con los datos desde el primer formulario.

 Las tareas ilustradas en este tutorial incluyen:

-   Crear un nuevo **aplicación de Windows Forms** proyecto.

-   Crear y configurar un conjunto de datos con el [Asistente para configuración de origen de datos](../data-tools/media/data-source-configuration-wizard.png).

-   Selecciona el control que se creará en el formulario al arrastrar elementos desde el **orígenes de datos** ventana. Para obtener más información, consulte [establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

-   Creación de un control enlazado a datos arrastrando elementos desde la **orígenes de datos** ventana en un formulario.

-   Crear un segundo formulario con una cuadrícula para mostrar datos.

-   Crear una consulta de TableAdapter para buscar los pedidos de un cliente determinado.

-   Pasar datos de un formulario a otro.

## <a name="prerequisites"></a>Requisitos previos
En este tutorial usa SQL Server Express LocalDB y la base de datos de ejemplo Northwind.

1.  Si no tiene SQL Server Express LocalDB, instálelo de desde el [página de descarga de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), o a través del **instalador de Visual Studio**. En el instalador de Visual Studio, se puede instalar SQL Server Express LocalDB como parte de la **procesamiento y almacenamiento de datos** carga de trabajo, o como un componente individual.

2.  Instalar la base de datos de ejemplo Northwind, siga estos pasos:

    1. En Visual Studio, abra el **Explorador de objetos de SQL Server** ventana. (Explorador de objetos de SQL Server se instala como parte de la **procesamiento y almacenamiento de datos** carga de trabajo en el instalador de Visual Studio.) Expanda el **SQL Server** nodo. Haga doble clic en la instancia de LocalDB y seleccione **nueva consulta**.

       Se abre una ventana del editor de consultas.

    2. Copia el [script Transact-SQL de Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) en el Portapapeles. Este script de Transact-SQL crea la base de datos Northwind desde el principio y lo rellena con datos.

    3. Pegue el script de Transact-SQL en el editor de consultas y, a continuación, elija el **Execute** botón.

       Después de un breve tiempo, finalice la consulta y se crea la base de datos Northwind.

## <a name="create-the-windows-forms-application"></a>Crear la aplicación de Windows Forms

### <a name="to-create-the-new-windows-project"></a>Para crear el nuevo proyecto de Windows

1. En Visual Studio, en el **archivo** menú, seleccione **New** > **proyecto**.

2. Expanda el **Visual C#** o **Visual Basic** en el panel izquierdo, seleccione **Windows Desktop**.

3. En el panel central, seleccione la **aplicación de Windows Forms** tipo de proyecto.

4. Denomine el proyecto **PassingDataBetweenForms**y, a continuación, elija **Aceptar**.

     El **PassingDataBetweenForms** se crea y agrega al proyecto **el Explorador de soluciones**.

## <a name="create-the-data-source"></a>Crear el origen de datos

### <a name="to-create-the-data-source"></a>Para crear el origen de datos

1.  En el menú **Datos** , haga clic en **Mostrar orígenes de datos**.

2.  En el **orígenes de datos** ventana, seleccione **Agregar nuevo origen de datos** para iniciar el **configuración origen de datos** asistente.

3.  Seleccione **Base de datos** en la página **Elegir un tipo de datos de origen** y luego haga clic en **Siguiente**.

4.  En el **elegir un modelo de base de datos** , comprueba que **Dataset** se especifica y, a continuación, haga clic en **siguiente**.

5.  En el **elegir la conexión de datos** , realice una de las siguientes acciones:

    -   Si una conexión de datos a la base de datos de ejemplo Northwind está disponible en la lista desplegable, selecciónela.

    -   Seleccione **nueva conexión** para iniciar el **agregar o modificar conexión** cuadro de diálogo.

6.  Si la base de datos requiere una contraseña y si está habilitada la opción para incluir datos confidenciales, seleccione la opción y, a continuación, haga clic en **siguiente**.

7.  En el **Guardar cadena de conexión en el archivo de configuración de la aplicación** página, haga clic en **siguiente**.

8.  En el **elija los objetos de base de datos** , expanda el **tablas** nodo.

9. Seleccione el **clientes** y **pedidos** tablas y, a continuación, haga clic en **finalizar**.

     El **NorthwindDataSet** se agrega al proyecto y el **clientes** y **pedidos** tablas aparecen en la **orígenes de datos** ventana.

## <a name="create-the-first-form-form1"></a>Crear el primer formulario (Form1)
 Puede crear una cuadrícula enlazada a datos (un <xref:System.Windows.Forms.DataGridView> control), arrastrando el **clientes** nodo desde el **orígenes de datos** ventana hasta el formulario.

### <a name="to-create-a-data-bound-grid-on-the-form"></a>Para crear una cuadrícula enlazada a datos en el formulario

-   Arrastre el método main **clientes** nodo desde el **orígenes de datos** ventana hasta **Form1**.

     Un <xref:System.Windows.Forms.DataGridView> y una barra de herramientas (<xref:System.Windows.Forms.BindingNavigator>) para navegar por los registros aparecen en **Form1**. Un [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource>, y <xref:System.Windows.Forms.BindingNavigator> aparecen en la Bandeja de componentes.

## <a name="create-the-second-form-form2"></a>Crear el segundo formulario (Form2)

### <a name="to-create-a-second-form-to-pass-the-data-to"></a>Para crear un segundo formulario al que pasar los datos

1.  En el menú **Proyecto**, elija **Agregar Windows Forms**.

2.  Deje el nombre predeterminado de **Form2**y haga clic en **agregar**.

3.  Arrastre el método main **pedidos** nodo desde el **orígenes de datos** ventana hasta **Form2**.

     Un <xref:System.Windows.Forms.DataGridView> y una barra de herramientas (<xref:System.Windows.Forms.BindingNavigator>) para navegar por los registros aparecen en **Form2**. Un [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource>, y <xref:System.Windows.Forms.BindingNavigator> aparecen en la Bandeja de componentes.

4.  Eliminar el **OrdersBindingNavigator** desde la Bandeja de componentes.

     El **OrdersBindingNavigator** desaparece del **Form2**.

## <a name="add-a-tableadapter-query-to-form2-to-load-orders-for-the-selected-customer-on-form1"></a>Agregar una consulta de TableAdapter al Form2 para cargar los pedidos del cliente seleccionado en Form1

### <a name="to-create-a-tableadapter-query"></a>Para crear una consulta de TableAdapter

1.  Haga doble clic en el **NorthwindDataSet.xsd** archivo **el Explorador de soluciones**.

2.  Haga clic en el **OrdersTableAdapter**y seleccione **Agregar consulta**.

3.  Deje la opción predeterminada de **usar instrucciones SQL**y, a continuación, haga clic en **siguiente**.

4.  Deje la opción predeterminada de **LECT que devuelve filas**y, a continuación, haga clic en **siguiente**.

5.  Agregue una cláusula WHERE para que devuelva la consulta `Orders` según el `CustomerID`. La consulta debe ser similar a lo siguiente:

    ```sql
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry
    FROM Orders
    WHERE CustomerID = @CustomerID
    ```

    > [!NOTE]
    >  Compruebe que la sintaxis de los parámetros sea correcta para su base de datos. Por ejemplo, en Microsoft Access, la cláusula WHERE tendría el aspecto, como: `WHERE CustomerID = ?`.

6.  Haga clic en **Siguiente**.

7.  Para el **rellene un nombre DataTableMethod**, tipo `FillByCustomerID`.

8.  Desactive el **devolver un DataTable** opción y, a continuación, haga clic en **siguiente**.

9. Haga clic en **Finalizar**.

## <a name="create-a-method-on-form2-to-pass-data-to"></a>Cree un método en Form2 para pasar datos a

### <a name="to-create-a-method-to-pass-data-to"></a>Para crear un método al que pasar datos

1.  Haga clic en **Form2**y seleccione **ver código** para abrir **Form2** en el **Editor de código**.

2.  Agregue el código siguiente al **Form2** después de que el `Form2_Load` método:

     [!code-vb[VbRaddataDisplaying#1](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_1.vb)]
     [!code-csharp[VbRaddataDisplaying#1](../data-tools/codesnippet/CSharp/pass-data-between-forms_1.cs)]

## <a name="create-a-method-on-form1-to-pass-data-and-display-form2"></a>Cree un método en Form1 para pasar datos y mostrar Form2

### <a name="to-create-a-method-to-pass-data-to-form2"></a>Para crear un método para pasar datos a Form2

1.  En **Form1**, haga clic en la cuadrícula de datos de cliente y, a continuación, haga clic en **propiedades**.

2.  En el **propiedades** ventana, haga clic en **eventos**.

3.  Haga doble clic en el **CellDoubleClick** eventos.

     Aparece el editor de código.

4.  Actualice la definición del método para que coincida con el ejemplo siguiente:

     [!code-csharp[VbRaddataDisplaying#2](../data-tools/codesnippet/CSharp/pass-data-between-forms_2.cs)]
     [!code-vb[VbRaddataDisplaying#2](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_2.vb)]

## <a name="run-the-application"></a>Ejecutar la aplicación

### <a name="to-run-the-application"></a>Para ejecutar la aplicación

-   Presione **F5** para ejecutar la aplicación.

-   Haga doble clic en un registro de cliente en **Form1** para abrir **Form2** con los pedidos del cliente.

## <a name="next-steps"></a>Pasos siguientes

Dependiendo de los requisitos de la aplicación, existen varios pasos que se pueden realizar después de pasar los datos de un formulario a otro. Entre las mejoras que podría realizar se incluyen:

-   Modificar el conjunto de datos agregando o quitando objetos de la base de datos. Para obtener más información, vea [Crear y configurar conjuntos de datos](../data-tools/create-and-configure-datasets-in-visual-studio.md).

-   Agregar funcionalidad para guardar los datos de nuevo en la base de datos. Para obtener más información, consulte [guardar los datos en la base de datos](../data-tools/save-data-back-to-the-database.md).

## <a name="see-also"></a>Vea también

- [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)