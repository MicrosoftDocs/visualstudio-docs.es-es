---
title: Crear una aplicación de datos sencilla con WPF y Entity Framework 6 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 65929fab-5d78-4e04-af1e-cf4957f230f6
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 56c211597e99689e1ad263cfe12d7dafdf3cf5cc
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "59002700"
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>Crear una aplicación de datos sencilla con WPF y Entity Framework 6
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Este tutorial muestra cómo crear una aplicación básica "formularios sobre datos" en Visual Studio con SQL Server LocalDB, la base de datos de Northwind, Entity Framework 6 y Windows Presentation Foundation. Muestra cómo realizar el enlace de datos básica con una vista principal-detallada y también tiene un personalizado "enlace navegador" con botones para "Mover siguiente", "Mover anterior," "Mover al principio," "mover al final," "Actualizar" y "Eliminar".  
  
 En este artículo se centra en usar las herramientas de datos en Visual Studio y no intenta explicar las tecnologías subyacentes en cualquier profundidad. Se supone que tiene un conocimiento básico con XAML, Entity Framework y SQL. También en este ejemplo no muestra la arquitectura MVVM, que es el estándar para las aplicaciones de WPF. Sin embargo, puede copiar este código en su propia aplicación de MVVM con muy pocas modificaciones.  
  
## <a name="install-and-connect-to-northwind"></a>Instalar y conectar a Northwind  
 En este ejemplo se usa SQL Server Express LocalDB y la base de datos de ejemplo Northwind. Debería funcionar con otros productos de base de datos SQL igual de bien si el proveedor de datos ADO.NET para ese producto es compatible con Entity Framework.  
  
