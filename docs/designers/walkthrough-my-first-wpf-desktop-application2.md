---
title: "Tutorial: Mi primera aplicación de escritorio WPF | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3c460fa9-2ea1-413f-ae54-54a1f2a499d1
caps.latest.revision: "6"
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs:
- csharp
- vb
ms.openlocfilehash: 75a333c7e5948e13db0c0c91b41128914e23222b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a>Tutorial: Mi primera aplicación de escritorio WPF
Este tutorial proporciona una introducción al desarrollo en Windows Presentation Foundation (WPF). Podrá crear una aplicación básica que incluya los elementos que son comunes a la mayoría de las aplicaciones de escritorio WPF: marcado XAML, código subyacente, definiciones de aplicación, controles, diseño, enlace de datos y estilos.  
  
## <a name="creating-the-application-project"></a>Creación del proyecto de la aplicación  
En esta sección, creará la infraestructura de la aplicación, que incluye el proyecto y una ventana principal o formulario.  
  
#### <a name="to-create-the-project"></a>Para crear el proyecto  
  
1.  En la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
2.  En el cuadro de diálogo **Nuevo proyecto** , expanda el nodo **Visual C#** o **Visual Basic** y elija el nodo **Windows** . A continuación, expanda el nodo **Windows** y elija **Escritorio clásico** .  
  
3.  En la lista de plantillas, elija la plantilla **Aplicación WPF** .  
  
4.  En el cuadro de diálogo **Nombre** , escriba `ExpenseIt`y elija el botón **Aceptar** .  
  
     El proyecto se creará, se agregarán los archivos del proyecto al **Explorador de soluciones**y se mostrará el diseñador de la ventana de aplicación predeterminada denominado **MainWindow.xaml** .  
  
#### <a name="to-modify-the-main-window"></a>Para modificar la ventana principal  
  
1.  En el diseñador, seleccione la pestaña **MainWindow.xaml** en caso de que todavía no sea la pestaña del diseñador activa.  
  
2.  Si va a usar C#, busque la línea `<Window x:Class="ExpenseIt.MainWindow"` y sustitúyala por `<NavigationWindow x:Class="ExpenseIt.MainWindow"`.  
  
     Si va a usar Visual Basic, busque la línea `<Window x:Class=" MainWindow"` y sustitúyala por `<NavigationWindow x:Class="MainWindow"`.  
  
     Tenga en cuenta que al cambiar la etiqueta `<Window` a `<NavigationWindow`, Intellisense cambiará automáticamente la etiqueta de cierre a `</NavigationWindow>` también.  
  
    > [!NOTE]
    >  Después de cambiar la etiqueta, si la ventana **Lista de errores** está abierta, es posible que encuentre varios errores. No se preocupe, los cambios que realizará en los próximos pasos hará que desaparezcan.  
  
3.  Elija las etiquetas `<Grid>` y `</Grid>` y elimínelas.  
  
     **NavigationWindow** no puede contener otros elementos de interfaz de usuario como, por ejemplo, una **cuadrícula**.  
  
4.  En el cuadro de diálogo **Propiedades** , expanda el nodo de categoría **Común** y elija la propiedad **Título** . A continuación, escriba `ExpenseIt` y presione la tecla **Entrar** .  
  
     Tenga en cuenta que el elemento **Título** de la ventana XAML cambia para que coincida con el nuevo valor. Puede modificar las propiedades XAML en la ventana XAML o en la ventana **Propiedades** para que se sincronicen los cambios.  
  
5.  En la ventana XAML, establezca el valor del elemento **Alto** en `375`y establezca el valor de la propiedad **Ancho** en `500`.  
  
     Estos elementos corresponden a las propiedades **Alto** y **Ancho** , que se encuentran en la categoría **Diseño** en la ventana **Propiedades** .  
  
     El archivo **MainWindow.xaml** debe tener el aspecto siguiente en C#:  
  
    ```xaml  
    <NavigationWindow x:Class="ExpenseIt.MainWindow"  
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
            xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
            xmlns:local="clr-namespace:ExpenseIt"  
            mc:Ignorable="d"  
            Title="ExpenseIt" Height="375" Width="500">    
    </NavigationWindow>  
    ```  
  
     O este aspecto en Visual Basic:  
  
    ```xaml  
    <NavigationWindow x:Class="MainWindow"  
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
            xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
            xmlns:local="clr-namespace:ExpenseIt"  
            mc:Ignorable="d"  
            Title="ExpenseIt" Height="375" Width="500">    
    </NavigationWindow>  
    ```  
  
#### <a name="to-modify-the-code-behind-file-c"></a>Para modificar el archivo de código subyacente (C#):  
  
1.  En el **Explorador de soluciones**, expanda el nodo **MainWindow.xaml** y abra el archivo **MainWindow.xaml.cs** .  
  
2.  Busque la línea `public partial class MainWindow : Window` y sustitúyala por `public partial class MainWindow : NavigationWindow`.  
  
     Esto cambia la clase `MainWindow` para que se derive de `NavigationWindow`. En Visual Basic, esto sucede automáticamente cuando se cambia la ventana en XAML, por lo que no es necesario ningún cambio de código.  
  
## <a name="adding-files-to-the-application"></a>Adición de archivos a la aplicación  
 En esta sección, agregará dos páginas y una imagen a la aplicación.  
  
