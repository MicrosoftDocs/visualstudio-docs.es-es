---
title: Aplicación de datos sencilla con WPF y Entity Framework 6
ms.date: 08/22/2017
ms.topic: conceptual
dev_langs:
- CSharp
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 6a8fd65c9f7c498f06b0776f0cd61ebc5ce48182
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72642922"
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>Crear una aplicación de datos sencilla con WPF y Entity Framework 6

En este tutorial se muestra cómo crear una aplicación básica de "formularios sobre datos" en Visual Studio. La aplicación usa SQL Server LocalDB, la base de datos Northwind, Entity Framework 6 y Windows Presentation Foundation. Muestra cómo realizar el enlace de datos básico con una vista de maestro y detalles, y también tiene un navegador de enlace personalizado con botones para **ir siguiente**, **moverse anterior**, **moverse al principio**, **moverse al final**, **Actualizar** y **eliminar**.

Este artículo se centra en el uso de herramientas de datos en Visual Studio y no intenta explicar las tecnologías subyacentes en cualquier profundidad. Se supone que tiene conocimientos básicos de XAML, Entity Framework y SQL. En este ejemplo tampoco se muestra la arquitectura Model-View-ViewModel (MVVM), que es estándar para las aplicaciones de WPF. Sin embargo, puede copiar este código en su propia aplicación MVVM con pocas modificaciones.

## <a name="install-and-connect-to-northwind"></a>Instalar y conectarse a Northwind

En este ejemplo se usa SQL Server Express LocalDB y la base de datos de ejemplo Northwind. Si el proveedor de datos ADO.NET para ese producto es compatible con Entity Framework, debería funcionar también con otros productos de SQL Database.

1. Si no tiene SQL Server Express LocalDB, instálelo desde la [Página de descarga de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)o a través de la **instalador de Visual Studio**. En el **instalador de Visual Studio**, puede instalar SQL Server Express LocalDB como parte de la carga de trabajo de **desarrollo de escritorio de .net** o como un componente individual.

2. Instale la base de datos de ejemplo Northwind siguiendo estos pasos:

    1. En Visual Studio, abra la ventana **Explorador de objetos de SQL Server** . (**Explorador de objetos de SQL Server** se instala como parte de la carga de trabajo de **procesamiento y almacenamiento de datos** en el **instalador de Visual Studio**). Expanda el nodo **SQL Server** . Haga clic con el botón secundario en la instancia de LocalDB y seleccione **nueva consulta**.

       Se abre una ventana del editor de consultas.

    2. Copie el [script de Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) en el portapapeles. Este script T-SQL crea la base de datos Northwind desde cero y la rellena con datos.

    3. Pegue el script T-SQL en el editor de consultas y, a continuación, elija el botón **Ejecutar** .

       Tras un breve período de tiempo, la consulta termina de ejecutarse y se crea la base de datos Northwind.

3. [Agregue nuevas conexiones](../data-tools/add-new-connections.md) para Northwind.

## <a name="configure-the-project"></a>Configuración del proyecto

1. En Visual Studio, cree un nuevo C# proyecto de **aplicación de WPF** .

2. Agregue el paquete de NuGet para Entity Framework 6. En **Explorador de soluciones**, seleccione el nodo del proyecto. En el menú principal, elija **proyecto**  > **administrar paquetes NuGet**.

     ![Elemento de menú administrar paquetes NuGet](../data-tools/media/raddata_vs2015_manage_nuget_packages.png)

3. En el **Administrador de paquetes NuGet**, haga clic en el vínculo **examinar** . Entity Framework es probablemente el paquete superior de la lista. Haga clic en **instalar** en el panel derecho y siga las indicaciones. La ventana salida le indica cuándo ha finalizado la instalación.

     ![Entity Framework paquete NuGet](../data-tools/media/raddata_vs2015_nuget_ef.png)

4. Ahora puede usar Visual Studio para crear un modelo basado en la base de datos Northwind.

## <a name="create-the-model"></a>Creación del modelo

