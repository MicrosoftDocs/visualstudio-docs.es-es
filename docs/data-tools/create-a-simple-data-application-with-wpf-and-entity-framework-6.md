---
title: "Crear una aplicación de datos sencilla con WPF y Entity Framework 6 | Documentos de Microsoft"
ms.custom: 
ms.date: 08/22/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
ms.assetid: 65929fab-5d78-4e04-af1e-cf4957f230f6
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 24d6401cae58b0bede44519900f6d72bd77ab2a9
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>Crear una aplicación de datos sencilla con WPF y Entity Framework 6
Este tutorial muestra cómo crear una aplicación básica "formularios sobre datos" en Visual Studio con SQL Server LocalDB, la base de datos de Northwind, Entity Framework 6 y Windows Presentation Foundation. Muestra cómo realizar el enlace de datos básico con una vista de detalles principales, y tiene también una personalizada "enlace navegador" con botones para "Mover siguiente", "Mover anterior," "Mover al principio," "mover al final," "Actualizar" y "Eliminar".  
  
 En este artículo se centra en con herramientas de datos en Visual Studio y no intenta explicar las tecnologías subyacentes en cualquier nivel de profundidad. Se supone que tiene un conocimiento básico de XAML, Entity Framework y SQL. En este ejemplo no muestra también la arquitectura Model-View-View Model (MVVM), que es el estándar para las aplicaciones de WPF. Sin embargo, puede copiar este código en su propia aplicación MVVM con muy pocas modificaciones.  
  
## <a name="install-and-connect-to-northwind"></a>Instalar y conectar a Northwind  
Este ejemplo utiliza SQL Server Express LocalDB y la base de datos de ejemplo Northwind. Debe funcionar con otros productos de base de datos SQL igual de bien, si el proveedor de datos ADO.NET para ese producto es compatible con Entity Framework.  
  
1.  Si no tiene SQL Server Express LocalDB, puede instalarlo desde el [página de descarga de ediciones de SQL Server](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx), o a través del **instalador de Visual Studio**. El instalador de Visual Studio, se puede instalar SQL Server Express LocalDB como parte de la **desarrollo de escritorio de .NET** carga de trabajo, o como un componente individual.  
  
2.  Instalar la base de datos de ejemplo Northwind, siga estos pasos:  

    1. En Visual Studio, abra el **Explorador de objetos de SQL Server** ventana. (Explorador de objetos de SQL Server se instala como parte de la **almacenamiento de datos y el procesamiento** carga de trabajo en el instalador de Visual Studio.) Expanda el **SQL Server** nodo. Haga doble clic en la instancia de LocalDB y seleccione **nueva consulta...** .  

       Se abre una ventana del editor de consultas.  

    2. Copia la [script Transact-SQL de Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) en el Portapapeles. Este script de T-SQL crea la base de datos Northwind desde el principio y lo rellena con datos.  

    3. Pegue el script de T-SQL en el editor de consultas y, a continuación, elija la **Execute** botón.  

       Después de unos minutos, finaliza la ejecución de la consulta y se crea la base de datos Northwind.  
  
3.  [Agregar nuevas conexiones](../data-tools/add-new-connections.md) de Northwind.  
  
## <a name="configure-the-project"></a>Configuración del proyecto  
  
1.  En Visual Studio, elija **archivo**, **New**, **proyecto...**  y, a continuación, cree una nueva aplicación de WPF de C#.  
  
2.  A continuación se agregará el paquete NuGet para Entity Framework 6. En el Explorador de soluciones, seleccione el nodo del proyecto. En el menú principal, elija **proyecto**, **administrar paquetes de NuGet...**  
  
     ![Administrar el elemento de menú de paquetes de NuGet](../data-tools/media/raddata_vs2015_manage_nuget_packages.png "raddata_vs2015_manage_nuget_packages")  
  
3.  En el Administrador de paquetes de NuGet, haga clic en el **examinar** vínculo. Entity Framework es probablemente el paquete superior en la lista. Haga clic en **instalar** en el panel derecho y siga las indicaciones. La ventana de salida le indicará cuando finalice la instalación.  
  
     ![Paquete de NuGet de Entity Framework](../data-tools/media/raddata_vs2015_nuget_ef.png "raddata_vs2015_Nuget_EF")  
  
4.  Ahora podemos usar Visual Studio para crear un modelo basado en la base de datos Northwind.  
  
## <a name="create-the-model"></a>Crear el modelo  
  