#### <a name="to-add-a-home-screen"></a>Para agregar una pantalla principal  
  
1.  En el **Explorador de soluciones**, abra el menú contextual del nodo **Expenselt** y elija **Agregar**, **Página**.  
  
2.  En el cuadro de diálogo **Agregar nuevo elemento** , elija el cuadro de texto **Nombre** y escriba `ExpenseItHome`y elija el botón **Agregar** .  
  
     Esta página es la primera ventana que se muestra cuando se inicia la aplicación.  
  
3.  En el diseñador, seleccione la pestaña **ExpenseItHome** en caso de que todavía no sea la pestaña del diseñador activa.  
  
4.  Seleccione el elemento `<Title>` y cambie el título a **ExpenseIt – Inicio**.  
  
     El archivo **MainWindow.xaml** deberá tener el aspecto siguiente en C#:  
  
    ```xaml  
    <Page x:Class="ExpenseIt.ExpenseItHome"  
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"   
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"   
          xmlns:local="clr-namespace:ExpenseIt"  
          mc:Ignorable="d"   
          d:DesignHeight="300" d:DesignWidth="300"  
          Title="ExpenseIt - Home">    
        <Grid>  
  
        </Grid>  
    </Page>  
    ```  
  
    En Visual Basic, la primera línea será ligeramente diferente:  
  
    ```xaml  
    <Page x:Class="ExpenseItHome"  
    ```  
  
5.  En el diseñador, elija la pestaña **MainWindow.xaml** .  
  
6.  Busque la línea del elemento `Title="ExpenseIt" Height="375" Width="500">` y agregue una propiedad `Source="ExpenseItHome.xaml"` .  
  
     Esto establece **ExpenseItHome.xaml** como la primera página que se abre al iniciar la aplicación. El archivo **MainWindow.xaml** debe tener el aspecto siguiente en C#:  
  
    ```xaml  
    <NavigationWindow x:Class="ExpenseIt.MainWindow"  
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
            xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
            xmlns:local="clr-namespace:ExpenseIt"  
            mc:Ignorable="d"  
            Title="ExpenseIt" Height="375" Width="500" Source="ExpenseItHome.xaml">    
    </NavigationWindow>  
    ```  
  
    En Visual Basic, la primera línea será ligeramente diferente:  
  
    ```xaml  
    <NavigationWindow x:Class="MainWindow"
    ```  
  
     Al igual que sucede con las propiedades establecidas anteriormente, podría haber establecido la propiedad `Source` en la categoría **Varios** de la ventana **Propiedades** .  
  
#### <a name="to-add-a-details-window"></a>Para agregar una ventana de detalles  
  
1.  En el **Explorador de soluciones**, abra el menú contextual del nodo **Expenselt** y elija **Agregar**, **Página**.  
  
2.  En el cuadro de diálogo **Agregar nuevo elemento** , elija el cuadro de texto **Nombre** y escriba `ExpenseReportPage`y elija el botón **Agregar** .  
  
     Esta ventana muestra un informe de gastos individuales.  
  
3.  En el diseñador, seleccione la pestaña **ExpenseReportPage.xaml** en caso de que todavía no sea la pestaña del diseñador activa.  
  
4.  Seleccione el elemento `<Title>` y cambie el título a **ExpenseIt – Ver gastos**.  
  
     El archivo ExpenseReportPage.xaml deberá tener el aspecto siguiente en C#:  
  
    ```xaml  
    <Page x:Class="ExpenseIt.ExpenseReportPage"  
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"   
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"   
          xmlns:local="clr-namespace:ExpenseIt"  
          mc:Ignorable="d"   
          d:DesignHeight="300" d:DesignWidth="300"  
          Title="ExpenseIt - View Expense">    
        <Grid>  
  
        </Grid>  
    </Page>  
    ```  
  
    En Visual Basic, la primera línea será ligeramente diferente:  
  
    ```xaml  
    <Page x:Class="ExpenseReportPage"  
    ```  
  
5.  En la barra de menús, elija **Depurar**, **Iniciar depuración** (o presione F5) para ejecutar la aplicación.  
  
     La ilustración siguiente muestra la aplicación con los botones de la ventana de navegación.  
  
     ![Captura de pantalla de ejemplo ExpenseIt](../designers/media/gettingstartedfigure1.png "GettingStartedFigure1")  
  
6.  Cierre la aplicación para volver al modo de diseño.  
  
## <a name="creating-the-user-interface"></a>Crear la interfaz de usuario  
 Diseño permite colocar los elementos de forma ordenada y administrar el tamaño y la posición de dichos elementos cuando se cambia el tamaño de un formulario. En esta sección, creará una cuadrícula de una sola columna con tres filas. Podrá agregar controles a las dos páginas, código y finalmente definir estilos para los controles que se pueden volver a usar.  
  
#### <a name="to-create-the-layout"></a>Para crear el diseño  
  
1.  Abra **ExpenseItHome.xaml** y elija el elemento `<Grid>` .  
  
2.  En el cuadro de diálogo **Propiedades** , expanda el nodo de categoría **Diseño** y establezca los valores de **Margen** en `10`, `10`, `0`y `10`, que corresponden a los márgenes izquierdo, derecho, superior e inferior.  
  
     El elemento `Margin="10,0,10,10"` se agrega al elemento `<Grid>` en el XAML. Una vez más, podría haber escrito estos valores directamente en el código XAML en lugar de en la ventana **Propiedades** con el mismo resultado.  
  
