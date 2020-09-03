---
title: Crear una aplicación de datos sencilla con WPF y Entity Framework 6 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 65929fab-5d78-4e04-af1e-cf4957f230f6
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 403415eaf8a882efdd63fdb9a73b5489b91f2529
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651086"
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>Crear una aplicación de datos sencilla con WPF y Entity Framework 6
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tutorial se muestra cómo crear una aplicación básica de "formularios sobre datos" en Visual Studio con SQL Server LocalDB, la base de datos Northwind, Entity Framework 6 y Windows Presentation Foundation. Muestra cómo realizar el enlace de datos básico con una vista de maestro y detalles, y también tiene un "navegador de enlace" personalizado con botones para "desplazamiento siguiente", "movimiento anterior", "ir al principio", "ir al final", "actualizar" y "eliminar".

 Este artículo se centra en el uso de herramientas de datos en Visual Studio y no intenta explicar las tecnologías subyacentes en cualquier profundidad. Se supone que tiene conocimientos básicos de XAML, Entity Framework y SQL. En este ejemplo tampoco se muestra la arquitectura de MVVM, que es estándar para las aplicaciones de WPF. Sin embargo, puede copiar este código en su propia aplicación MVVM con muy pocas modificaciones.

## <a name="install-and-connect-to-northwind"></a>Instalar y conectarse a Northwind
 En este ejemplo se usa SQL Server Express LocalDB y la base de datos de ejemplo Northwind. También debe funcionar con otros productos de SQL Database si el proveedor de datos ADO.NET para ese producto admite Entity Framework.