1.  Haga clic con el botón secundario en el nodo de proyecto en el Explorador de soluciones y elija **agregar**, **nuevo elemento...** . En el panel izquierdo, bajo el nodo de C#, elija **datos** y en el panel central, elija **ADO.NET Entity Data Model**.  
  
     ![Entity Framework modelo nuevo elemento de proyecto](../data-tools/media/raddata-ef-new-project-item.png "raddata EF nuevo elemento de proyecto")  

  2.  Llame el modelo `Northwind_model` y haga clic en Aceptar. Se abrirá la **Entity Data Model Wizard**. Elija **EF Designer de base de datos** y, a continuación, haga clic en **siguiente**.  
  
     ![Modelo EF de base de datos](../data-tools/media/raddata-ef-model-from-database.png "raddata EF modelo de base de datos")  
  
3.  En la siguiente pantalla, elija su LocalDB Northwind conexión y haga clic en **siguiente**.  
  
4.  En la siguiente página del asistente, se elige qué tablas, procedimientos almacenados y otros objetos de base de datos que se incluirán en el modelo de Entity Framework. Expanda el nodo dbo en la vista de árbol y elija los clientes, pedidos y detalles de pedido. Deje las opciones predeterminadas y haga clic en **finalizar**.  
  
     ![Seleccione los objetos de base de datos para el modelo](../data-tools/media/raddata-choose-ef-objects.png "raddata elegir EF objetos")  
  
5.  El asistente genera las clases de C# que representan el modelo de Entity Framework. Se trata de clases C# anteriores sin formato y son lo que haremos enlazar datos a la interfaz de usuario WPF. El archivo .edmx describe las relaciones y otros metadatos que se asocia a las clases de objetos en la base de datos.  .Tt (archivos) son plantillas de T4 que generan el código que funcione en el modelo y guardar los cambios en la base de datos. Puede ver todos estos archivos en el Explorador de soluciones bajo el nodo Northwind_model:  

       ![Archivos de modelo de EF de explorador de soluciones](../data-tools/media/raddata-solution-explorer-ef-model-files.png "raddata archivos de modelo de EF de explorador de soluciones")  
  
     La superficie del diseñador para el archivo .edmx le permite modificar algunas propiedades y relaciones en el modelo. No vamos a usar el Diseñador de este tutorial.  
  
6.  .Tt (archivos) son de uso generales y necesitamos Retocar uno de ellos para que funcione con enlace de datos WPF, que requiere ObservableCollections.  En el Explorador de soluciones, expanda el nodo Northwind_model hasta que encuentre Northwind_model.tt. (Asegúrese de que está **no** en el *. Contexto archivo .tt que está directamente bajo el archivo .edmx).  
  
    -   Reemplace las dos apariciones de <xref:System.Collections.ICollection> con <xref:System.Collections.ObjectModel.ObservableCollection%601>.  
  
    -   Reemplace la primera aparición de <xref:System.Collections.Generic.HashSet%601> con <xref:System.Collections.ObjectModel.ObservableCollection%601> alrededor de la línea 51. No reemplaza la segunda aparición del objeto HashSet  
  
    -   Reemplazar la aparición única de <xref:System.Collections.Generic> (alrededor de línea 431) con <xref:System.Collections.ObjectModel>.  
  
7.  Presione **Ctrl + Mayús + B** para compilar el proyecto. Cuando finalice la compilación, las clases del modelo son visibles para el Asistente para orígenes de datos.  
  
Ahora estamos preparados para enlazar este modelo en la página XAML para que podamos ver, navegar y modificar los datos.  
  
## <a name="databind-the-model-to-the-xaml-page"></a>Enlazar el modelo en la página XAML  
 Es posible escribir su propio código de enlace de datos, pero es mucho más fácil dejar que Visual Studio lo haga por usted.  
  
1.  En el menú principal, elija **proyecto > Agregar nuevo origen de datos** para que aparezca el **Asistente para configuración de orígenes de datos**. Elija **objeto** porque estamos enlazando a las clases del modelo, no a la base de datos:  
  
     ![Asistente para la configuración de origen de datos con objeto de origen](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png "raddata Asistente para la configuración de origen de datos con objeto de origen")  
  
2.  Seleccione el cliente.  (Orígenes para los pedidos se generará automáticamente de la propiedad de navegación de pedidos de cliente.)  
  
     ![Agregar clases de entidad como orígenes de datos](../data-tools/media/raddata-add-entity-classes-as-data-sources.png "raddata Agregar entidad clases como orígenes de datos")  
  
3.  Haga clic en **finalizar**  
  