1.  Si no lo ha hecho ya, instale SQL Server 2014 LocalDB Express de 32 bits desde el [página de descarga de las ediciones de SQL Server](https://www.microsoft.com/sql-server/sql-server-editions-express).  
  
2.  Instale la base de datos de ejemplo Northwind siguiendo estas instrucciones: [Instalar bases de datos de ejemplo de SQL Server](../data-tools/install-sql-server-sample-databases.md).  
  
3.  [Agregar nuevas conexiones](../data-tools/add-new-connections.md) para Northwind.  
  
## <a name="configure-the-project"></a>Configuración del proyecto  
  
1.  En Visual Studio, elija **archivo &#124; nuevo proyecto** y, a continuación, cree una nueva aplicación de WPF de C#.  
  
2.  A continuación, agregaremos el paquete NuGet de Entity Framework 6. En el Explorador de soluciones, seleccione el nodo del proyecto. En el menú principal, elija **proyecto &#124; administrar paquetes NuGet...**  
  
     ![Administrar paquetes de NuGet elemento de menú](../data-tools/media/raddata-vs2015-manage-nuget-packages.png "raddata_vs2015_manage_nuget_packages")  
  
3.  En el Administrador de paquetes de NuGet, haga clic en el **examinar** vínculo. Entity Framework es probablemente el paquete en la lista superior. Haga clic en **instalar** en el panel derecho y siga las indicaciones. La ventana de salida indicará cuando finalice la instalación.  
  
     ![Paquete de NuGet de Entity Framework](../data-tools/media/raddata-vs2015-nuget-ef.png "raddata_vs2015_Nuget_EF")  
  
4.  Ahora podemos usar Visual Studio para crear un modelo basado en la base de datos Northwind.  
  
## <a name="create-the-model"></a>Creación del modelo  
  
1. Haga clic con el botón derecho en el nodo del proyecto en el Explorador de soluciones y elija **agregar &#124; nuevo elemento**. En el panel izquierdo, bajo el nodo de C#, elija **datos** y en el panel central, elija **ADO.NET Entity Data Model**.  
  
    ![Entity Framework modelo nuevo elemento de proyecto](../data-tools/media/raddata-ef-new-project-item.png "raddata EF nuevo elemento de proyecto")  
  
2. Llamar al modelo `Northwind_model` y haga clic en Aceptar. Se abrirá el **Asistente para Entity Data Model**. Elija **EF Designer de base de datos** y, a continuación, haga clic en **siguiente**.  
  
    ![Modelo EF desde la base de datos](../data-tools/media/raddata-ef-model-from-database.png "raddata modelo de EF desde la base de datos")  
  
3. En la siguiente pantalla, elija su LocalDB Northwind, conexión y haga clic en **siguiente**.  
  
4. En la siguiente página del asistente, se elige qué tablas, procedimientos almacenados y otros objetos de base de datos para incluir en el modelo de Entity Framework. Expanda el nodo dbo en la vista de árbol y elija Customers, Orders y Order Details. Deje las opciones predeterminadas y haga clic en **finalizar**.  
  
    ![Elija los objetos de base de datos para el modelo](../data-tools/media/raddata-choose-ef-objects.png "raddata elegir objetos de EF")  
  
5. El asistente genera las clases de C# que representan el modelo de Entity Framework. Estas son clases C# antiguas sin formato y son lo que vamos a enlazar datos a la interfaz de usuario WPF. El archivo .edmx describe las relaciones y otros metadatos que se asocia a las clases de objetos en la base de datos.  Los archivos .tt son plantillas T4 que generan el código y que operan en el modelo y guardar los cambios en la base de datos. Puede ver todos estos archivos en el Explorador de soluciones bajo el nodo Northwind_model:  
  
    ![Archivos de modelo de EF del explorador de soluciones](../data-tools/media/raddata-solution-explorer-ef-model-files.png "raddata archivos de modelo de EF del explorador de soluciones")  
  
    La superficie del diseñador para el archivo .edmx le permite modificar algunas propiedades y relaciones en el modelo. No vamos a usar el Diseñador de este tutorial.  
  
6. Los archivos .tt son de uso general y es necesario ajustar uno de ellos para que funcione con el enlace de datos WPF, lo que requiere ObservableCollections.  En el Explorador de soluciones, expanda el nodo Northwind_model hasta que encuentre Northwind_model.tt. (Asegúrese de que están **no** en el *. Contexto archivo .tt que está directamente bajo el archivo .edmx).  
  
   -   Reemplace las dos repeticiones de <xref:System.Collections.ICollection> con <xref:System.Collections.ObjectModel.ObservableCollection%601>.  
  
   -   Reemplace la primera aparición de <xref:System.Collections.Generic.HashSet%601> con <xref:System.Collections.ObjectModel.ObservableCollection%601> alrededor de la línea 51. No reemplazar la segunda aparición de HashSet  
  
   -   Reemplazar la aparición única de <xref:System.Collections.Generic> (alrededor de la línea 334) con <xref:System.Collections.ObjectModel>.  
  
7. Presione **Ctrl + Mayús + B** para compilar el proyecto. Cuando finalice la compilación, las clases del modelo son visibles para el Asistente para orígenes de datos.  
  
   Ahora estamos preparados enlazar este modelo a la página XAML para que podemos ver, navegar y modificar los datos.  
  
## <a name="databind-the-model-to-the-xaml-page"></a>Enlazar datos en el modelo a la página XAML  
 Es posible escribir su propio código de enlace de datos, pero resulta mucho más fácil permitir que Visual Studio lo haga por usted.  
  
1.  En el menú principal, elija **proyecto &#124; Agregar nuevo origen de datos** para que aparezca el **Asistente para configuración de origen de datos**. Elija **objeto** porque estamos enlazando a las clases de modelo, no a la base de datos:  
  
     ![Asistente para configuración de origen de datos con objeto de origen](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png "raddata Asistente para configuración de origen de datos con objeto de origen")  
  
2.  Seleccione un cliente.  (Los orígenes para los pedidos se generará automáticamente desde la propiedad de navegación de pedidos de cliente.)  
  
     ![Agregar clases de entidad como orígenes de datos](../data-tools/media/raddata-add-entity-classes-as-data-sources.png "raddata Agregar entidad clases como orígenes de datos")  
  
3.  Haga clic en **finalizar**  
  
4.  Vaya a MainWindow.xaml en la vista código. Vamos a mantener el XAML muy sencillo para los fines de este ejemplo. Cambiar el título de MainWindow a algo más descriptivo y aumentar el alto y ancho a 800 x 600 por ahora. Siempre puede cambiar más adelante. Ahora, agregue estas definiciones de tres filas a la cuadrícula principal, una fila para los botones de navegación, uno de los detalles del cliente, uno para la cuadrícula que muestra los pedidos:  
  
    ```xaml  
    <Grid.RowDefinitions>  
               <RowDefinition Height="auto"/>  
               <RowDefinition Height="auto"/>  
               <RowDefinition Height="*"/>  
           </Grid.RowDefinitions>  
    ```  
  
5.  Ahora abra MainWindow.xaml por lo que está viendo en el diseñador. Esto hará que la ventana de orígenes de datos que aparezca como una opción en el margen de la ventana de Visual Studio junto al cuadro de herramientas. Haga clic en la pestaña para abrir la ventana, o presione else **Mayús + Alt + D** o elija **vista &#124; Other Windows &#124; orígenes de datos**. Vamos a mostrar cada propiedad de la clase de los clientes en su propio cuadro de texto individuales. En primer lugar, haga clic en la flecha en el cuadro combinado de clientes y elija **detalles**. A continuación, arrastre el nodo a la parte central de la superficie de diseño para que sepa que el diseñador que desee que aparezca en la fila central.  Si se pierde, puede especificar la fila manualmente más adelante en el XAML. De forma predeterminada, los controles se colocan verticalmente en un elemento de cuadrícula, pero en este momento puede organizarlos como desee en el formulario.  Por ejemplo, tendría sentido para colocar el cuadro de texto Nombre de la parte superior, por encima de la dirección. La aplicación de ejemplo para este artículo reordena los campos y ellos reorganiza en dos columnas.  
  
     ![Enlace de origen de datos de los clientes a controles individuales](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png "raddata enlace de origen de datos de los clientes a controles individuales")  
  
     En la vista de código, ahora puede ver un nuevo `Grid` elemento en la fila 1 (la fila central) de la cuadrícula principal. El elemento primario Grid tiene un `DataContext` atributo que hace referencia a CollectionViewSource que se ha agregado a la `Windows.Resources` elemento. Dado ese contexto de datos, cuando el primer cuadro de texto, por ejemplo, se asigna a ese nombre de "Address" se enlaza el `Address` propiedad actual `Customer` objeto en CollectionViewSource.  
  
    ```xaml  
    <Grid DataContext="{StaticResource customerViewSource}">  
    ```  
  
6.  Cuando un cliente está visible en la mitad superior de la ventana, queremos ver mitad sus pedidos en la parte inferior. Le mostraremos los pedidos en un control de vista de cuadrícula único. Para que el enlace de datos principal-detalle funcione según lo esperado, es importante que enlazamos a la propiedad Orders en la clase de los clientes, no para el nodo de pedidos independiente. Preste atención a la siguiente ilustración. Arrastre la propiedad Orders de la clase de los clientes a la mitad inferior del formulario, para que el diseñador lo coloca en la fila 2:  
  
     ![Arrastre las clases de pedidos como cuadrícula](../data-tools/media/raddata-drag-orders-classes-as-grid.png "raddata pedidos arrastrar clases como cuadrícula")  
  
7.  Visual Studio ha generado todo el código de enlace que se conecta a los controles de interfaz de usuario a los eventos en el modelo. Todo lo que necesitamos hacer para ver algunos datos, consiste en escribir código para rellenar el modelo. Primero vamos a navegar a MainWindow.xaml.cs y agregue un miembro de datos a la clase MainWindow para el contexto de datos. Este objeto, que se ha generado para nosotros, actúa algo parecido a un control que realiza el seguimiento de cambios y eventos en el modelo. Mientras estamos aquí, vamos a agregar a dos miembros que se usará más adelante para agregar un nuevo cliente o un pedido nuevo. También vamos a agregar la lógica de inicialización del constructor. La parte superior de la clase debe tener este aspecto:  
  
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
  
     Agregar un `using` System.Data.Entity poner el método de extensión de la carga en el ámbito de directiva:  
  
    ```csharp  
    using System.Data.Entity;  
    ```  
  
     Ahora, desplácese hacia abajo y busque el controlador de eventos Window_Loaded. Tenga en cuenta que Visual Studio ha agregado un objeto CollectionViewSource para nosotros. Representa el objeto NorthwindEntities que hemos seleccionado cuando se creó el modelo. Vamos a agregar código a Window_loaded para que todo el método ahora este aspecto:  
  
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
  
8.  Presione **F5**. Debería ver los detalles para el primer cliente que se recuperó en CollectionViewSource y sus pedidos en la cuadrícula de datos. El formato no es excelente, así que vamos a corregir que. crear una forma de ver los demás registros y realizar operaciones CRUD básicas.  
  
## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>Ajustar el diseño de página y agregue las cuadrículas para clientes y pedidos nuevos  
 La organización predeterminada generada por Visual Studio no es ideal para nuestra aplicación, por lo que haremos algunos cambios manualmente en el XAML. También necesitamos algunas "forms" (que son realmente las cuadrículas) para permitir al usuario agregar un nuevo cliente o un pedido nuevo.    Para poder agregar un nuevo cliente y un pedido, necesitamos un conjunto independiente de los cuadros de texto que no están enlazados a datos a la `CollectionViewSource`. Se deberá controlar qué ve el usuario en cualquier momento estableciendo la propiedad Visible en los métodos de control de cuadrícula.  
  
 Por último, agregaremos un botón Eliminar para cada fila de la cuadrícula de pedidos para que los usuarios eliminar un pedido individual.  
  
 En primer lugar, agregue estos estilos a Windows.Resources:  
  
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
 En las aplicaciones de Windows Forms, obtener un objeto de BindingNavigator con botones para navegar por las filas de una base de datos y realizar operaciones CRUD básicas. WPF no proporciona un BindingNavigator pero son bastante fáciles de realizar. Haremos esto con botones dentro de un elemento StackPanel horizontal en la fila inferior de la cuadrícula de página y se asociará los botones de comandos que están enlazados a los métodos en el código subyacente.  
  
 Hay partes cuatros a la lógica de comando: (1) los comandos, (2) los enlaces, (3) los botones y (4) los controladores de comandos en el código subyacente.  
  
#### <a name="add-commands-bindings-and-buttons-in-xaml"></a>Agregar comandos, enlaces y los botones en XAML  
  
1.  En primer lugar, vamos a agregar los comandos de nuestro archivo MainWindow.XAML dentro del elemento Windows.Resources:  
  
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
  
2.  Un elemento CommandBinding asigna un evento RoutedUICommand a un método en el código subyacente. Agregue este elemento CommandBindings después de la etiqueta de cierre de Windows.Resources:  
  
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
  
3.  Ahora vamos a agregar el elemento StackPanel con el panel de navegación, agregar, eliminar y actualizar los botones. En primer lugar, agregue este estilo a Windows.Resources:  
  
    ```xaml  
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">  
        <Setter Property="FontSize" Value="24"/>  
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>  
        <Setter Property="Margin" Value="2,2,2,0"/>  
        <Setter Property="Width" Value="40"/>  
        <Setter Property="Height" Value="auto"/>  
    </Style>  
    ```  
  
     Ahora puede pegar este código justo después RowDefinitions para el elemento de cuadrícula exterior hacia la parte superior de la página XAML:  
  
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
  
1.  El código subyacente es mínimo, excepto los métodos add y delete. Tenga en cuenta que el panel de navegación se realiza llamando a métodos en la propiedad de la vista de CollectionViewSource. La DeleteOrderCommandHandler muestra cómo realizar una eliminación en cascada de un pedido. Se debe eliminar primero el Order_Details que están asociados con ella. El UpdateCommandHandler agrega a un nuevo cliente a la colección, o bien actualiza solo el objeto existente con lo que los cambios realizados en los cuadros de texto por el usuario.  
  
2.  Agregue estos métodos de controlador a la clase MainWindow de MainWindow.xaml.cs, si su CollectionViewSource para la tabla Customers tiene un nombre diferente, será necesario ajustar el nombre de cada uno de estos métodos:  
  
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
  
3.  Presione **F5**. Debería ver los datos y los botones de navegación deberían funcionar según lo previsto. Haga clic en "Confirmar" para agregar un nuevo cliente o un pedido para el modelo después de escribir los datos.  Haga clic en "Cancelar" para volver atrás en un nuevo formulario de cliente o un pedido nuevo sin guardar los cambios. Puede realizar modificaciones a los clientes y pedidos directamente en los cuadros de texto existentes, y esos cambios se escribirán en el modelo automáticamente.  
  
## <a name="see-also"></a>Vea también  
 [Visual Studio data tools para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md) [documentación de Entity Framework](https://msdn.microsoft.com/data/ee712907.aspx)
