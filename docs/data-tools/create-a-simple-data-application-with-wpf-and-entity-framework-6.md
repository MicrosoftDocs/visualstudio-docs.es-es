---
title: Crear una aplicación de datos sencilla con WPF y Entity Framework 6
ms.date: 08/22/2017
ms.topic: conceptual
dev_langs:
- CSharp
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 5993256b41a07c4861ef2def58dc14d7fd849313
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305616"
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>Crear una aplicación de datos sencilla con WPF y Entity Framework 6

Este tutorial muestra cómo crear una aplicación básica "formularios sobre datos" en Visual Studio. La aplicación usa SQL Server LocalDB, la base de datos de Northwind, Entity Framework 6 y Windows Presentation Foundation. Muestra cómo realizar el enlace de datos básica con una vista principal-detallada y también tiene un navegador de enlace personalizado con botones para **Mover siguiente**, **mover anterior**, **mover a partir de**, **Mover al final**, **actualización** y **eliminar**.

En este artículo se centra en usar las herramientas de datos en Visual Studio y no intenta explicar las tecnologías subyacentes en cualquier profundidad. Se supone que tiene un conocimiento básico con XAML, Entity Framework y SQL. También en este ejemplo no muestra la arquitectura Model-View-ViewModel (MVVM), que es el estándar para las aplicaciones de WPF. Sin embargo, puede copiar este código en su propia aplicación de MVVM con pocas modificaciones.

## <a name="install-and-connect-to-northwind"></a>Instalar y conectar a Northwind

En este ejemplo se usa SQL Server Express LocalDB y la base de datos de ejemplo Northwind. Si el proveedor de datos ADO.NET para ese producto es compatible con Entity Framework, debería funcionar perfectamente con otros productos de base de datos SQL.

1.  Si no tiene SQL Server Express LocalDB, instálelo de desde el [página de descarga de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), o a través del **instalador de Visual Studio**. En el **instalador de Visual Studio**, puede instalar SQL Server Express LocalDB como parte de la **desarrollo de escritorio de .NET** carga de trabajo o como un componente individual.

2.  Instalar la base de datos de ejemplo Northwind, siga estos pasos:

    1. En Visual Studio, abra el **Explorador de objetos de SQL Server** ventana. (**Explorador de objetos de SQL Server** se instala como parte de la **procesamiento y almacenamiento de datos** carga de trabajo en el **instalador de Visual Studio**.) Expanda el **SQL Server** nodo. Haga doble clic en la instancia de LocalDB y seleccione **nueva consulta**.

       Se abre una ventana del editor de consultas.

    2. Copia el [script Transact-SQL de Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) en el Portapapeles. Este script de Transact-SQL crea la base de datos Northwind desde el principio y lo rellena con datos.

    3. Pegue el script de Transact-SQL en el editor de consultas y, a continuación, elija el **Execute** botón.

       Después de un breve tiempo, finalice la consulta y se crea la base de datos Northwind.

3.  [Agregar nuevas conexiones](../data-tools/add-new-connections.md) para Northwind.

## <a name="configure-the-project"></a>Configuración del proyecto

1.  En Visual Studio, elija **archivo** > **New** > **proyecto** y, a continuación, cree una nueva aplicación de WPF de C#.

2.  A continuación, agregue el paquete NuGet de Entity Framework 6. En **el Explorador de soluciones**, seleccione el nodo del proyecto. En el menú principal, elija **proyecto** > **administrar paquetes de NuGet**.

     ![Administrar el elemento de menú de paquetes de NuGet](../data-tools/media/raddata_vs2015_manage_nuget_packages.png)

3.  En el **Administrador de paquetes de NuGet**, haga clic en el **examinar** vínculo. Entity Framework es probablemente el paquete en la lista superior. Haga clic en **instalar** en el panel derecho y siga las indicaciones. La ventana de salida indica cuando finalice la instalación.

     ![Paquete de NuGet de Entity Framework](../data-tools/media/raddata_vs2015_nuget_ef.png)

4.  Ahora puede usar Visual Studio para crear un modelo basado en la base de datos Northwind.

## <a name="create-the-model"></a>Creación del modelo