3.  Agregue el siguiente código XAML al elemento `Grid` para crear las definiciones de fila y columna:  
  
    ```xaml  
    <Grid.ColumnDefinitions>  
        <ColumnDefinition />  
    </Grid.ColumnDefinitions>  
    <Grid.RowDefinitions>  
        <RowDefinition Height="Auto"/>  
        <RowDefinition />  
        <RowDefinition Height="Auto"/>  
    </Grid.RowDefinitions>  
    ```  
  
#### <a name="to-add-controls"></a>Para agregar controles  
  
1.  Abra **ExpenseItHome.xaml**.  
  
2.  Agregue el código XAML siguiente justo encima de la etiqueta `</Grid>` para crear los controles `Border`, `ListBox` y `Button`:  
  
    ```xaml  
    <!-- People list -->  
      <Border Grid.Column="0" Grid.Row="0" Height="35" Padding="5" Background="#4E87D4">  
          <Label VerticalAlignment="Center" Foreground="White">Names</Label>  
      </Border>  
      <ListBox Name="peopleListBox" Grid.Column="0" Grid.Row="1">  
          <ListBoxItem>Mike</ListBoxItem>  
          <ListBoxItem>Lisa</ListBoxItem>  
          <ListBoxItem>John</ListBoxItem>  
          <ListBoxItem>Mary</ListBoxItem>  
      </ListBox>  
  
      <!-- View report button -->  
      <Button Grid.Column="0" Grid.Row="2" Margin="0,10,0,0" Width="125"  
    Height="25" HorizontalAlignment="Right">View</Button>    
    ```  
  
     Tenga en cuenta que los controles aparecen en la ventana de diseño. Podría también haber creado los controles arrastrándolos desde la ventana **Cuadro de herramientas** a la ventana de diseño y establecer sus propiedades en la ventana **Propiedades** .  
  
3.  Compile y ejecute la aplicación. La siguiente ilustración muestra el aspecto de tiempo de ejecución de los controles creados por el código XAML en este procedimiento.  
  
     ![Captura de pantalla de ejemplo ExpenseIt](../designers/media/gettingstartedfigure2.png "GettingStartedFigure2")  
  
4.  Cierre la aplicación para volver al modo de diseño.  
  
#### <a name="to-add-a-background-image"></a>Para agregar una imagen de fondo  
  
1.  Elija la siguiente imagen y guárdela como `watermark.png`.  
  
     ![Marca de agua de tutorial](../designers/media/wpf_watermark.png "WPF_watermark")  
  
    > [!NOTE]
    >  O bien, puede crear su propia imagen y guardarla como `watermark.png`.  
  
2.  En el **Explorador de soluciones**, abra el menú contextual del nodo **Expenselt** y elija **Agregar**, **Elemento existente**.  
  
3.  En el cuadro de diálogo **Agregar elemento existente** , busque la imagen **watermark.png** que acaba de agregar, selecciónela y, a continuación, elija el botón **Agregar** .  
  
    > [!NOTE]
    >  Es posible que necesite expandir la lista **Tipos de archivo** y elegir **Archivos de imagen**.  
  
4.  Abra el archivo **ExpenseItHome.xaml** y agregue el siguiente código XAML justo encima de la etiqueta `</Grid>` para crear una imagen de fondo:  
  
    ```xaml  
    <Grid.Background>  
        <ImageBrush ImageSource="watermark.png"/>  
    </Grid.Background>    
    ```  
  
#### <a name="to-add-a-title"></a>Para agregar un título  
  
1.  Abra **ExpenseItHome.xaml**.  
  
2.  Busque la línea `<Grid.ColumnDefinitions>` y agregue lo siguiente justo debajo de ella:  
  
    ```xaml  
    <ColumnDefinition Width="230" />    
    ```  
  
     Esto crea una columna adicional a la izquierda de las demás columnas con un ancho fijo de 230 píxeles.  
  
3.  Busque la línea `<Grid.RowDefinitions>` y agregue lo siguiente justo debajo de ella:  
  
    ```xaml  
    <RowDefinition />    
    ```  
  
     Esto agrega una fila a la parte superior de la cuadrícula.  
  
4.  Mover los controles a la segunda columna estableciendo el valor `Grid.Column` en 1. Baje cada control una fila aumentando cada valor `Grid.Row` en 1.  
  
    1.  Busque la línea `<Border Grid.Column="0" Grid.Row="0" Height="35" Padding="5" Background="#4E87D4">`. Cambie `Grid.Column="0"` a `Grid.Column="1"` y cambie `Grid.Row="0"` a `Grid.Row="1"`.  
  
    2.  Busque la línea `<ListBox Name="peopleListBox" Grid.Column="0" Grid.Row="1"`. Cambie `Grid.Column="0"` a `Grid.Column="1"` y cambie `Grid.Row="1"` a `Grid.Row="2"`.  
  
    3.  Busque la línea `<Button Grid.Column="0" Grid.Row="2" Margin="0,10,0,0" Width="125"`. Cambie `Grid.Column="0"` a `Grid.Column="1"` y cambie `Grid.Row="2"` a `Grid.Row="3"`.  
  