1. Haga clic con el botón derecho en el nodo del proyecto en **Explorador de soluciones** y elija **Agregar**  > **nuevo elemento**. En el panel izquierdo, en el C# nodo, elija **datos** y, en el panel central, elija **ADO.NET Entity Data Model**.

   ![Modelo de Entity Framework nuevo elemento](../data-tools/media/raddata-ef-new-project-item.png)

2. Llame al `Northwind_model` del modelo y elija **Aceptar**. Se abre el **Asistente para Entity Data Model**. Elija **EF Designer en la base de datos** y, a continuación, haga clic en **siguiente**.

   ![Modelo EF de la base de datos](../data-tools/media/raddata-ef-model-from-database.png)

3. En la siguiente pantalla, elija la conexión de LocalDB Northwind y haga clic en **siguiente**.

4. En la página siguiente del asistente, elija qué tablas, procedimientos almacenados y otros objetos de base de datos se van a incluir en el modelo de Entity Framework. Expanda el nodo DBO en la vista de árbol y elija **clientes**, **pedidos**y **detalles de pedido**. Deje la opción valores predeterminados activada y haga clic en **Finalizar**.

    ![Elegir objetos de base de datos para el modelo](../data-tools/media/raddata-choose-ef-objects.png)

5. El asistente genera las C# clases que representan el modelo de Entity Framework. Las clases son clases antiguas C# sin formato y son lo que se enlaza a la interfaz de usuario de WPF. El archivo *. edmx* describe las relaciones y otros metadatos que asocian las clases con los objetos de la base de datos. Los archivos *. TT* son plantillas T4 que generan el código que funciona en el modelo y guardan los cambios en la base de datos. Puede ver todos estos archivos en **Explorador de soluciones** en el nodo Northwind_model:

      ![Archivos de modelo de Explorador de soluciones EF](../data-tools/media/raddata-solution-explorer-ef-model-files.png)

    La superficie del diseñador del archivo *. edmx* le permite modificar algunas propiedades y relaciones en el modelo. No vamos a usar el diseñador en este tutorial.

6. Los archivos *. TT* son de uso general y es necesario retocar uno de ellos para que funcionen con el enlace de los DATABINDINGS de WPF, lo que requiere ObservableCollections. En **Explorador de soluciones**, expanda el nodo Northwind_model hasta que encuentre *Northwind_model. TT*. (Asegúrese de que no está en el *. Archivo Context.tt* , que se encuentra justo debajo del archivo *. edmx* ).

   - Reemplace las dos apariciones de <xref:System.Collections.ICollection> por <xref:System.Collections.ObjectModel.ObservableCollection%601>.

   - Reemplace la primera aparición de <xref:System.Collections.Generic.HashSet%601> por <xref:System.Collections.ObjectModel.ObservableCollection%601> en torno a la línea 51. No reemplace la segunda aparición de HashSet.

   - Reemplace la única aparición de <xref:System.Collections.Generic> (en torno a la línea 431) con <xref:System.Collections.ObjectModel>.

7. Presione **Ctrl** +**MAYÚS** +**B** para compilar el proyecto. Cuando finaliza la compilación, las clases del modelo son visibles para el Asistente para orígenes de datos.

Ahora ya puede enlazar este modelo a la página XAML para que pueda ver, navegar y modificar los datos.

## <a name="databind-the-model-to-the-xaml-page"></a>Enlazar el modelo a la página XAML

Es posible escribir su propio código de enlace de la propiedad, pero es mucho más fácil dejar que Visual Studio lo haga automáticamente.

1. En el menú principal, elija **proyecto**  > **Agregar nuevo origen de datos** para abrir el **Asistente para configuración de orígenes de datos**. Elija **objeto** porque está enlazando a las clases del modelo, no a la base de datos:

     ![Asistente para configuración de orígenes de datos con origen de objeto](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png)

2. Seleccione **Customer**. (Los orígenes de pedidos se generan automáticamente a partir de la propiedad de navegación Orders en Customer).

     ![Agregar clases de entidad como orígenes de datos](../data-tools/media/raddata-add-entity-classes-as-data-sources.png)

3. Haga clic en **Finalizar**.