1. Haga doble clic en el nodo del proyecto en **el Explorador de soluciones** y elija **agregar** > **nuevo elemento**. En el panel izquierdo, bajo el nodo de C#, elija **datos** y en el panel central, elija **ADO.NET Entity Data Model**.

   ![Entity Framework modelo nuevo elemento de proyecto](../data-tools/media/raddata-ef-new-project-item.png)

2. Llamar al modelo `Northwind_model` y elija **Aceptar**. Se abre el **Asistente para Entity Data Model**. Elija **EF Designer de base de datos** y, a continuación, haga clic en **siguiente**.

   ![Modelo EF desde la base de datos](../data-tools/media/raddata-ef-model-from-database.png)

3. En la siguiente pantalla, elija su LocalDB Northwind, conexión y haga clic en **siguiente**.

4. En la siguiente página del asistente, elija qué tablas, procedimientos almacenados y otros objetos de base de datos para incluir en el modelo de Entity Framework. Expanda el nodo dbo en la vista de árbol y elija **clientes**, **pedidos**, y **Order Details**. Deje las opciones predeterminadas y haga clic en **finalizar**.

    ![Elija los objetos de base de datos para el modelo](../data-tools/media/raddata-choose-ef-objects.png)

5. El asistente genera las clases de C# que representan el modelo de Entity Framework. Las clases son clases C# antiguas sin formato y son lo que enlazar datos a la interfaz de usuario WPF. El *.edmx* archivo describe las relaciones y otros metadatos que se asocia a las clases de objetos en la base de datos. El *.tt* archivos son plantillas T4 que generan el código que funciona en el modelo y guarde los cambios en la base de datos. Puede ver todos estos archivos en **el Explorador de soluciones** bajo el nodo Northwind_model:

      ![Archivos de modelo de EF del explorador de soluciones](../data-tools/media/raddata-solution-explorer-ef-model-files.png)

    La superficie del diseñador para el *.edmx* archivo le permite modificar algunas propiedades y relaciones en el modelo. No vamos a usar el Diseñador de este tutorial.

6. El *.tt* archivos son para fines generales y deberá ajustar uno de ellos para que funcione con el enlace de datos WPF, lo que requiere ObservableCollections. En **el Explorador de soluciones**, expanda el nodo Northwind_model hasta que encuentre *Northwind_model.tt*. (Asegúrese de que no están en el *. Context.tt* archivo, que está justo debajo del *.edmx* archivo.)

   -   Reemplace las dos repeticiones de <xref:System.Collections.ICollection> con <xref:System.Collections.ObjectModel.ObservableCollection%601>.

   -   Reemplace la primera aparición de <xref:System.Collections.Generic.HashSet%601> con <xref:System.Collections.ObjectModel.ObservableCollection%601> alrededor de la línea 51. No se debe reemplazar la segunda aparición del objeto HashSet.

   -   Reemplazar la aparición única de <xref:System.Collections.Generic> (alrededor de la línea 431) con <xref:System.Collections.ObjectModel>.

7. Presione **Ctrl**+**MAYÚS**+**B** para compilar el proyecto. Cuando finalice la compilación, las clases del modelo son visibles para el Asistente para orígenes de datos.

Ahora está listo para enlazar este modelo a la página XAML para que se puede ver, navegar y modificar los datos.

## <a name="databind-the-model-to-the-xaml-page"></a>Enlazar datos en el modelo a la página XAML

Es posible escribir su propio código de enlace de datos, pero resulta mucho más fácil permitir que Visual Studio lo haga por usted.

1.  En el menú principal, elija **proyecto** > **Agregar nuevo origen de datos** para que aparezca el **Asistente para configuración de origen de datos**. Elija **objeto** porque va a enlazar a las clases del modelo, no a la base de datos:

     ![Asistente para configuración de origen de datos con el origen de objeto](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png)

2.  Seleccione **cliente**. (Los orígenes para los pedidos se generan automáticamente desde la propiedad de navegación de pedidos de cliente).

     ![Agregar clases de entidad como orígenes de datos](../data-tools/media/raddata-add-entity-classes-as-data-sources.png)

3.  Haga clic en **Finalizar**.