5.  Justo antes del elemento `<Border` , agregue el siguiente código XAML para mostrar el título:  
  
    ```xaml  
    <Label Grid.Column="1" VerticalAlignment="Center" FontFamily="Trebuchet MS"   
            FontWeight="Bold" FontSize="18" Foreground="#0066cc">  
        View Expense Report  
    </Label>    
    ```  
  
     El contenido del archivo **MainWindow.xaml** deberá tener un aspecto similar al siguiente en C#:  
  
    ```xaml  
    <Page x:Class="ExpenseIt.ExpenseItHome"  
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"   
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"   
          xmlns:local="clr-namespace:ExpenseIt"  
          mc:Ignorable="d"   
          d:DesignHeight="300" d:DesignWidth="300"  
          Title="ExpenseIt - Home">  
        <Grid Margin="10,0,10,10">  
            <Grid.ColumnDefinitions>  
                <ColumnDefinition Width="230" />  
                <ColumnDefinition />  
            </Grid.ColumnDefinitions>  
            <Grid.RowDefinitions>  
                <RowDefinition />  
                <RowDefinition Height="Auto"/>  
                <RowDefinition />  
                <RowDefinition Height="Auto"/>  
            </Grid.RowDefinitions>  
            <Border Grid.Column="1" Grid.Row="1" Height="35" Padding="5" Background="#4E87D4">  
                <Label VerticalAlignment="Center" Foreground="White">Names</Label>  
            </Border>  
            <!-- People list -->  
            <Label Grid.Column="1" VerticalAlignment="Center" FontFamily="Trebuchet MS"   
            FontWeight="Bold" FontSize="18" Foreground="#0066cc">  
                View Expense Report  
            </Label>  
            <ListBox Name="peopleListBox" Grid.Column="1" Grid.Row="2">  
                <ListBoxItem>Mike</ListBoxItem>  
                <ListBoxItem>Lisa</ListBoxItem>  
                <ListBoxItem>John</ListBoxItem>  
                <ListBoxItem>Mary</ListBoxItem>  
            </ListBox>  
  
            <!-- View report button -->  
            <Button Grid.Column="1" Grid.Row="3" Margin="0,10,0,0" Width="125"  
    Height="25" HorizontalAlignment="Right">View</Button>  
            <Grid.Background>  
                <ImageBrush ImageSource="watermark.png"/>  
            </Grid.Background>  
        </Grid>  
    </Page>  
    ```  
  
    En Visual Basic, la primera línea será ligeramente diferente:  
  
    ```xaml  
    <Page x:Class="ExpenseItHome"  
    ```  
  
6.  Si compila y ejecuta la aplicación en este punto, debería ser similar a la siguiente ilustración:  
  
     ![Captura de pantalla de ejemplo ExpenseIt](../designers/media/gettingstartedfigure3.png "GettingStartedFigure3")  
  
#### <a name="to-add-code-to-the-button"></a>Para agregar el código al botón  
  
1.  Abra **ExpenseItHome.xaml**.  
  
2.  Elija el elemento `Button` y agregue el código XAML siguiente inmediatamente después del elemento `HorizontalAlignment="Right"`: `Click="Button_Click"`.  
  
     Esto agrega un controlador de eventos para el evento `Click` del botón. El código del elemento **Button** debe tener el siguiente aspecto:  
  
    ```xaml  
    <!-- View report button -->  
      <Button Grid.Column="1" Grid.Row="3" Margin="0,10,0,0" Width="125"  
    Height="25" HorizontalAlignment="Right" Click="Button_Click">View</Button>  
    ```  
  
3.  Abra el archivo **ExpenseItHome.xaml.cs** o **ExpenseItHome.xaml.vb** .  
  
4.  Agregue el código siguiente a la clase `ExpenseItHome` :  
  
    ```csharp  
    private void Button_Click(object sender, RoutedEventArgs e)  
    {  
        // View Expense Report  
        ExpenseReportPage expenseReportPage = new ExpenseReportPage();  
        this.NavigationService.Navigate(expenseReportPage);    
    }  
    ```  
  
    ```vb  
    Private Sub Button_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)  
        ' View Expense Report  
        Dim expenseReportPage As New ExpenseReportPage()  
    Me.NavigationService.Navigate(expenseReportPage)  
    End Sub  
    ```  
  
     Este controlador de eventos abre la página de informe de gastos al hacer clic en el botón.  
  
#### <a name="to-create-the-ui-for-the-report-page"></a>Para crear la interfaz de usuario para la página de informes  
  
1.  Abra el archivo **ExpenseReportPage.xaml**.  
  
     Esta página mostrará el informe de gastos de la persona que está seleccionada en la página de inicio.  
  