1. Si todavía no lo ha hecho, instale SQL Server 2014 LocalDB Express 32 bit de la página de descarga de las [ediciones de SQL Server](https://www.microsoft.com/sql-server/sql-server-editions-express).

2. Instale la base de datos de ejemplo Northwind siguiendo estas instrucciones: [instalar SQL Server bases](../data-tools/install-sql-server-sample-databases.md)de datos de ejemplo.

3. [Agregue nuevas conexiones](../data-tools/add-new-connections.md) para Northwind.

## <a name="configure-the-project"></a>Configuración del proyecto

1. En Visual Studio, elija **archivo &#124; nuevo proyecto** y, a continuación, cree una nueva aplicación WPF de C#.

2. A continuación, agregaremos el paquete NuGet para Entity Framework 6. En Explorador de soluciones, seleccione el nodo del proyecto. En el menú principal, elija **proyecto &#124; administrar paquetes NuGet...**

     ![Elemento de menú administrar paquetes NuGet](../data-tools/media/raddata-vs2015-manage-nuget-packages.png "raddata_vs2015_manage_nuget_packages")

3. En el administrador de paquetes NuGet, haga clic en el vínculo **examinar** . Entity Framework es probablemente el paquete superior de la lista. Haga clic en **instalar** en el panel derecho y siga las indicaciones. La ventana de salida le indicará cuándo ha finalizado la instalación.

     ![Entity Framework paquete NuGet](../data-tools/media/raddata-vs2015-nuget-ef.png "raddata_vs2015_Nuget_EF")

4. Ahora podemos usar Visual Studio para crear un modelo basado en la base de datos Northwind.

## <a name="create-the-model"></a>Creación del modelo

1. Haga clic con el botón derecho en el nodo del proyecto en Explorador de soluciones y elija **agregar &#124; nuevo elemento**. En el panel izquierdo, en el nodo C#, elija **datos** y, en el panel central, elija **ADO.NET Entity Data Model**.

    ![Modelo de Entity Framework nuevo elemento de proyecto](../data-tools/media/raddata-ef-new-project-item.png "raddata EF nuevo elemento de proyecto")

2. Llame al modelo `Northwind_model` y elija Aceptar. Se abre el **Asistente para Entity Data Model**. Elija **EF Designer en la base de datos** y, a continuación, haga clic en **siguiente**.

    ![Modelo EF de la base de datos](../data-tools/media/raddata-ef-model-from-database.png "raddata modelo EF de la base de datos")

3. En la siguiente pantalla, elija la conexión de LocalDB Northwind y haga clic en **siguiente**.

4. En la página siguiente del asistente, se eligen las tablas, los procedimientos almacenados y otros objetos de base de datos que se van a incluir en el modelo de Entity Framework. Expanda el nodo DBO en la vista de árbol y elija clientes, pedidos y detalles de pedido. Deje los valores predeterminados activado y haga clic en **Finalizar**.

    ![Elegir objetos de base de datos para el modelo](../data-tools/media/raddata-choose-ef-objects.png "raddata elegir objetos EF")

5. El asistente genera las clases de C# que representan el modelo de Entity Framework. Se trata de clases de C# antiguas sin formato y son lo que se enlazará a la interfaz de usuario de WPF. El archivo. edmx describe las relaciones y otros metadatos que asocian las clases con los objetos de la base de datos.  Los archivos. TT son plantillas T4 que generan el código que funcionará en el modelo y guardará los cambios en la base de datos. Puede ver todos estos archivos en Explorador de soluciones en el nodo Northwind_model:

    ![Archivos de modelo de Explorador de soluciones EF](../data-tools/media/raddata-solution-explorer-ef-model-files.png "archivos de modelo de raddata Explorador de soluciones EF")

    La superficie del diseñador del archivo. edmx le permite modificar algunas propiedades y relaciones en el modelo. No vamos a usar el diseñador en este tutorial.

6. Los archivos. TT tienen fines generales y es necesario retocar uno de ellos para que funcionen con el enlace de los DataBindings de WPF, que requiere ObservableCollections.  En Explorador de soluciones, expanda el nodo Northwind_model hasta que encuentre Northwind_model. TT. (Asegúrese de que **no** está en el *. Archivo context. TT que está directamente debajo del archivo. edmx).

   - Reemplace las dos apariciones de <xref:System.Collections.ICollection> por <xref:System.Collections.ObjectModel.ObservableCollection%601> .

   - Reemplace la primera aparición de <xref:System.Collections.Generic.HashSet%601> en <xref:System.Collections.ObjectModel.ObservableCollection%601> torno a la línea 51. No reemplazar la segunda aparición de HashSet

   - Reemplace la única aparición de <xref:System.Collections.Generic> (alrededor de la línea 334) por <xref:System.Collections.ObjectModel> .

7. Presione **Ctrl + Mayús + B** para compilar el proyecto. Cuando finaliza la compilación, las clases del modelo son visibles para el Asistente para orígenes de datos.

   Ahora estamos preparados para enlazar este modelo a la página XAML para que podamos ver, navegar y modificar los datos.

## <a name="databind-the-model-to-the-xaml-page"></a>Enlazar el modelo a la página XAML
 Es posible escribir su propio código de enlace de la propiedad, pero es mucho más fácil dejar que Visual Studio lo haga automáticamente.

1. En el menú principal, elija **proyecto &#124; agregar nuevo origen de datos** para abrir el **Asistente para configuración de orígenes de datos**. Elija **objeto** porque estamos enlazando a las clases del modelo, no a la base de datos:

     ![Asistente para configuración de orígenes de datos con origen de objeto](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png "Asistente para la configuración de orígenes de datos de raddata con origen de objeto")

2. Selecciona Cliente.  (Los orígenes de los pedidos se generarán automáticamente a partir de la propiedad de navegación Orders en Customer).

     ![Agregar clases de entidad como orígenes de datos](../data-tools/media/raddata-add-entity-classes-as-data-sources.png "raddata agregar clases de entidad como orígenes de datos")

3. Haga clic en **Finish** (Finalizar).

4. Vaya a MainWindow. XAML en la vista Código. Vamos a mantener el XAML muy sencillo para los fines de este ejemplo. Cambie el título de MainWindow a algo más descriptivo y aumente el alto y el ancho a 600 x 800 por ahora. Siempre puede cambiarlo más adelante. Ahora, agregue estas tres definiciones de fila a la cuadrícula principal, una fila para los botones de navegación, una para los detalles del cliente, una para la cuadrícula que muestra los pedidos:

    ```xaml
    <Grid.RowDefinitions>
               <RowDefinition Height="auto"/>
               <RowDefinition Height="auto"/>
               <RowDefinition Height="*"/>
           </Grid.RowDefinitions>
    ```

5. Ahora, Abra MainWindow. XAML para verlo en el diseñador. Esto hará que la ventana orígenes de datos aparezca como una opción en el margen de la ventana de Visual Studio junto a cuadro de herramientas. Haga clic en la pestaña para abrir la ventana, o bien presione **Mayús + Alt + D** o elija **Ver &#124; otras ventanas &#124; orígenes de datos**. Vamos a mostrar cada propiedad en la clase customers en su propio cuadro de texto individual. En primer lugar, haga clic en la flecha en el cuadro combinado clientes y elija **detalles**. A continuación, arrastre el nodo hasta la parte central de la superficie de diseño para que el diseñador sepa que desea que aparezca en la fila central.  Si la coloca mal, puede especificar la fila manualmente más adelante en el código XAML. De forma predeterminada, los controles se colocan verticalmente en un elemento de cuadrícula, pero en este momento puede organizarlos como desee en el formulario.  Por ejemplo, puede que tenga sentido poner el cuadro de texto nombre en la parte superior, encima de la dirección. En la aplicación de ejemplo de este artículo se reordenan los campos y se reorganizan en dos columnas.

     ![Enlace de origen de datos de los clientes a controles individuales](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png "raddata el enlace de origen de datos a controles individuales")

     En la vista de código, ahora puede ver un nuevo `Grid` elemento en la fila 1 (la fila central) de la cuadrícula primaria. La cuadrícula primaria tiene un `DataContext` atributo que hace referencia a un CollectionViewSource que se ha agregado al `Windows.Resources` elemento. Dado ese contexto de datos, cuando el primer cuadro de texto, por ejemplo, se enlaza a "dirección", ese nombre se asigna a la `Address` propiedad en el `Customer` objeto actual en CollectionViewSource.

    ```xaml
    <Grid DataContext="{StaticResource customerViewSource}">
    ```

6. Cuando un cliente está visible en la mitad superior de la ventana, queremos ver sus pedidos en la mitad inferior. Mostraremos los pedidos en un solo control de vista de cuadrícula. Para que el enlace de los enlaces de los detalles maestros funcione según lo previsto, es importante que se enlace a la propiedad Orders en la clase customers, no al nodo Orders independiente. Preste atención a la siguiente ilustración. Arrastre la propiedad Orders de la clase customers a la mitad inferior del formulario para que el diseñador la coloque en la fila 2:

     ![Arrastrar clases de pedidos como cuadrícula](../data-tools/media/raddata-drag-orders-classes-as-grid.png "raddata arrastrar las clases de pedidos como cuadrícula")

7. Visual Studio ha generado todo el código de enlace que conecta los controles de interfaz de usuario a los eventos del modelo. Todo lo que necesitamos hacer para ver algunos datos es escribir código para rellenar el modelo. En primer lugar, vaya a MainWindow.xaml.cs y agregue un miembro de datos a la clase MainWindow para el contexto de datos. Este objeto, que se ha generado para nosotros, actúa como un control que realiza un seguimiento de los cambios y eventos del modelo. Mientras estamos aquí, vamos a agregar dos miembros que usaremos más adelante para agregar un nuevo cliente o nuevo pedido. También agregaremos la lógica de inicialización del constructor. La parte superior de nuestra clase debe ser similar a la siguiente:

    ```csharp
    public partial class MainWindow : Window
       {
           public Customer newCustomer { get; set; }
           public Order newOrder { get; set; }

           NorthwindEntities context = new NorthwindEntities();
           CollectionViewSource custViewSource;
           CollectionViewSource ordViewSource;

           public MainWindow()
           {
               InitializeComponent();
               newCustomer = new Customer();
               newOrder = new Order();
               custViewSource = ((CollectionViewSource)
                   (FindResource("customerViewSource")));
               ordViewSource = ((CollectionViewSource)
                   (FindResource("customerOrdersViewSource")));
               DataContext = this;
           }
    ```

     Agregue una `using` Directiva para System. Data. Entity para poner el método de extensión de carga en el ámbito:

    ```csharp
    using System.Data.Entity;
    ```

     Ahora, desplácese hacia abajo y busque el controlador de eventos Window_Loaded. Tenga en cuenta que Visual Studio ha agregado un objeto CollectionViewSource para nosotros. Esto representa el objeto NorthwindEntities que se seleccionó cuando se creó el modelo. Vamos a agregar código a Window_loaded de modo que todo el método tenga ahora el siguiente aspecto:

    ```csharp
    private void Window_Loaded(object sender, RoutedEventArgs e)
        {
            // Load is an extension method on IQueryable,
            // defined in the System.Data.Entity namespace.
            // This method enumerates the results of the query,
            // similar to ToList but without creating a list.
            // When used with Linq to Entities this method
            // creates entity objects and adds them to the context.
            context.Customers.Load();

            // After the data is loaded call the DbSet<T>.Local property
            // to use the DbSet<T> as a binding source.
            custViewSource.Source = context.Customers.Local;
        }
    ```

8. Presione **F5**. Debería ver los detalles del primer cliente que se recuperó en CollectionViewSource y sus pedidos en la cuadrícula de datos. El formato no es excelente, así que vamos a solucionarlo. y comjaulan una manera de ver los demás registros y realizar operaciones de CRUD básicas.

## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>Ajustar el diseño de la página y agregar cuadrículas para nuevos clientes y pedidos
 La organización predeterminada generada por Visual Studio no es ideal para nuestra aplicación, por lo que realizaremos algunos cambios manualmente en el código XAML. También se necesitarán algunos "formularios" (que son en realidad cuadrículas) para que el usuario pueda agregar un nuevo cliente o nuevo pedido.    Para poder agregar un nuevo cliente y un pedido, necesitamos un conjunto independiente de cuadros de texto que no estén enlazados a datos con `CollectionViewSource` . Controlaremos qué cuadrícula Ve el usuario en un momento dado estableciendo la propiedad visible en los métodos de controlador.

 Por último, agregaremos un botón eliminar a cada fila de la cuadrícula pedidos para permitir que un usuario elimine un pedido individual.

 En primer lugar, agregue estos estilos a Windows. Resources:

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
<Grid >
     <Grid.RowDefinitions>
         <RowDefinition Height="auto"/>
         <RowDefinition Height="auto"/>
         <RowDefinition Height="*"/>
     </Grid.RowDefinitions>
     <StackPanel  Orientation="Horizontal" Margin="2,2,2,0" Height="36" VerticalAlignment="Top" Background="Gainsboro" DataContext="{StaticResource customerViewSource}" d:LayoutOverrides="LeftMargin, RightMargin, TopMargin, BottomMargin">
         <Button Name="btnFirst" Content="|◄" Command="{StaticResource FirstCommand}" Style="{StaticResource NavButton}"  />
         <Button Name="btnPrev"  Content="◄" Command="{StaticResource PreviousCommand}" Style="{StaticResource NavButton}"/>
         <Button Name="btnNext"  Content="►" Command="{StaticResource NextCommand}"     Style="{StaticResource NavButton}"/>
         <Button Name="btnLast"  Content="►|" Command="{StaticResource LastCommand}" Style="{StaticResource NavButton}"/>
         <Button Name="btnDelete" Content="Delete Customer" Command="{StaticResource DeleteCustomerCommand}" FontSize="11" Width="120" Style="{StaticResource NavButton}"/>
         <Button  Name="btnAdd"   Content="New Customer"  Command="{StaticResource AddCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
         <Button Content="New Order" Name="btnNewOrder" FontSize="11" Width="80" Style="{StaticResource NavButton}" Click="NewOrder_click"/>
         <Button Name="btnUpdate" Content="Commit" Command="{StaticResource UpdateCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
         <Button Content="Cancel" Name="btnCancel"  Command="{StaticResource CancelCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
     </StackPanel>
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
         <TextBox x:Name="customerIDTextBox"  Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Company Name:"  Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="companyNameTextBox"  Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Name:"  Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Title:"  Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>
         <TextBox x:Name="addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="City:" Grid.Column="1" Grid.Row="0"  Style="{StaticResource Label}"/>
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
         <TextBox x:Name="add_customerIDTextBox"  Grid.Row="0"  Style="{StaticResource CustTextBox}"
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Company Name:"  Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_companyNameTextBox"  Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true }"/>
         <Label Content="Contact Name:"  Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Title:"  Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="City:" Grid.Column="1" Grid.Row="0"  Style="{StaticResource Label}"/>
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
                         <Button Content="Delete"  Command="{StaticResource DeleteOrderCommand}" CommandParameter="{Binding}"/>
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
 En Windows Forms aplicaciones, se obtiene un objeto BindingNavigator con botones para navegar por las filas de una base de datos y realizar las operaciones CRUD básicas. WPF no proporciona un BindingNavigator pero es lo bastante fácil de hacer. Lo haremos con botones dentro de un StackPanel horizontal en la fila inferior de la cuadrícula de páginas y asociaremos los botones con comandos que están enlazados a métodos en el código subyacente.

 Hay cuatro partes en la lógica de comandos: (1) los comandos, (2) los enlaces, (3) los botones y (4) los controladores de comandos en el código subyacente.