4.  Vaya a *MainWindow.xaml* en la vista código. Simplificaremos el XAML para los fines de este ejemplo. Cambiar el título de MainWindow a algo más descriptivo y aumentar el alto y ancho a 800 x 600 por ahora. Siempre puede cambiar más adelante. Ahora, agregue estas definiciones de tres filas a la cuadrícula principal, una fila para los botones de navegación, uno de los detalles del cliente y otro para la cuadrícula que muestra los pedidos:

    ```xaml
    <Grid.RowDefinitions>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="*"/>
        </Grid.RowDefinitions>
    ```

5.  Ahora abra *MainWindow.xaml* para que se está viendo en el diseñador. Esto hace que el **orígenes de datos** ventana aparezca como una opción en el margen de la ventana de Visual Studio junto a la **cuadro de herramientas**. Haga clic en la pestaña para abrir la ventana, o presione else **MAYÚS**+**Alt**+**d.** o elija **vista**  >  **Otros Windows** > **orígenes de datos**. Vamos a mostrar cada propiedad de la clase de los clientes en su propio cuadro de texto individuales. En primer lugar, haga clic en la flecha de la **clientes** combinado y elija **detalles**. A continuación, arrastre el nodo a la parte central de la superficie de diseño para que sepa que el diseñador que desee que aparezca en la fila central. Si se pierde, puede especificar la fila manualmente más adelante en el XAML. De forma predeterminada, los controles se colocan verticalmente en un elemento de cuadrícula, pero en este momento, puede organizarlos como desee en el formulario. Por ejemplo, tendría sentido poner el **nombre** cuadro de texto en la parte superior, por encima de la dirección. La aplicación de ejemplo para este artículo reordena los campos y ellos reorganiza en dos columnas.

     ![Enlace de origen de datos de los clientes a controles individuales](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png)

     En la vista de código, ahora puede ver un nuevo `Grid` elemento en la fila 1 (la fila central) de la cuadrícula principal. El elemento primario Grid tiene un `DataContext` atributo que hace referencia a CollectionViewSource que se han agregado a la `Windows.Resources` elemento. Dado ese contexto de datos, cuando el primer cuadro de texto que se enlaza a **dirección**, ese nombre se asigna a la `Address` propiedad actual `Customer` objeto en CollectionViewSource.

    ```xaml
    <Grid DataContext="{StaticResource customerViewSource}">
    ```

6.  Cuando un cliente está visible en la mitad superior de la ventana, en el que desea ver sus pedidos en la parte inferior de mitad. Mostrar los pedidos en un control de vista de cuadrícula único. Para que el enlace de datos principal-detalle funcione según lo esperado, es importante que se enlazan a la propiedad Orders en la clase de los clientes, no para el nodo de pedidos independiente. Arrastre la propiedad Orders de la clase de los clientes a la mitad inferior del formulario, para que el diseñador lo coloca en la fila 2:

     ![Arrastre las clases de pedidos como cuadrícula](../data-tools/media/raddata-drag-orders-classes-as-grid.png)

