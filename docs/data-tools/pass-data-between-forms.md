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
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: dc08b0667d4bcde4a2b0eaf95f966806b4a8931e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62566285"
---
# <a name="pass-data-between-forms"></a>Pasar datos de un formulario a otro

En este tutorial se proporcionan instrucciones paso a paso para pasar datos de un formulario a otro. Con las tablas customers y orders de Northwind, un formulario permite a los usuarios seleccionar a un cliente y un segundo formulario muestra los pedidos del cliente seleccionado. Este tutorial muestra cómo crear un método en el segundo formulario que recibe los datos del primer formulario.

> [!NOTE]
> En este tutorial solo se muestra una manera de pasar datos de un formulario a otro. Hay otras opciones para pasar datos a un formulario, incluida la creación de un segundo constructor para recibir datos, o crear una propiedad pública que se puede establecer con los datos desde el primer formulario.

Las tareas ilustradas en este tutorial incluyen:

- Crear un proyecto nuevo de **aplicación de Windows Forms**.

- Crear y configurar un conjunto de datos con el [Asistente para configuración de origen de datos](../data-tools/media/data-source-configuration-wizard.png).

- Seleccionar el control que se va a crear en el formulario al arrastrar elementos desde la ventana **Orígenes de datos**. Para obtener más información, consulte [establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

- Crear un control enlazado a datos arrastrando elementos desde la ventana **Orígenes de datos** hasta un formulario.

- Crear un segundo formulario con una cuadrícula para mostrar datos.

- Crear una consulta de TableAdapter para buscar los pedidos de un cliente determinado.

- Pasar datos de un formulario a otro.

## <a name="prerequisites"></a>Requisitos previos

En este tutorial usa SQL Server Express LocalDB y la base de datos de ejemplo Northwind.

1. Si no tiene SQL Server Express LocalDB, instálelo de desde el [página de descarga de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), o a través del **instalador de Visual Studio**. En el instalador de Visual Studio, se puede instalar SQL Server Express LocalDB como parte de la **procesamiento y almacenamiento de datos** carga de trabajo, o como un componente individual.

2. Instalar la base de datos de ejemplo Northwind, siga estos pasos:

    1. En Visual Studio, abra el **Explorador de objetos de SQL Server** ventana. (Explorador de objetos de SQL Server se instala como parte de la **procesamiento y almacenamiento de datos** carga de trabajo en el instalador de Visual Studio.) Expanda el **SQL Server** nodo. Haga doble clic en la instancia de LocalDB y seleccione **nueva consulta**.

       Se abre una ventana del editor de consultas.

    2. Copia el [script Transact-SQL de Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) en el Portapapeles. Este script de Transact-SQL crea la base de datos Northwind desde el principio y lo rellena con datos.

    3. Pegue el script de Transact-SQL en el editor de consultas y, a continuación, elija el **Execute** botón.

       Después de un breve tiempo, finalice la consulta y se crea la base de datos Northwind.

## <a name="create-the-windows-forms-app-project"></a>Crear el proyecto de aplicación de Windows Forms

1. En Visual Studio, en el **archivo** menú, seleccione **New** > **proyecto**.

2. Expanda el **Visual C#** o **Visual Basic** en el panel izquierdo, seleccione **Windows Desktop**.

3. En el panel central, seleccione la **aplicación de Windows Forms** tipo de proyecto.

4. Denomine el proyecto **PassingDataBetweenForms**y, a continuación, elija **Aceptar**.

     El proyecto **PassingDataBetweenForms** se crea y se agrega al **Explorador de soluciones**.

## <a name="create-the-data-source"></a>Crear el origen de datos

1. Para abrir el **orígenes de datos** ventana, en el **datos** menú, haga clic en **Mostrar orígenes de datos**.

2. En la ventana **Orígenes de datos**, seleccione **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de orígenes de datos**.

3. Seleccione **Base de datos** en la página **Elegir un tipo de datos de origen** y luego haga clic en **Siguiente**.

4. En la página **Elegir un modelo de base de datos**, compruebe que se ha especificado **Conjunto de datos** y haga clic en **Siguiente**.

5. En la página **Elegir la conexión de datos** realice una de las siguientes operaciones:

    - Si una conexión de datos a la base de datos de ejemplo Northwind está disponible en la lista desplegable, selecciónela.

    - Seleccione **Nueva conexión** para iniciar el cuadro de diálogo **Agregar o modificar conexión**.

6. Si su base de datos requiere una contraseña y la opción para incluir datos confidenciales está habilitada, seleccione la opción y haga clic en **Siguiente**.

7. Haga clic en **Siguiente** en la página **Guardar la cadena de conexión en el archivo de configuración de la aplicación**.

8. Expanda el nodo **Tablas** en la página **Elija los objetos de base de datos**.

9. Seleccione las tablas **Customers** y **Orders** y después haga clic en **Finalizar**.

     **NorthwindDataSet** se agrega al proyecto y las tablas **Customers** y **Orders** aparecen en la ventana **Orígenes de datos**.

## <a name="create-the-first-form-form1"></a>Crear el primer formulario (Form1)

Puede crear una cuadrícula enlazada a datos (un control <xref:System.Windows.Forms.DataGridView>) arrastrando el nodo **Customers** desde la ventana **Orígenes de datos** al formulario.

### <a name="to-create-a-data-bound-grid-on-the-form"></a>Para crear una cuadrícula enlazada a datos en el formulario

- Arrastre el nodo principal **Customers** desde la ventana **Orígenes de datos** hasta **Form1**.

     Un <xref:System.Windows.Forms.DataGridView> y una barra de herramientas (<xref:System.Windows.Forms.BindingNavigator>) para navegar por los registros aparecen en **Form1**. En la bandeja de componentes aparecen [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> y <xref:System.Windows.Forms.BindingNavigator>.

## <a name="create-the-second-form"></a>Crear el segundo formulario

Crear un segundo formulario para pasar los datos.

1. En el menú **Proyecto**, elija **Agregar Windows Forms**.

2. Deje el nombre predeterminado **Form2** y haga clic en **Agregar**.

3. Arrastre el nodo **Orders** principal desde la ventana **Orígenes de datos** a **Form2**.

     Un <xref:System.Windows.Forms.DataGridView> y una barra de herramientas (<xref:System.Windows.Forms.BindingNavigator>) para navegar por los registros aparecen en **Form2**. En la bandeja de componentes aparecen [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> y <xref:System.Windows.Forms.BindingNavigator>.

4. Elimine **OrdersBindingNavigator** de la bandeja de componentes.

     **OrdersBindingNavigator** desaparece del **Form2**.

## <a name="add-a-tableadapter-query"></a>Agregar una consulta de TableAdapter

Agregar una consulta de TableAdapter al Form2 para cargar los pedidos del cliente seleccionado en Form1.

1. Haga doble clic en el archivo **NorthwindDataSet.xsd**, en el **Explorador de soluciones**.

2. Haga clic con el botón derecho en **OrdersTableAdapter** y seleccione **Agregar consulta**.

3. Deje la opción predeterminada **Usar instrucciones SQL** y haga clic en **Siguiente**.

4. Deje la opción predeterminada **SELECT que devuelve filas** y haga clic en **Siguiente**.

5. Agregue una cláusula WHERE a la consulta para que devuelva `Orders` en función del `CustomerID`. La consulta debe ser similar a lo siguiente:

    ```sql
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry
    FROM Orders
    WHERE CustomerID = @CustomerID
    ```

    > [!NOTE]
    > Compruebe que la sintaxis de los parámetros sea correcta para su base de datos. Por ejemplo, en Microsoft Access, la cláusula WHERE tendría el siguiente aspecto: `WHERE CustomerID = ?`.

6. Haga clic en **Siguiente**.

7. Para el **rellene un nombre DataTableMethod**, tipo `FillByCustomerID`.

8. Desactive la opción **Devolver un DataTable** y haga clic en **Siguiente**.

9. Haga clic en **Finalizar**.

## <a name="create-a-method-on-form2-to-pass-data-to"></a>Cree un método en Form2 para pasar datos a

1. Haga clic con el botón derecho en **Form2** y seleccione **Ver código** para abrir **Form2** en el **Editor de código**.

2. Agregue el código siguiente a **Form2** después del método `Form2_Load`:

     [!code-vb[VbRaddataDisplaying#1](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_1.vb)]
     [!code-csharp[VbRaddataDisplaying#1](../data-tools/codesnippet/CSharp/pass-data-between-forms_1.cs)]

## <a name="create-a-method-on-form1-to-pass-data-and-display-form2"></a>Cree un método en Form1 para pasar datos y mostrar Form2

1. En **Form1**, haga clic con el botón derecho en la cuadrícula de datos Customer y después haga clic en **Propiedades**.

2. En la ventana **Propiedades**, haga clic en **Eventos**.

3. Haga doble clic en el evento **CellDoubleClick**.

     Aparece el editor de código.

4. Actualice la definición del método para que coincida con el ejemplo siguiente:

     [!code-csharp[VbRaddataDisplaying#2](../data-tools/codesnippet/CSharp/pass-data-between-forms_2.cs)]
     [!code-vb[VbRaddataDisplaying#2](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_2.vb)]

## <a name="run-the-app"></a>Ejecutar la aplicación

- Presione **F5** para ejecutar la aplicación.

- Haga doble clic en un registro de cliente en **Form1** para abrir **Form2** con los pedidos del cliente.

## <a name="next-steps"></a>Pasos siguientes

Dependiendo de los requisitos de la aplicación, existen varios pasos que se pueden realizar después de pasar los datos de un formulario a otro. Entre las mejoras que podría realizar se incluyen:

- Modificar el conjunto de datos agregando o quitando objetos de la base de datos. Para obtener más información, vea [Crear y configurar conjuntos de datos](../data-tools/create-and-configure-datasets-in-visual-studio.md).

- Agregar funcionalidad para guardar los datos de nuevo en la base de datos. Para obtener más información, consulte [guardar los datos en la base de datos](../data-tools/save-data-back-to-the-database.md).

## <a name="see-also"></a>Vea también

- [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)