2.  Agregue el código XAML siguiente entre las etiquetas `<Grid>` y `</Grid>`  
  
    ```xaml  
    <Grid.Background>  
        <ImageBrush ImageSource="watermark.png" />  
    </Grid.Background>  
    <Grid.ColumnDefinitions>  
        <ColumnDefinition Width="230" />  
        <ColumnDefinition />  
    </Grid.ColumnDefinitions>  
    <Grid.RowDefinitions>  
        <RowDefinition Height="Auto" />  
        <RowDefinition />  
    </Grid.RowDefinitions>  
  
    <Label Grid.Column="1" VerticalAlignment="Center" FontFamily="Trebuchet MS"   
    FontWeight="Bold" FontSize="18" Foreground="#0066cc">  
        Expense Report For:  
    </Label>  
    <Grid Margin="10" Grid.Column="1" Grid.Row="1">  
  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition />  
            <ColumnDefinition />  
        </Grid.ColumnDefinitions>  
        <Grid.RowDefinitions>  
            <RowDefinition Height="Auto" />  
            <RowDefinition Height="Auto" />  
            <RowDefinition />  
        </Grid.RowDefinitions>  
  
        <!-- Name -->  
        <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="0" Orientation="Horizontal">  
            <Label Margin="0,0,0,5" FontWeight="Bold">Name:</Label>  
            <Label Margin="0,0,0,5" FontWeight="Bold"></Label>  
        </StackPanel>  
  
        <!-- Department -->  
        <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="1" Orientation="Horizontal">  
            <Label Margin="0,0,0,5" FontWeight="Bold">Department:</Label>  
            <Label Margin="0,0,0,5" FontWeight="Bold"></Label>  
        </StackPanel>  
  
        <Grid Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="2" VerticalAlignment="Top"   
              HorizontalAlignment="Left">  
            <!-- Expense type and Amount table -->  
            <DataGrid  AutoGenerateColumns="False" RowHeaderWidth="0" >  
                <DataGrid.ColumnHeaderStyle>  
                    <Style TargetType="{x:Type DataGridColumnHeader}">  
                        <Setter Property="Height" Value="35" />  
                        <Setter Property="Padding" Value="5" />  
                        <Setter Property="Background" Value="#4E87D4" />  
                        <Setter Property="Foreground" Value="White" />  
                    </Style>  
                </DataGrid.ColumnHeaderStyle>  
                <DataGrid.Columns>  
                    <DataGridTextColumn Header="ExpenseType" />  
                    <DataGridTextColumn Header="Amount"  />  
                </DataGrid.Columns>  
            </DataGrid>  
        </Grid>  
    </Grid>  
    ```  
  
     Esta interfaz de usuario es similar a la interfaz de usuario creada para la página de inicio, aunque los datos del informe se muestran en un control **DataGrid** .  
  
3.  Compile y ejecute la aplicación.  
  
4.  Elija el botón **Ver** .  
  
     Se mostrará la página de informe de gastos  
  
     En la ilustración siguiente se muestra la página de informe de gastos. Observe que el botón de navegación hacia atrás está habilitado.  
  
     ![Captura de pantalla de ejemplo ExpenseIt](../designers/media/gettingstartedfigure4.png "GettingStartedFigure4")  
  
#### <a name="to-style-controls"></a>Aplicar estilo a los controles  
  