4. Vaya a *MainWindow. Xaml* en la vista Código. Estamos manteniendo el XAML sencillo para los fines de este ejemplo. Cambie el título de MainWindow a algo más descriptivo y aumente el alto y el ancho a 600 x 800 por ahora. Siempre puede cambiarlo más adelante. Ahora, agregue estas tres definiciones de fila a la cuadrícula principal, una fila para los botones de navegación, una para los detalles del cliente y otra para la cuadrícula que muestra los pedidos:

    ```xaml
    <Grid.RowDefinitions>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="*"/>
        </Grid.RowDefinitions>
    ```

5. Ahora Abra *MainWindow. Xaml* para que lo esté viendo en el diseñador. Esto hace que la ventana **orígenes de datos** aparezca como una opción en el margen de la ventana de Visual Studio junto al **cuadro de herramientas**. Haga clic en la pestaña para abrir la ventana, o bien presione **mayús** +**Alt** +**D** o elija **Ver**  > **otras ventanas**  > **orígenes de datos**. Vamos a mostrar cada propiedad en la clase customers en su propio cuadro de texto individual. En primer lugar, haga clic en la flecha en el cuadro combinado **clientes** y elija **detalles**. A continuación, arrastre el nodo hasta la parte central de la superficie de diseño para que el diseñador sepa que desea que aparezca en la fila central. Si la coloca mal, puede especificar la fila manualmente más adelante en el código XAML. De forma predeterminada, los controles se colocan verticalmente en un elemento de cuadrícula, pero en este momento puede organizarlos como desee en el formulario. Por ejemplo, puede que tenga sentido poner el cuadro de texto **nombre** en la parte superior, encima de la dirección. En la aplicación de ejemplo de este artículo se reordenan los campos y se reorganizan en dos columnas.

     ![Enlace de origen de datos de los clientes a controles individuales](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png)

     En la vista de código, ahora puede ver un nuevo elemento `Grid` en la fila 1 (la fila central) de la cuadrícula primaria. La cuadrícula primaria tiene un atributo `DataContext` que hace referencia a un CollectionViewSource que se ha agregado al elemento `Windows.Resources`. Dado ese contexto de datos, cuando el primer cuadro de texto se enlaza a la **Dirección**, ese nombre se asigna a la propiedad `Address` en el objeto de `Customer` actual en CollectionViewSource.

    ```xaml
    <Grid DataContext="{StaticResource customerViewSource}">
    ```

6. Cuando un cliente está visible en la mitad superior de la ventana, desea ver sus pedidos en la mitad inferior. Los pedidos se muestran en un solo control de vista de cuadrícula. Para que el enlace de los enlaces de los detalles maestros funcione según lo previsto, es importante enlazar a la propiedad Orders de la clase customers, no al nodo Orders independiente. Arrastre la propiedad Orders de la clase customers a la mitad inferior del formulario para que el diseñador la coloque en la fila 2:

     ![Arrastrar clases de pedidos como cuadrícula](../data-tools/media/raddata-drag-orders-classes-as-grid.png)