#### <a name="add-commands-bindings-and-buttons-in-xaml"></a>Agregar comandos, enlaces y botones en XAML

1. En primer lugar, vamos a agregar los comandos en nuestro archivo MainWindow. XAML dentro del elemento Windows. Resources:

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

2. Un CommandBinding asigna un evento RoutedUICommand a un método en el código subyacente. Agregue este elemento CommandBindings después de la etiqueta de cierre Windows. Resources:

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

3. Ahora vamos a agregar el StackPanel con los botones de navegación, agregar, eliminar y actualizar. En primer lugar, agregue este estilo a Windows. Resources:

    ```xaml
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">
        <Setter Property="FontSize" Value="24"/>
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>
        <Setter Property="Margin" Value="2,2,2,0"/>
        <Setter Property="Width" Value="40"/>
        <Setter Property="Height" Value="auto"/>
    </Style>
    ```

     Ahora, pegue este código justo después de RowDefinitions para el elemento de cuadrícula exterior hacia la parte superior de la página XAML:

    ```xaml
    <StackPanel  Orientation="Horizontal" Margin="2,2,2,0" Height="36" VerticalAlignment="Top" Background="Gainsboro" DataContext="{StaticResource customerViewSource}" d:LayoutOverrides="LeftMargin, RightMargin, TopMargin, BottomMargin">
        <Button Name="btnFirst" Content="|◄" Command="{StaticResource FirstCommand}" Style="{StaticResource NavButton}"  />
        <Button Name="btnPrev"  Content="◄" Command="{StaticResource PreviousCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnNext"  Content="►" Command="{StaticResource NextCommand}"     Style="{StaticResource NavButton}"/>
        <Button Name="btnLast"  Content="►|" Command="{StaticResource LastCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnDelete" Content="Delete Customer" Command="{StaticResource DeleteCustomerCommand}" FontSize="11" Width="120" Style="{StaticResource NavButton}"/>
        <Button  Name="btnAdd"   Content="New Customer"  Command="{StaticResource AddCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
        <Button Content="New Order" Name="btnNewOrder" FontSize="11" Width="80" Style="{StaticResource NavButton}" Click="NewOrder_click"/>
        <Button Name="btnUpdate" Content="Commit" Command="{StaticResource UpdateCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
        <Button Content="Cancel" Name="btnCancel"  Command="{StaticResource CancelCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
    </StackPanel>
    ```