7.  Visual Studio ha generado todo el código de enlace que se conecta a los controles de interfaz de usuario a los eventos en el modelo. Todo lo que necesita hacer para ver algunos datos, consiste en escribir código para rellenar el modelo. En primer lugar, vaya a *MainWindow.xaml.cs* y agregue un miembro de datos a la clase MainWindow para el contexto de datos. Este objeto, que se ha generado automáticamente, actúa algo parecido a un control que realiza el seguimiento de cambios y eventos en el modelo. También agregará la lógica de inicialización del constructor. La parte superior de la clase debe tener este aspecto:

     [!code-csharp[MainWindow#1](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#1)]

     Agregar un `using` System.Data.Entity poner el método de extensión de la carga en el ámbito de directiva:

     ```csharp
     using System.Data.Entity;
     ```

     Ahora, desplácese hacia abajo y busque el `Window_Loaded` controlador de eventos. Tenga en cuenta que Visual Studio ha agregado un objeto CollectionViewSource. Representa el objeto NorthwindEntities que seleccionó al crear el modelo. Vamos a agregar código a `Window_Loaded` para que todo el método ahora este aspecto:

     [!code-csharp[Window_Loaded#2](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#2)]

8.  Presione **F5**. Debería ver los detalles para el primer cliente que se recuperó en CollectionViewSource. También debería ver sus pedidos en la cuadrícula de datos. El formato no es excelente, así que vamos a corregir que. También puede crear una forma de ver los demás registros y realizar operaciones CRUD básicas.

## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>Ajustar el diseño de página y agregue las cuadrículas para clientes y pedidos nuevos

La organización predeterminada generada por Visual Studio no es ideal para su aplicación, por lo que deberá realizar algunos cambios manualmente en el XAML. También necesita algunas "formularios" (que son realmente las cuadrículas) para permitir al usuario agregar un nuevo cliente o un pedido. Para poder agregar un nuevo cliente y un pedido, se necesita un conjunto independiente de los cuadros de texto que no están enlazados a datos a la `CollectionViewSource`. Podrá controlar qué ve el usuario en cualquier momento estableciendo la propiedad Visible en los métodos de control de cuadrícula. Por último, agregar un botón Eliminar para cada fila de la cuadrícula de pedidos para permitir al usuario eliminar un pedido individual.

En primer lugar, agregue estos estilos para el `Windows.Resources` elemento *MainWindow.xaml*:

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

A continuación, reemplace toda la cuadrícula externa con este marcado:

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
         <Label Content="Contact Title:" Grid.Row="3" Style="{StaticResource Label}"/>
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
         <Label Content="Contact Title:" Grid.Row="3" Style="{StaticResource Label}"/>
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

En las aplicaciones de Windows Forms, obtener un objeto de BindingNavigator con botones para navegar por las filas de una base de datos y realizar operaciones CRUD básicas. WPF no proporciona un BindingNavigator, pero es bastante fácil de crear uno. Hacer eso con botones dentro de un elemento StackPanel horizontal y asociar los botones de comandos que están enlazados a los métodos en el código subyacente.

Hay partes cuatros a la lógica de comando: (1) los comandos, (2) los enlaces, (3) los botones y (4) los controladores de comandos en el código subyacente.

### <a name="add-commands-bindings-and-buttons-in-xaml"></a>Agregar comandos, enlaces y los botones en XAML

1.  En primer lugar, agregue los comandos en el *MainWindow.xaml* archivo dentro de la `Windows.Resources` elemento:

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

2.  Asigna un CommandBinding un `RoutedUICommand` eventos a un método en el código subyacente. Agregar esto `CommandBindings` elemento tras el `Windows.Resources` etiqueta de cierre:

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

3.  Ahora, agregue el `StackPanel` con el panel de navegación, agregar, eliminar y actualizar los botones. En primer lugar, agregue este estilo a `Windows.Resources`:

    ```xaml
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">
        <Setter Property="FontSize" Value="24"/>
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>
        <Setter Property="Margin" Value="2,2,2,0"/>
        <Setter Property="Width" Value="40"/>
        <Setter Property="Height" Value="auto"/>
    </Style>
    ```

     En segundo lugar, pegue este código justo después del `RowDefinitions` para el exterior `Grid` elemento hacia la parte superior de la página XAML:

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

El código subyacente es mínimo, excepto los métodos add y delete. Navegación se realiza llamando a métodos en la propiedad de la vista de CollectionViewSource. La `DeleteOrderCommandHandler` muestra cómo realizar una eliminación en cascada de un pedido. Se debe eliminar primero el Order_Details que están asociados con ella. El `UpdateCommandHandler` agrega un nuevo cliente o un pedido a la colección, o bien simplemente actualiza un cliente existente o un pedido con los cambios realizados por el usuario en los cuadros de texto.

Agregue estos métodos de controlador a la clase MainWindow en *MainWindow.xaml.cs*. Si su CollectionViewSource para la tabla Customers tiene un nombre diferente, deberá ajustar el nombre de cada uno de estos métodos:

[!code-csharp[CommandHandlers#3](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#3)]

## <a name="run-the-application"></a>Ejecutar la aplicación

Presione **F5** para iniciar la depuración. Debería ver datos de clientes y pedidos rellena en la cuadrícula, y los botones de navegación deberían funcionar según lo previsto. Haga clic en **confirmar** para agregar un nuevo cliente o un pedido para el modelo después de escribir los datos. Haga clic en **cancelar** para realizar una copia fuera de un cliente nuevo o un nuevo formulario de pedido sin guardar los datos. Puede realizar modificaciones a los clientes existentes y los pedidos directamente en los cuadros de texto, y esos cambios se escriben en el modelo automáticamente.

## <a name="see-also"></a>Vea también

- [Visual Studio Data Tools para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
- [Documentación de Entity Framework](/ef/)