4.  Navegue a MainWindow.xaml en la vista código. Vamos a mantener el archivo XAML muy sencillo para los fines de este ejemplo. Cambiar el título de MainWindow a algo más descriptivo y aumentar su alto y ancho a 800 x 600 por ahora. Siempre puede cambiar más adelante. Agregue ahora estas definiciones de tres filas en la cuadrícula principal, una fila para los botones de navegación, uno de los detalles del cliente, uno para la cuadrícula que muestra sus pedidos:  

    ```xaml  
    <Grid.RowDefinitions>  
            <RowDefinition Height="auto"/>  
            <RowDefinition Height="auto"/>  
            <RowDefinition Height="*"/>  
        </Grid.RowDefinitions>
    ```

5.  Ahora abra MainWindow.xaml por lo que está viendo en el diseñador. Esto hará que la ventana de orígenes de datos para que aparezca como una opción en el margen de la ventana de Visual Studio junto al cuadro de herramientas. Haga clic en la ficha para abrir la ventana, o presione else **Mayús + Alt + D** o elija **vista &#124; Otras ventanas &#124; Orígenes de datos**. Vamos a visualizar cada propiedad en la clase de clientes en su propio cuadro de texto individuales. En primer lugar, haga clic en la flecha en el cuadro combinado de clientes y elija **detalles**. A continuación, arrastre el nodo de la parte central de la superficie de diseño para que el diseñador sepa que desee que aparezca en la fila del medio.  Si ha extraviado, puede especificar la fila manualmente más adelante en el código XAML. De forma predeterminada, los controles se colocan verticalmente en un elemento de cuadrícula, pero en este momento puede organizarlas como prefiera en el formulario.  Por ejemplo, tendría sentido para colocar el cuadro de texto nombre en la parte superior, por encima de la dirección. La aplicación de ejemplo de este artículo reordena los campos y vuelve a ellos en dos columnas.  
  
     ![Enlace de origen de datos de los clientes a controles individuales](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png "raddata enlace de origen de datos de los clientes a controles individuales")  
  
     En la vista de código, ahora puede ver un nuevo `Grid` elemento en la fila 1 (la fila del medio) de la cuadrícula principal. El elemento primario cuadrícula tiene un `DataContext` atributo que hace referencia a un CollectionViewSource que se ha agregado a la `Windows.Resources` elemento. Dado ese contexto de datos, cuando el primer cuadro de texto, por ejemplo, se enlaza a "Address" ese nombre está asignado a la `Address` propiedad actual `Customer` objeto en CollectionViewSource.  
  
    ```xaml  
    <Grid DataContext="{StaticResource customerViewSource}">  
    ```  

6.  Cuando un cliente está visible en la mitad superior de la ventana, en el que quiere ver sus pedidos en la parte inferior de medio. Vamos a mostrarle los pedidos en un control de vista de cuadrícula único. Para que el enlace de datos de principal-detalle funcionen según lo previsto, es importante que se enlaza con la propiedad de pedidos en la clase de clientes, no para el nodo de pedidos independiente. Preste atención a la siguiente ilustración. Arrastre la propiedad de pedidos de la clase de los clientes a la mitad inferior del formulario, para que el diseñador lo coloca en la fila 2:  
  
     ![Arrastre las clases de pedidos como cuadrícula](../data-tools/media/raddata-drag-orders-classes-as-grid.png "raddata arrastre pedidos clases como cuadrícula")  
  