#### <a name="add-command-handlers-to-the-mainwindow-class"></a>Agregar controladores de comandos a la clase MainWindow

1. El código subyacente es mínimo, a excepción de los métodos Add y DELETE. Tenga en cuenta que la navegación se realiza llamando a métodos en la propiedad View del CollectionViewSource. El DeleteOrderCommandHandler muestra cómo realizar una eliminación en cascada en un pedido. Primero tenemos que eliminar los Order_Details asociados a él. El UpdateCommandHandler agrega un nuevo cliente a la colección; de lo contrario, solo actualiza el objeto existente con cualquier cambio que haya realizado el usuario en los cuadros de texto.

2. Agregue estos métodos de controlador a la clase MainWindow en MainWindow.xaml.cs, si el CollectionViewSource de la tabla Customers tiene un nombre diferente, tendrá que ajustar el nombre en cada uno de estos métodos:

    ```csharp
       private void LastCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        custViewSource.View.MoveCurrentToLast();
    }

    private void PreviousCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        custViewSource.View.MoveCurrentToPrevious();
    }

    private void NextCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        custViewSource.View.MoveCurrentToNext();
    }

    private void FirstCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        custViewSource.View.MoveCurrentToFirst();
    }

    private void DeleteCustomerCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        // If existing window is visible, then delete the customer and all their orders.
        // In a real application, you should add warnings and allow a user to cancel the operation.
        var cur = custViewSource.View.CurrentItem as Customer;

        var cust = (from c in context.Customers
                    where c.CustomerID == cur.CustomerID
                    select c).FirstOrDefault();

        if (cust != null)
        {
            foreach (var ord in cust.Orders.ToList())
            {
                Delete_Order(ord);
            }
            context.Customers.Remove(cust);
        }
        context.SaveChanges();
        custViewSource.View.Refresh();
    }

    // Commit changes from the new customer form, the new order form,
    // or edits made to the existing customer form.
    private void UpdateCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        if (newCustomerGrid.IsVisible)
        {
            // Create a new object because the old one
            // is being tracked by EF now.
            newCustomer = new Customer();
            newCustomer.Address = add_addressTextBox.Text;
            newCustomer.City = add_cityTextBox.Text;
            newCustomer.CompanyName = add_companyNameTextBox.Text;
            newCustomer.ContactName = add_contactNameTextBox.Text;
            newCustomer.ContactTitle = add_contactTitleTextBox.Text;
            newCustomer.Country = add_countryTextBox.Text;
            newCustomer.CustomerID = add_customerIDTextBox.Text;
            newCustomer.Fax = add_faxTextBox.Text;
            newCustomer.Phone = add_phoneTextBox.Text;
            newCustomer.PostalCode = add_postalCodeTextBox.Text;
            newCustomer.Region = add_regionTextBox.Text;

            // Perform very basic validation
            if (newCustomer.CustomerID.Length == 5)
            {
                // Insert the new customer at correct position:
                int len = context.Customers.Local.Count();
                int pos = len;
                for (int i = 0; i < len; ++i)
                {
                    if (String.CompareOrdinal(newCustomer.CustomerID, context.Customers.Local[i].CustomerID) < 0)
                    {
                        pos = i;
                        break;
                    }
                }
                context.Customers.Local.Insert(pos, newCustomer);
                custViewSource.View.Refresh();
                custViewSource.View.MoveCurrentTo(newCustomer);
            }
            else
            {
                MessageBox.Show("CustomerID must have 5 characters.");
            }

            newCustomerGrid.Visibility = Visibility.Collapsed;
            existingCustomerGrid.Visibility = Visibility.Visible;
        }
        else if (newOrderGrid.IsVisible)
        {
            // Order ID is auto-generated so we don't set it here.
            // For CustomerID, address, etc we use the values from current customer.
            // User can modify these in the datagrid after the order is entered.

            newOrder.OrderDate = add_orderDatePicker.SelectedDate;
            newOrder.RequiredDate = add_requiredDatePicker.SelectedDate;
            newOrder.ShippedDate = add_shippedDatePicker.SelectedDate;
            try
            {
                // Exercise for the reader if you are using Northwind:
                // Add the Northwind Shippers table to the model.
                // Acceptable ShipperID values are 1, 2, or 3.
                if (add_ShipViaTextBox.Text == "1" || add_ShipViaTextBox.Text == "2"
                    || add_ShipViaTextBox.Text == "3")
                {
                    newOrder.ShipVia = Convert.ToInt32(add_ShipViaTextBox.Text);
                }
                else
                {
                    MessageBox.Show("Shipper ID must be 1, 2, or 3 in Northwind.");
                    return;
                }
            }
            catch
            {
                MessageBox.Show("Ship Via must be convertible to int");
                return;
            }
            try
            {
                newOrder.Freight = Convert.ToDecimal(add_freightTextBox.Text);
            }
            catch
            {
                MessageBox.Show("Freight must be convertible to decimal.");
                return;
            }

            // Add the order into the EF model
            context.Orders.Add(newOrder);
            ordViewSource.View.Refresh();
        }

        // Save the changes, either for a new customer, a new order
        // or an edit in an existing customer or order
        context.SaveChanges();
    }

    // Sets up the form so that user can enter data. Data is later
    // saved when user clicks Commit.
    private void AddCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        existingCustomerGrid.Visibility = Visibility.Collapsed;
        newOrderGrid.Visibility = Visibility.Collapsed;
        newCustomerGrid.Visibility = Visibility.Visible;

        // Clear all the text boxes before adding a new customer.
        foreach (var child in newCustomerGrid.Children)
        {
            var tb = child as TextBox;
            if (tb != null)
            {
                tb.Text = "";
            }
        }
    }

    private void NewOrder_click(object sender, RoutedEventArgs e)
    {
        var cust = custViewSource.View.CurrentItem as Customer;
        if (cust == null)
        {
            MessageBox.Show("No customer selected.");
            return;
        }

        newOrder.CustomerID = cust.CustomerID;

        // Get address and other mostly constant fields from
        // an existing order, if one exists
        var coll = custViewSource.Source as IEnumerable<Customer>;
        var lastOrder = (from c in coll
                         from ord in c.Orders
                         select ord).LastOrDefault();
        if (lastOrder != null)
        {
            newOrder.ShipAddress = lastOrder.ShipAddress;
            newOrder.ShipCity = lastOrder.ShipCity;
            newOrder.ShipCountry = lastOrder.ShipCountry;
            newOrder.ShipName = lastOrder.ShipName;
            newOrder.ShipPostalCode = lastOrder.ShipPostalCode;
            newOrder.ShipRegion = lastOrder.ShipRegion;
        }

        existingCustomerGrid.Visibility = Visibility.Collapsed;
        newCustomerGrid.Visibility = Visibility.Collapsed;
        newOrderGrid.UpdateLayout();
        newOrderGrid.Visibility = Visibility.Visible;
    }

    // Cancels any input into the new customer form
    private void CancelCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        add_addressTextBox.Text = "";
        add_cityTextBox.Text = "";
        add_companyNameTextBox.Text = "";
        add_contactNameTextBox.Text = "";
        add_contactTitleTextBox.Text = "";
        add_countryTextBox.Text = "";
        add_customerIDTextBox.Text = "";
        add_faxTextBox.Text = "";
        add_phoneTextBox.Text = "";
        add_postalCodeTextBox.Text = "";
        add_regionTextBox.Text = "";

        existingCustomerGrid.Visibility = Visibility.Visible;
        newCustomerGrid.Visibility = Visibility.Collapsed;
        newOrderGrid.Visibility = Visibility.Collapsed;
    }

    private void Delete_Order(Order order)
    {
        // Find the order in the EF model.
        var ord = (from o in context.Orders.Local
                   where o.OrderID == order.OrderID
                   select o).FirstOrDefault();

        // Delete all the order_details that have
        // this Order as a foreign key
        foreach (var detail in ord.Order_Details.ToList())
        {
            context.Order_Details.Remove(detail);
        }

        // Now it's safe to delete the order.
        context.Orders.Remove(ord);
        context.SaveChanges();

        // Update the data grid.
        ordViewSource.View.Refresh();
    }

    private void DeleteOrderCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        // Get the Order in the row in which the Delete button was clicked.
        Order obj = e.Parameter as Order;
        Delete_Order(obj);
    }
    ```

3. Presione **F5**. Debería ver los datos y los botones de navegación deberían funcionar según lo previsto. Haga clic en "confirmar" para agregar un nuevo cliente o pedido al modelo después de haber escrito los datos.  Haga clic en "Cancelar" para devolverlo a un nuevo formulario de cliente o de pedido sin guardar. Puede realizar modificaciones en los clientes y pedidos existentes directamente en los cuadros de texto, y estos cambios se escribirán automáticamente en el modelo.

## <a name="see-also"></a>Consulte también
 Documentación [de Visual Studio Data Tools para .net](../data-tools/visual-studio-data-tools-for-dotnet.md) [Entity Framework](https://msdn.microsoft.com/data/ee712907.aspx)