7. Visual Studio ha generado todo el código de enlace que conecta los controles de interfaz de usuario a los eventos del modelo. Todo lo que necesita hacer para ver algunos datos es escribir código para rellenar el modelo. En primer lugar, vaya a *MainWindow.Xaml.CS* y agregue un miembro de datos a la clase MainWindow para el contexto de datos. Este objeto, que se ha generado automáticamente, actúa como un control que realiza un seguimiento de los cambios y eventos del modelo. También agregará la lógica de inicialización del constructor. La parte superior de la clase debe ser similar a la siguiente:

     [!code-csharp[MainWindow#1](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#1)]

     Agregue una directiva de `using` para System. Data. Entity para poner el método de extensión de carga en el ámbito:

     ```csharp
     using System.Data.Entity;
     ```

     Ahora, desplácese hacia abajo y busque el controlador de eventos `Window_Loaded`. Tenga en cuenta que Visual Studio ha agregado un objeto CollectionViewSource. Esto representa el objeto NorthwindEntities que seleccionó al crear el modelo. Vamos a agregar código a `Window_Loaded` de modo que todo el método tenga ahora el siguiente aspecto:

     [!code-csharp[Window_Loaded#2](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#2)]

8. Presione **F5**. Debería ver los detalles del primer cliente que se recuperó en CollectionViewSource. También debería ver sus pedidos en la cuadrícula de datos. El formato no es excelente, así que vamos a solucionarlo. También puede crear una manera de ver los demás registros y realizar las operaciones CRUD básicas.

## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>Ajustar el diseño de la página y agregar cuadrículas para nuevos clientes y pedidos

La disposición predeterminada generada por Visual Studio no es idónea para su aplicación, por lo que realizará algunos cambios manualmente en el código XAML. También necesitará algunos "formularios" (que son en realidad cuadrículas) para que el usuario pueda agregar un nuevo cliente o pedido. Para poder agregar un nuevo cliente y un pedido, necesita un conjunto independiente de cuadros de texto que no están enlazados a datos con el `CollectionViewSource`. Puede controlar qué cuadrícula Ve el usuario en un momento dado estableciendo la propiedad visible en los métodos de controlador. Por último, agregue un botón eliminar a cada fila de la cuadrícula pedidos para permitir que el usuario elimine un pedido individual.

En primer lugar, agregue estos estilos al elemento `Windows.Resources` en *MainWindow. Xaml*:

```xaml
<Style x:Key="Label" TargetType="{x:Type Label}" BasedOn="{x:Null}">
    <Setter Property="HorizontalAlignment" Value="Left"/>
    <Setter Property="VerticalAlignment" Value="Center"/>
    <Setter Property="Margin" Value="3"/>
    <Setter Property="Height" Value="23"/>
</Style>
<Style x:Key="CustTextBox" TargetType="{x:Type TextBox}" BasedOn="{x:Null}">
    <Setter Property="HorizontalAlignment" Value="Right"/>
    <Setter Property="VerticalAlignment" Value="Center"/>
    <Setter Property="Margin" Value="3"/>
    <Setter Property="Height" Value="26"/>
    <Setter Property="Width" Value="120"/>
</Style>
```

A continuación, reemplace toda la cuadrícula externa por este marcado:

```xaml
<Grid>
     <Grid.RowDefinitions>
         <RowDefinition Height="auto"/>
         <RowDefinition Height="auto"/>
         <RowDefinition Height="*"/>
     </Grid.RowDefinitions>
     <Grid x:Name="existingCustomerGrid" Grid.Row="1" HorizontalAlignment="Left" Margin="5" Visibility="Visible" VerticalAlignment="Top" Background="AntiqueWhite" DataContext="{StaticResource customerViewSource}">
         <Grid.ColumnDefinitions>
             <ColumnDefinition Width="Auto" MinWidth="233"/>
             <ColumnDefinition Width="Auto" MinWidth="397"/>
         </Grid.ColumnDefinitions>
         <Grid.RowDefinitions>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
         </Grid.RowDefinitions>
         <Label Content="Customer ID:" Grid.Row="0" Style="{StaticResource Label}"/>
         <TextBox x:Name="customerIDTextBox" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Company Name:" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="companyNameTextBox" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Name:" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact title:" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>
         <TextBox x:Name="addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="City:" Grid.Column="1" Grid.Row="0" Style="{StaticResource Label}"/>
         <TextBox x:Name="cityTextBox" Grid.Column="1" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding City, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Country:" Grid.Column="1" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="countryTextBox" Grid.Column="1" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding Country, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Fax:" Grid.Column="1" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="faxTextBox" Grid.Column="1" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding Fax, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Phone:" Grid.Column="1" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="phoneTextBox" Grid.Column="1" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding Phone, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Postal Code:" Grid.Column="1" Grid.Row="4" VerticalAlignment="Center" Style="{StaticResource Label}"/>
         <TextBox x:Name="postalCodeTextBox" Grid.Column="1" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding PostalCode, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Region:" Grid.Column="1" Grid.Row="5" Style="{StaticResource Label}"/>
         <TextBox x:Name="regionTextBox" Grid.Column="1" Grid.Row="5" Style="{StaticResource CustTextBox}"
                  Text="{Binding Region, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
     </Grid>
     <Grid x:Name="newCustomerGrid" Grid.Row="1" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="5" DataContext="{Binding RelativeSource={RelativeSource FindAncestor, AncestorType={x:Type Window}}, Path=newCustomer, UpdateSourceTrigger=Explicit}" Visibility="Collapsed" Background="CornflowerBlue">
         <Grid.ColumnDefinitions>
             <ColumnDefinition Width="Auto" MinWidth="233"/>
             <ColumnDefinition Width="Auto" MinWidth="397"/>
         </Grid.ColumnDefinitions>
         <Grid.RowDefinitions>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
         </Grid.RowDefinitions>
         <Label Content="Customer ID:" Grid.Row="0" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_customerIDTextBox" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Company Name:" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_companyNameTextBox" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true }"/>
         <Label Content="Contact Name:" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact title:" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="City:" Grid.Column="1" Grid.Row="0" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_cityTextBox" Grid.Column="1" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding City, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Country:" Grid.Column="1" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_countryTextBox" Grid.Column="1" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding Country, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Fax:" Grid.Column="1" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_faxTextBox" Grid.Column="1" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding Fax, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Phone:" Grid.Column="1" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_phoneTextBox" Grid.Column="1" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding Phone, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Postal Code:" Grid.Column="1" Grid.Row="4" VerticalAlignment="Center" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_postalCodeTextBox" Grid.Column="1" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding PostalCode, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Region:" Grid.Column="1" Grid.Row="5" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_regionTextBox" Grid.Column="1" Grid.Row="5" Style="{StaticResource CustTextBox}"
                  Text="{Binding Region, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
     </Grid>
     <Grid x:Name="newOrderGrid" Grid.Row="1" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="5" DataContext="{Binding Path=newOrder, Mode=TwoWay}" Visibility="Collapsed" Background="LightGreen">
         <Grid.ColumnDefinitions>
             <ColumnDefinition Width="Auto" MinWidth="233"/>
             <ColumnDefinition Width="Auto" MinWidth="397"/>
         </Grid.ColumnDefinitions>
         <Grid.RowDefinitions>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
         </Grid.RowDefinitions>
         <Label Content="New Order Form" FontWeight="Bold"/>
         <Label Content="Employee ID:"  Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_employeeIDTextBox" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding EmployeeID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Order Date:"  Grid.Row="2" Style="{StaticResource Label}"/>
         <DatePicker x:Name="add_orderDatePicker" Grid.Row="2"  HorizontalAlignment="Right" Width="120"
                 SelectedDate="{Binding OrderDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
         <Label Content="Required Date:" Grid.Row="3" Style="{StaticResource Label}"/>
         <DatePicker x:Name="add_requiredDatePicker" Grid.Row="3" HorizontalAlignment="Right" Width="120"
                  SelectedDate="{Binding RequiredDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
         <Label Content="Shipped Date:"  Grid.Row="4"  Style="{StaticResource Label}"/>
         <DatePicker x:Name="add_shippedDatePicker"  Grid.Row="4"  HorizontalAlignment="Right" Width="120"
                 SelectedDate="{Binding ShippedDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
         <Label Content="Ship Via:"  Grid.Row="5" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_ShipViaTextBox"  Grid.Row="5" Style="{StaticResource CustTextBox}"
                  Text="{Binding ShipVia, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Freight"  Grid.Row="6" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_freightTextBox" Grid.Row="6" Style="{StaticResource CustTextBox}"
                  Text="{Binding Freight, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
     </Grid>
     <DataGrid x:Name="ordersDataGrid" SelectionUnit="Cell" SelectionMode="Single" AutoGenerateColumns="False" CanUserAddRows="false" IsEnabled="True" EnableRowVirtualization="True" Width="auto" ItemsSource="{Binding Source={StaticResource customerOrdersViewSource}}" Margin="10,10,10,10" Grid.Row="2" RowDetailsVisibilityMode="VisibleWhenSelected">
         <DataGrid.Columns>
             <DataGridTemplateColumn>
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <Button Content="Delete" Command="{StaticResource DeleteOrderCommand}" CommandParameter="{Binding}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="customerIDColumn" Binding="{Binding CustomerID}" Header="Customer ID" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="employeeIDColumn" Binding="{Binding EmployeeID}" Header="Employee ID" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="freightColumn" Binding="{Binding Freight}" Header="Freight" Width="SizeToHeader"/>
             <DataGridTemplateColumn x:Name="orderDateColumn" Header="Order Date" Width="SizeToHeader">
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <DatePicker SelectedDate="{Binding OrderDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="orderIDColumn" Binding="{Binding OrderID}" Header="Order ID" Width="SizeToHeader"/>
             <DataGridTemplateColumn x:Name="requiredDateColumn" Header="Required Date" Width="SizeToHeader">
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <DatePicker SelectedDate="{Binding RequiredDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="shipAddressColumn" Binding="{Binding ShipAddress}" Header="Ship Address" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipCityColumn" Binding="{Binding ShipCity}" Header="Ship City" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipCountryColumn" Binding="{Binding ShipCountry}" Header="Ship Country" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipNameColumn" Binding="{Binding ShipName}" Header="Ship Name" Width="SizeToHeader"/>
             <DataGridTemplateColumn x:Name="shippedDateColumn" Header="Shipped Date" Width="SizeToHeader">
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <DatePicker SelectedDate="{Binding ShippedDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="shipPostalCodeColumn" Binding="{Binding ShipPostalCode}" Header="Ship Postal Code" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipRegionColumn" Binding="{Binding ShipRegion}" Header="Ship Region" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipViaColumn" Binding="{Binding ShipVia}" Header="Ship Via" Width="SizeToHeader"/>
         </DataGrid.Columns>
     </DataGrid>
 </Grid>
```

## <a name="add-buttons-to-navigate-add-update-and-delete"></a>Agregar botones para navegar, agregar, actualizar y eliminar

En Windows Forms aplicaciones, se obtiene un objeto BindingNavigator con botones para navegar por las filas de una base de datos y realizar las operaciones CRUD básicas. WPF no proporciona un BindingNavigator, pero es lo suficientemente fácil para crear uno. Esto se hace con los botones dentro de un StackPanel horizontal y los botones se asocian con los comandos que se enlazan a los métodos del código subyacente.

Hay cuatro partes en la lógica de comandos: (1) los comandos, (2) los enlaces, (3) los botones y (4) los controladores de comandos en el código subyacente.

### <a name="add-commands-bindings-and-buttons-in-xaml"></a>Agregar comandos, enlaces y botones en XAML

1. En primer lugar, agregue los comandos del archivo *MainWindow. Xaml* dentro del elemento `Windows.Resources`:

    ```xaml
    <RoutedUICommand x:Key="FirstCommand" Text="First"/>
    <RoutedUICommand x:Key="LastCommand" Text="Last"/>
    <RoutedUICommand x:Key="NextCommand" Text="Next"/>
    <RoutedUICommand x:Key="PreviousCommand" Text="Previous"/>
    <RoutedUICommand x:Key="DeleteCustomerCommand" Text="Delete Customer"/>
    <RoutedUICommand x:Key="DeleteOrderCommand" Text="Delete Order"/>
    <RoutedUICommand x:Key="UpdateCommand" Text="Update"/>
    <RoutedUICommand x:Key="AddCommand" Text="Add"/>
    <RoutedUICommand x:Key="CancelCommand" Text="Cancel"/>
    ```

2. Un CommandBinding asigna un evento `RoutedUICommand` a un método en el código subyacente. Agregue este elemento de `CommandBindings` después de la etiqueta de cierre de `Windows.Resources`:

    ```xaml
    <Window.CommandBindings>
        <CommandBinding Command="{StaticResource FirstCommand}" Executed="FirstCommandHandler"/>
        <CommandBinding Command="{StaticResource LastCommand}" Executed="LastCommandHandler"/>
        <CommandBinding Command="{StaticResource NextCommand}" Executed="NextCommandHandler"/>
        <CommandBinding Command="{StaticResource PreviousCommand}" Executed="PreviousCommandHandler"/>
        <CommandBinding Command="{StaticResource DeleteCustomerCommand}" Executed="DeleteCustomerCommandHandler"/>
        <CommandBinding Command="{StaticResource DeleteOrderCommand}" Executed="DeleteOrderCommandHandler"/>
        <CommandBinding Command="{StaticResource UpdateCommand}" Executed="UpdateCommandHandler"/>
        <CommandBinding Command="{StaticResource AddCommand}" Executed="AddCommandHandler"/>
        <CommandBinding Command="{StaticResource CancelCommand}" Executed="CancelCommandHandler"/>
    </Window.CommandBindings>
    ```

3. Ahora, agregue el `StackPanel` con los botones de navegación, agregar, eliminar y actualizar. En primer lugar, agregue este estilo a `Windows.Resources`:

    ```xaml
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">
        <Setter Property="FontSize" Value="24"/>
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>
        <Setter Property="Margin" Value="2,2,2,0"/>
        <Setter Property="Width" Value="40"/>
        <Setter Property="Height" Value="auto"/>
    </Style>
    ```

     En segundo lugar, pegue este código justo después del `RowDefinitions` para el elemento de `Grid` externo, hacia la parte superior de la página XAML:

    ```xaml
    <StackPanel Orientation="Horizontal" Margin="2,2,2,0" Height="36" VerticalAlignment="Top" Background="Gainsboro" DataContext="{StaticResource customerViewSource}" d:LayoutOverrides="LeftMargin, RightMargin, TopMargin, BottomMargin">
        <Button Name="btnFirst" Content="|◄" Command="{StaticResource FirstCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnPrev" Content="◄" Command="{StaticResource PreviousCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnNext" Content="►" Command="{StaticResource NextCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnLast" Content="►|" Command="{StaticResource LastCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnDelete" Content="Delete Customer" Command="{StaticResource DeleteCustomerCommand}" FontSize="11" Width="120" Style="{StaticResource NavButton}"/>
        <Button Name="btnAdd" Content="New Customer" Command="{StaticResource AddCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
        <Button Content="New Order" Name="btnNewOrder" FontSize="11" Width="80" Style="{StaticResource NavButton}" Click="NewOrder_click"/>
        <Button Name="btnUpdate" Content="Commit" Command="{StaticResource UpdateCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
        <Button Content="Cancel" Name="btnCancel" Command="{StaticResource CancelCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
    </StackPanel>
    ```

### <a name="add-command-handlers-to-the-mainwindow-class"></a>Agregar controladores de comandos a la clase MainWindow

El código subyacente es mínimo, a excepción de los métodos Add y DELETE. La navegación se realiza llamando a métodos en la propiedad View del CollectionViewSource. En el `DeleteOrderCommandHandler` se muestra cómo realizar una eliminación en cascada en un pedido. Primero tenemos que eliminar el Order_Details que está asociado a él. El `UpdateCommandHandler` agrega un nuevo cliente o pedido a la colección, o bien simplemente actualiza un cliente o pedido existente con los cambios que el usuario realizó en los cuadros de texto.

Agregue estos métodos de controlador a la clase MainWindow en *MainWindow.Xaml.CS*. Si el CollectionViewSource de la tabla Customers tiene un nombre diferente, debe ajustar el nombre en cada uno de estos métodos:

[!code-csharp[CommandHandlers#3](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#3)]

## <a name="run-the-application"></a>Ejecutar la aplicación

Presione **F5** para iniciar la depuración. Debería ver los datos de cliente y de pedido rellenados en la cuadrícula y los botones de navegación deberían funcionar según lo previsto. Haga clic en **confirmar** para agregar un nuevo cliente o un pedido al modelo después de haber escrito los datos. Haga clic en **Cancelar** para salir de un nuevo formulario de cliente o de pedido nuevo sin guardar los datos. Puede realizar modificaciones en los clientes y pedidos existentes directamente en los cuadros de texto, y estos cambios se escriben automáticamente en el modelo.

## <a name="see-also"></a>Vea también

- [Visual Studio Data Tools para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
- [Documentación de Entity Framework](/ef/)