7.  Todo el código de enlace que se conecta a los controles de interfaz de usuario a los eventos en el modelo generado por Visual Studio. Lo que debemos hacer para ver algunos datos, consiste en escribir código para rellenar el modelo. Primero vamos a navegar al MainWindow.xaml.cs y agregar un miembro de datos a la clase MainWindow para el contexto de datos. Este objeto, que se ha generado para que podamos, actúa algo parecido a un control que realiza el seguimiento de cambios y los eventos en el modelo. También vamos a agregar la lógica de inicialización del constructor. La parte superior de la clase debe tener este aspecto:  
  
     [!code-csharp[MainWindow#1](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#1)]  
     
     Agregar un `using` directivas para System.Data.Entity devolver el método de extensión de la carga en el ámbito:  
  
     ```csharp
     using System.Data.Entity;  
     ```  

     Ahora, desplácese hacia abajo y busque el controlador de eventos Window_Loaded. Tenga en cuenta que Visual Studio ha agregado un objeto CollectionViewSource para nosotros. Representa el objeto NorthwindEntities que se seleccionó cuando se creó el modelo. Vamos a agregar código a Window_Loaded por lo que todo el método ahora tenga un aspecto similar al siguiente:  

     [!code-csharp[Window_Loaded#2](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#2)]  

8.  Presione **F5**. Debe ver los detalles para el primer cliente que se recuperó en CollectionViewSource. También debe ver sus pedidos en la cuadrícula de datos. El formato no es grande, así que vamos a corregir que. También creará una forma para ver los demás registros y realizar operaciones CRUD básicas.  
  
## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>Ajustar el diseño de página y agregue cuadrículas para pedidos y nuevos clientes  
La organización predeterminada generada por Visual Studio no es ideal para nuestra aplicación, por lo que nos aseguraremos de hacer algunos cambios manualmente en el código XAML. También necesitamos algunos "forms" (que son realmente cuadrículas) para permitir al usuario agregar un nuevo cliente o un pedido. Para poder agregar un nuevo cliente y del pedido, necesitamos un conjunto independiente de los cuadros de texto que no están enlazados a datos a la `CollectionViewSource`. Se podrá controlar qué ve el usuario en cualquier momento estableciendo la propiedad Visible en los métodos de control de cuadrícula. Por último, se agregará un botón Eliminar para cada fila de la cuadrícula de pedidos para permitir al usuario eliminar un pedido individual.  
  
En primer lugar, agregue estos estilos para el elemento Windows.Resources en MainWindow.xaml:  
  
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
  
A continuación, reemplace toda la cuadrícula externo con este formato:  
  
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
 En las aplicaciones de Windows Forms, se obtiene un objeto de BindingNavigator con botones para desplazarse por filas en una base de datos y realizar operaciones CRUD básicas. WPF no proporciona un BindingNavigator, pero es fácil crear uno. Haremos con botones dentro de un elemento StackPanel horizontal y se asociará los botones con los comandos que están enlazados a los métodos en el código subyacente.  
  
 Consta de cuatro partes la lógica de comando: (1) los comandos, (2) los enlaces, (3) los botones y (4) los controladores de comando en el código subyacente.  
  
#### <a name="add-commands-bindings-and-buttons-in-xaml"></a>Agregue comandos, enlaces y botones en XAML  
  
1.  En primer lugar, vamos a agregar los comandos en el archivo MainWindow.xaml dentro del elemento Windows.Resources:  
  
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
  
3.  Ahora vamos a agregar la StackPanel con el panel de navegación, agregar, eliminar y actualizar botones. En primer lugar, agregue este estilo a Windows.Resources:  
  
    ```xaml  
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">  
        <Setter Property="FontSize" Value="24"/>  
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>  
        <Setter Property="Margin" Value="2,2,2,0"/>  
        <Setter Property="Width" Value="40"/>  
        <Setter Property="Height" Value="auto"/>  
    </Style>  
    ```  
  
     En segundo lugar, pegue este código justo después de la RowDefinitions para el elemento de cuadrícula exterior, hacia la parte superior de la página XAML:  
  
    ```xaml  
    <StackPanel Orientation="Horizontal" Margin="2,2,2,0" Height="36" VerticalAlignment="Top" Background="Gainsboro" DataContext="{StaticResource customerViewSource}" d:LayoutOverrides="LeftMargin, RightMargin, TopMargin, BottomMargin">  
        <Button Name="btnFirst" Content="|◄" Command="{StaticResource FirstCommand}" Style="{StaticResource NavButton}"  />  
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
  
#### <a name="add-command-handlers-to-the-mainwindow-class"></a>Agregar controladores de comandos a la clase MainWindow  
  
El código subyacente es mínimo excepto para los métodos add y delete. Navegación se realiza mediante una llamada a métodos en la propiedad de la vista de CollectionViewSource. La DeleteOrderCommandHandler muestra cómo realizar una eliminación en cascada en un pedido. Tenemos que eliminar primero el Order_Details que están asociadas a ella. El UpdateCommandHandler agrega un nuevo cliente o un pedido a la colección, o bien actualiza solo un cliente existente o un pedido con los cambios realizados por el usuario en los cuadros de texto.  
  
Agregar estos métodos de controlador a la clase MainWindow de MainWindow.xaml.cs. Si su CollectionViewSource para la tabla Customers tiene un nombre diferente, debe ajustar el nombre de cada uno de estos métodos:  
  
[!code-csharp[CommandHandlers#3](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#3)]  
  
## <a name="run-the-application"></a>Ejecutar la aplicación
Para iniciar la depuración, presione **F5**. Debería ver datos de clientes y pedidos rellena en la cuadrícula y los botones de navegación deberían funcionar según lo esperado. Haga clic en "Confirmación" para agregar un nuevo cliente o un pedido para el modelo después de escribir los datos. Haga clic en "Cancelar" para revertir un cliente nuevo o un nuevo formulario de pedido sin guardar los datos. Puede realizar modificaciones en los clientes existentes y pedidos directamente en los cuadros de texto, y esos cambios se escriben en el modelo automáticamente.  
  
## <a name="see-also"></a>Vea también
[Visual Studio Data Tools para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)  
[Documentación de Entity Framework](https://msdn.microsoft.com/en-us/data/ee712907.aspx)