1.  Abra el archivo **App.xaml** (C#) o **Application.xaml** (Visual Basic).  
  
2.  Agregue el siguiente código XAML siguiente entre las etiquetas `<Application.Resources>` y `</Application.Resources>` .  
  
    ```xaml  
    <!-- Header text style -->  
    <Style x:Key="headerTextStyle">  
        <Setter Property="Label.VerticalAlignment" Value="Center"></Setter>  
        <Setter Property="Label.FontFamily" Value="Trebuchet MS"></Setter>  
        <Setter Property="Label.FontWeight" Value="Bold"></Setter>  
        <Setter Property="Label.FontSize" Value="18"></Setter>  
        <Setter Property="Label.Foreground" Value="#0066cc"></Setter>  
    </Style>  
  
    <!-- Label style -->  
    <Style x:Key="labelStyle" TargetType="{x:Type Label}">  
        <Setter Property="VerticalAlignment" Value="Top" />  
        <Setter Property="HorizontalAlignment" Value="Left" />  
        <Setter Property="FontWeight" Value="Bold" />  
        <Setter Property="Margin" Value="0,0,0,5" />  
    </Style>  
  
    <!-- DataGrid header style -->  
    <Style x:Key="columnHeaderStyle" TargetType="{x:Type DataGridColumnHeader}">  
        <Setter Property="Height" Value="35" />  
        <Setter Property="Padding" Value="5" />  
        <Setter Property="Background" Value="#4E87D4" />  
        <Setter Property="Foreground" Value="White" />  
    </Style>  
  
    <!-- List header style -->  
    <Style x:Key="listHeaderStyle" TargetType="{x:Type Border}">  
        <Setter Property="Height" Value="35" />  
        <Setter Property="Padding" Value="5" />  
        <Setter Property="Background" Value="#4E87D4" />  
    </Style>  
  
    <!-- List header text style -->  
    <Style x:Key="listHeaderTextStyle" TargetType="{x:Type Label}">  
        <Setter Property="Foreground" Value="White" />  
        <Setter Property="VerticalAlignment" Value="Center" />  
        <Setter Property="HorizontalAlignment" Value="Left" />  
    </Style>  
  
    <!-- Button style -->  
    <Style x:Key="buttonStyle" TargetType="{x:Type Button}">  
        <Setter Property="Width" Value="125" />  
        <Setter Property="Height" Value="25" />  
        <Setter Property="Margin" Value="0,10,0,0" />  
        <Setter Property="HorizontalAlignment" Value="Right" />  
    </Style>  
    ```  
  
     Este código XAML agrega los estilos siguientes:  
  
    -   `headerTextStyle`: para dar formato al título de la página `Label`.  
  
    -   `labelStyle`: para dar formato a los controles `Label` .  
  
    -   `columnHeaderStyle`: para dar formato a `DataGridColumnHeader`.  
  
    -   `listHeaderStyle`: para dar formato a los controles del encabezado de lista `Border` .  
  
    -   `listHeaderTextStyle`: para dar formato al encabezado de lista **Etiqueta**.  
  
    -   `buttonStyle`: para dar formato a `Button` en la página **ExpenseItHome.xaml** .  
  
3.  Abra **ExpenseItHome.xaml** y reemplace todo lo que haya entre los elementos `<Grid>` y `</Grid>` con el código XAML siguiente:  
  
    ```xaml  
    <Grid.ColumnDefinitions>  
                <ColumnDefinition Width="230" />  
                <ColumnDefinition />  
            </Grid.ColumnDefinitions>  
  
            <Grid.RowDefinitions>  
                <RowDefinition/>  
                <RowDefinition Height="Auto"/>  
                <RowDefinition />  
                <RowDefinition Height="Auto"/>  
            </Grid.RowDefinitions>  
            <Label Grid.Column="1" Style="{StaticResource headerTextStyle}" >  
                View Expense Report  
            </Label>  
            <!-- People list -->  
                  <Border Grid.Column="1" Grid.Row="1" Style="{StaticResource listHeaderStyle}">  
                <Label Style="{StaticResource listHeaderTextStyle}">Names</Label>  
            </Border>  
            <ListBox Name="peopleListBox" Grid.Column="1" Grid.Row="2">  
                <ListBoxItem>Mike</ListBoxItem>  
                <ListBoxItem>Lisa</ListBoxItem>  
                <ListBoxItem>John</ListBoxItem>  
                <ListBoxItem>Mary</ListBoxItem>  
            </ListBox>  
  
            <!-- View report button -->  
            <Button Grid.Column="1" Grid.Row="3" Click="Button_Click" Style="{StaticResource buttonStyle}">View</Button>  
            <Grid.Background>  
                <ImageBrush ImageSource="watermark.png"  />  
            </Grid.Background>  
    ```  
  
     Las propiedades como `VerticalAlignment` y `FontFamily` que definen la apariencia de cada control se quitan y reemplazan aplicando los estilos.  
  
4.  Abra **ExpenseReportPage.xaml** y reemplace todo lo que haya entre los elementos `<Grid>` y finalmente `</Grid>` con el código XAML siguiente:  
  
    ```xaml  
    <Grid.Background>  
        <ImageBrush ImageSource="watermark.png" />  
    </Grid.Background>  
    <Grid.ColumnDefinitions>  
        <ColumnDefinition Width="230" />  
        <ColumnDefinition />  
    </Grid.ColumnDefinitions>  
    <Grid.RowDefinitions>  
        <RowDefinition Height="Auto" />  
        <RowDefinition />  
    </Grid.RowDefinitions>  
    <Label Grid.Column="1" Style="{StaticResource headerTextStyle}">  
        Expense Report For:  
    </Label>  
    <Grid Margin="10" Grid.Column="1" Grid.Row="1">  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition />  
            <ColumnDefinition />  
        </Grid.ColumnDefinitions>  
        <Grid.RowDefinitions>  
            <RowDefinition Height="Auto" />  
            <RowDefinition Height="Auto" />  
            <RowDefinition />  
        </Grid.RowDefinitions>  
  
        <!-- Name -->  
        <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="0" Orientation="Horizontal">  
            <Label Style="{StaticResource labelStyle}">Name:</Label>  
            <Label Style="{StaticResource labelStyle}"></Label>  
        </StackPanel>  
  
        <!-- Department -->  
        <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="1"   
    Orientation="Horizontal">  
            <Label Style="{StaticResource labelStyle}">Department:</Label>  
            <Label Style="{StaticResource labelStyle}"></Label>  
        </StackPanel>  
  
        <Grid Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="2" VerticalAlignment="Top"   
              HorizontalAlignment="Left">  
            <!-- Expense type and Amount table -->  
            <DataGrid ColumnHeaderStyle="{StaticResource columnHeaderStyle}"   
                      AutoGenerateColumns="False" RowHeaderWidth="0" >  
                <DataGrid.Columns>  
                    <DataGridTextColumn Header="ExpenseType" />  
                    <DataGridTextColumn Header="Amount"  />  
                </DataGrid.Columns>  
            </DataGrid>  
        </Grid>  
    </Grid>    
    ```  
  
     Esto agrega estilos a los elementos `<Label>` y `<Border>` .  
  
## <a name="connecting-to-data"></a>Conectarse a datos  
 En esta sección, podrá crear un proveedor de datos y una plantilla de datos y, después, conectar los controles para mostrar los datos.  
  
#### <a name="to-bind-data-to-a-control"></a>Cómo enlazar datos a un control  
  
1.  Abra **ExpenseItHome.xaml** y elija el elemento `<Grid>` .  
  
2.  Agregue el siguiente código XAML:  
  
    ```xaml    
    <Grid.Resources>  
    <!-- Expense Report Data -->  
    <XmlDataProvider x:Key="ExpenseDataSource" XPath="Expenses">  
        <x:XData>  
            <Expenses xmlns="">  
                <Person Name="Mike" Department="Legal">  
                    <Expense ExpenseType="Lunch" ExpenseAmount="50" />  
                    <Expense ExpenseType="Transportation" ExpenseAmount="50" />  
                </Person>  
                <Person Name="Lisa" Department="Marketing">  
                    <Expense ExpenseType="Document printing"  
          ExpenseAmount="50"/>  
                    <Expense ExpenseType="Gift" ExpenseAmount="125" />  
                </Person>  
                <Person Name="John" Department="Engineering">  
                    <Expense ExpenseType="Magazine subscription"   
         ExpenseAmount="50"/>  
                    <Expense ExpenseType="New machine" ExpenseAmount="600" />  
                    <Expense ExpenseType="Software" ExpenseAmount="500" />  
                </Person>  
                <Person Name="Mary" Department="Finance">  
                    <Expense ExpenseType="Dinner" ExpenseAmount="100" />  
                </Person>  
            </Expenses>  
        </x:XData>  
    </XmlDataProvider>  
    </Grid.Resources>  
    ```  
  
     Este código crea una clase `XmlDataProvider` que contiene los datos de cada persona. Normalmente esto se cargaría como archivo, pero los datos se agregan en línea para simplificar.  
  
3.  En el elemento `<Grid.Resources>` , agregue el siguiente código XAML.  
  
    ```xaml  
    <!-- Name item template -->  
    <DataTemplate x:Key="nameItemTemplate">  
        <Label Content="{Binding XPath=@Name}"/>  
    </DataTemplate>  
    ```  
  
     Esto agrega una `Data Template` que define cómo mostrar los datos en **ListBox**.  
  
4.  Reemplace el elemento `<ListBox>` existente por el siguiente código XAML:  
  
    ```xaml  
    <ListBox Name="peopleListBox" Grid.Column="1" Grid.Row="2"   
             ItemsSource="{Binding Source={StaticResource ExpenseDataSource}, XPath=Person}"  
             ItemTemplate="{StaticResource nameItemTemplate}">  
    </ListBox>  
    ```  
  
     Este código enlaza la propiedad `ItemsSource` de `ListBox` al origen de datos y aplica la plantilla de datos como `ItemTemplate`.  
  
#### <a name="to-connect-data-to-controls"></a>Para conectar datos a controles  
  
1.  Abra **ExpenseReportPage.xaml.vb** o **ExpenseReportPage.xaml.cs**.  
  
2.  En C#, agregue el siguiente constructor a la clase **ExpenseReportPage** , o bien, en Visual Basic, reemplace la clase existente por lo siguiente:  
  
    ```csharp  
    // Custom constructor to pass expense report data  
    public ExpenseReportPage(object data):this()  
    {  
        // Bind to expense report data.  
        this.DataContext = data;  
    }  
    ```  
  
    ```vb  
    Partial Public Class ExpenseReportPage  
    Inherits Page  
        Public Sub New()  
        InitializeComponent()  
        End Sub  
  
        ' Custom constructor to pass expense report data  
        Public Sub New(ByVal data As Object)  
            Me.New()  
            ' Bind to expense report data.  
            Me.DataContext = data  
        End Sub    
    End Class  
    ```  
  
     Este constructor toma un objeto de datos como un parámetro. En este caso, el objeto de datos contendrá el nombre de la persona seleccionada.  
  
3.  Abra el archivo **ExpenseItHome.xaml.vb** o **ExpenseItHome.xaml.cs**.  
  
4.  Reemplace el código del controlador de eventos `Click` por lo siguiente:  
  
    ```csharp  
    private void Button_Click(object sender, RoutedEventArgs e)  
    {  
        // View Expense Report  
        ExpenseReportPage expenseReportPage = new ExpenseReportPage(this.peopleListBox.SelectedItem);  
        this.NavigationService.Navigate(expenseReportPage);    
    }  
    ```  
  
    ```vb  
    Private Sub Button_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)  
        ' View Expense Report  
        Dim expenseReportPage As New ExpenseReportPage(Me.peopleListBox.SelectedItem)  
        Me.NavigationService.Navigate(expenseReportPage)  
    End Sub  
    ```  
  
     Este código llama al constructor nuevo.  
  
#### <a name="to-update-the-ui-with-data-templates"></a>Para actualizar la interfaz de usuario con plantillas de datos  
  
1.  Abra el archivo **ExpenseReportPage.xaml**.  
  
2.  Reemplace el código XAML de los elementos **Nombre** y **Departamento**`<StackPanel` con lo siguiente:  
  
    ```xaml  
    <!-- Name -->  
    <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="0" Orientation="Horizontal">  
        <Label Style="{StaticResource labelStyle}">Name:</Label>  
        <Label Style="{StaticResource labelStyle}" Content="{Binding XPath=@Name}"></Label>  
    </StackPanel>  
  
    <!-- Department -->  
    <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="1" Orientation="Horizontal">  
        <Label Style="{StaticResource labelStyle}">Department:</Label>  
        <Label Style="{StaticResource labelStyle}" Content="{Binding XPath=@Department}"></Label>  
    </StackPanel>    
    ```  
  
     Esto enlaza los controles de **Etiqueta** a las propiedades del origen de datos adecuado.  
  
3.  Agregue el código XAML siguiente en el elemento `<Grid>` :  
  
    ```xaml  
    <!--Templates to display expense report data-->  
    <Grid.Resources>  
        <!-- Reason item template -->  
        <DataTemplate x:Key="typeItemTemplate">  
            <Label Content="{Binding XPath=@ExpenseType}"/>  
        </DataTemplate>  
        <!-- Amount item template -->  
        <DataTemplate x:Key="amountItemTemplate">  
            <Label Content="{Binding XPath=@ExpenseAmount}"/>  
        </DataTemplate>  
    </Grid.Resources>    
    ```  
  
     Esto define cómo se muestran los datos del informe de gastos.  
  
4.  Reemplace el elemento `<DataGrid>` por los siguiente.  
  
    ```xaml  
    <!-- Expense type and Amount table -->  
    <DataGrid ItemsSource="{Binding XPath=Expense}" ColumnHeaderStyle="{StaticResource columnHeaderStyle}" AutoGenerateColumns="False" RowHeaderWidth="0" >  
  
        <DataGrid.Columns>  
            <DataGridTextColumn Header="ExpenseType" Binding="{Binding XPath=@ExpenseType}"  />  
            <DataGridTextColumn Header="Amount" Binding="{Binding XPath=@ExpenseAmount}" />  
        </DataGrid.Columns>  
  
    </DataGrid>  
    ```  
  
     Esto agrega **ItemSource** y define los enlaces para los elementos de gastos.  
  
5.  Compile y ejecute la aplicación.  
  
6.  Elija una persona y, a continuación, elija el botón **Ver** .  
  
     La ilustración siguiente muestra ambas páginas de la aplicación ExpenseIt con los controles, el diseño, los estilos, el enlace de datos y las plantillas de datos aplicadas.  
  
     ![Capturas de pantalla de ejemplo ExpenseIt](../designers/media/gettingstartedfigure5.png "GettingStartedFigure5")  
  
##  <a name="Best_Practices"></a> Procedimientos recomendados  
 Esta muestra ilustra los fundamentos de WPF y, por consiguiente, no sigue las prácticas recomendadas de desarrollo de aplicaciones. Para obtener procedimientos recomendados de desarrollo de aplicaciones de WPF y .NET Framework, vea los temas siguientes según corresponda:  
  
-   Accesibilidad: [Procedimientos de accesibilidad recomendados](https://msdn.microsoft.com/en-us/library/aa350483\(v=vs.100\).aspx)  
  
-   Seguridad: [Seguridad de Windows Presentation Foundation](https://msdn.microsoft.com/en-us/library/aa970906\(v=vs.100\).aspx)  
  
-   Localización: [Información general sobre la globalización y la localización de WPF](https://msdn.microsoft.com/en-us/library/ms788718\(v=vs.100\).aspx)  
  
-   Rendimiento: [Optimizar WPF: Rendimiento de aplicaciones](https://msdn.microsoft.com/en-us/library/aa970683\(v=vs.100\).aspx)  
  
##  <a name="Whats_Next"></a> Pasos adicionales  
 Ahora tiene una serie de técnicas a su disposición para crear una aplicación de escritorio con WPF. Ya dispone de conocimientos básicos de los bloques de creación de aplicaciones de WPF enlazados a datos. Este tema no pretende ser exhaustivo, pero espero que ya tenga una idea de las posibilidades que puede descubrir por sí mismo además de las técnicas descritas en este tema.  
  
 Para más información sobre los modelos de programación y arquitectura de WPF, vea los temas siguientes:  
  
-   [Arquitectura de WPF](https://msdn.microsoft.com/en-us/library/ms750441\(v=vs.100\).aspx)  
  
-   [Información general sobre XAML](https://msdn.microsoft.com/en-us/library/ms752059\(v=vs.100\).aspx)  
  
-   [Información general sobre las propiedades de dependencia](https://msdn.microsoft.com/en-us/library/ms752914\(v=vs.100\).aspx)  
  
-   [Sistema de diseño](https://msdn.microsoft.com/en-us/library/ms745058\(v=vs.100\).aspx)  
  
-   [Estilos y plantillas](https://msdn.microsoft.com/en-us/library/bb613570\(v=vs.100\).aspx)  
  
 Para más información sobre la creación de aplicaciones, vea los temas siguientes:  
  
-   [Información general sobre el desarrollo de aplicaciones](https://msdn.microsoft.com/en-us/library/bb613549\(v=vs.100\).aspx)  
  
-   [Información general sobre los controles](https://msdn.microsoft.com/en-us/library/bb613551\(v=vs.100\).aspx)  
  
-   [Información general sobre el enlace de datos](https://msdn.microsoft.com/en-us/library/ms752347\(v=vs.100\).aspx)  
  
-   [Información general sobre gráficos, animaciones y multimedia de WPF.](https://msdn.microsoft.com/en-us/library/ms742562\(v=vs.100\).aspx)  
  
-   [Documentos en WPF](https://msdn.microsoft.com/en-us/library/ms748388\(v=vs.100\).aspx)  
  
## <a name="see-also"></a>Vea también  
[Crear aplicaciones de escritorio modernas con Windows Presentation Foundation](../designers/create-modern-desktop-applications-with-windows-presentation-foundation.md)