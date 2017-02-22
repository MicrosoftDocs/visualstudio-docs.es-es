---
title: "Tutorial: Crear una aplicaci&#243;n de escritorio de WPF conectada a un servicio m&#243;vil de Azure | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8d42620f-553b-4b04-a38b-f6b306d73a50
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tutorial: Crear una aplicaci&#243;n de escritorio de WPF conectada a un servicio m&#243;vil de Azure
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede usar Windows Presentation Foundation \(WPF\) para crear rápidamente una aplicación de escritorio moderna que usa un servicio móvil de Azure para almacenar y proporcionar datos.  
  
##  <a name="Requirements"></a> Requisitos previos  
 Necesitará lo siguiente para poder llevar a cabo este tutorial:  
  
-   Visual Studio 2015: cualquier versión que admita el desarrollo en WPF.  
  
-   Una cuenta activa de Microsoft Azure.  
  
    -   Puede suscribirse a una cuenta de prueba gratuita [aquí](http://azure.microsoft.com/en-us/pricing/free-trial/).  
  
    -   Puede activar las [ventajas de suscriptor MSDN](https://azure.microsoft.com/en-us/pricing/member-offers/msdn-benefits-details/?WT.mc_id=A261C142F). Su suscripción a MSDN ofrece créditos cada mes que puede usar para servicios de pago de Azure.  
  
## Crear un proyecto y agregar referencias  
 El primer paso es crear un proyecto de WPF y agregar un paquete de NuGet que le permite conectarse a los servicios móviles de Azure.  
  
#### Para crear el proyecto  
  
1.  En la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
2.  En el cuadro de diálogo **Nuevo proyecto**, expanda el nodo **Visual C\#** o **Visual Basic** y elija el nodo **Windows**. A continuación, expanda el nodo **Windows** y elija **Escritorio clásico**.  
  
3.  En la lista de plantillas, elija la plantilla **Aplicación WPF**.  
  
4.  En el cuadro **Nombre**, escriba `WPFQuickStart` y elija el botón **Aceptar**.  
  
     El proyecto se creará, se agregarán los archivos del proyecto al **Explorador de soluciones** y se mostrará el diseñador de la ventana de aplicación predeterminada denominado **MainWindow.xaml**.  
  
#### Agregar una referencia al SDK de servicios móviles de Windows Azure  
  
1.  En el **Explorador de soluciones**, abra el menú contextual del nodo **Referencias** y, a continuación, elija **Administrar paquetes NuGet**.  
  
2.  En el **Administrador de paquetes NuGet**, elija el campo **Búsqueda** y escriba `mobileservices`.  
  
3.  En el panel izquierdo, elija **WindowsAzure.MobileServices** y, a continuación, en el panel derecho, elija el botón **Instalar**.  
  
    > [!NOTE]
    >  Si aparece el cuadro de diálogo **Vista previa**, revise los cambios propuestos y, a continuación, elija el botón **Aceptar**.  
  
4.  En el cuadro de diálogo **Aceptación de licencia**, revise los términos de la licencia y acéptelos con el botón **Acepto**.  
  
     Se agregarán las referencias necesarias al **Explorador de soluciones**.  
  
    > [!NOTE]
    >  Si no está de acuerdo con los términos de licencia, elija el botón **No acepto**. No podrá finalizar el resto del tutorial.  
  
## Crear la interfaz de usuario  
 El siguiente paso es crear la interfaz de usuario para la aplicación. Primero creará un control de usuario reutilizable que muestra un diseño estándar en paralelo de dos paneles. Podrá agregar el control de usuario a la ventana de la aplicación principal y controles para escribir y mostrar los datos para, a continuación, escribir algo de código para definir la interacción con el servicio móvil de back\-end.  
  
#### Para agregar un control de usuario  
  
1.  En el **Explorador de soluciones**, abra el menú contextual del nodo **WPFQuickStart** y elija **Agregar**, **Nueva carpeta**.  
  
2.  Asigne a la carpeta el nombre `Common`.  
  
3.  Abra el menú contextual de la carpeta **Common** y elija **Agregar**, **Control de usuario**.  
  
4.  En el cuadro de diálogo **Agregar nuevo elemento**, elija el campo Nombre y escriba `QuickStartTask`. A continuación, elija el botón **Agregar**.  
  
     El control de usuario se agregará al proyecto y se abrirá el archivo **QuickStartTask.xaml** en el diseñador.  
  
5.  En el panel inferior del diseñador, seleccione las etiquetas `<Grid>` y `</Grid>` y reemplácelas con el siguiente código XAML:  
  
    ```xaml  
    <Grid VerticalAlignment="Top"> <StackPanel Orientation="Horizontal"> <Border BorderThickness="0,0,1,0" BorderBrush="DarkGray" Margin="0,10" MinWidth="70"> <TextBlock Text="{Binding Number}" FontSize="45" Foreground="DarkGray" Margin="20,0"/> </Border> <StackPanel> <TextBlock Text="{Binding Title}" Margin="10,10,0,0" FontSize="16" FontWeight="Bold" /> <TextBlock Text="{Binding Description}" Margin="10,0,0,0" TextWrapping="Wrap" MaxWidth="500" /> </StackPanel> </StackPanel> </Grid>  
    ```  
  
     Este código XAML crea un diseño reutilizable con marcadores de posición para los campos de número, título y descripción. En tiempo de ejecución pueden sustituirse los marcadores de posición con texto tal como se muestra en la siguiente ilustración.  
  
     ![The QuickStartTask user control](../designers/media/wpfquickstart1.PNG "WPFQuickStart1")  
  
6.  En el **Explorador de soluciones**, expanda el nodo **QuickStartTask.xaml** y abra el archivo **QuickStartTask.xaml.cs** o **QuickStartTask.xaml.vb**.  
  
7.  En el editor de código, reemplace el espacio de nombres `namespace WPFQuickStart.Common` \(C\#\) o el método `Public Class QuickStartTask` \(VB\) con el código siguiente:  
  
    ```c#  
    namespace WPFQuickStart.Common { /// <summary> /// Interaction logic for QuickStartTask.xaml /// </summary> public partial class QuickStartTask : UserControl { public QuickStartTask() { this.InitializeComponent(); this.DataContext = this; } public int Number { get { return (int)GetValue(NumberProperty); } set { SetValue(NumberProperty, value); } } // Using a DependencyProperty as the backing store for Number.  This enables animation, styling, binding, etc... public static readonly DependencyProperty NumberProperty = DependencyProperty.Register("Number", typeof(int), typeof(QuickStartTask), new PropertyMetadata(0)); public string Title { get { return (string)GetValue(TitleProperty); } set { SetValue(TitleProperty, value); } } // Using a DependencyProperty as the backing store for Title.  This enables animation, styling, binding, etc... public static readonly DependencyProperty TitleProperty = DependencyProperty.Register("Title", typeof(string), typeof(QuickStartTask), new PropertyMetadata(default(string))); public string Description { get { return (string)GetValue(DescriptionProperty); } set { SetValue(DescriptionProperty, value); } } // Using a DependencyProperty as the backing store for Description.  This enables animation, styling, binding, etc... public static readonly DependencyProperty DescriptionProperty = DependencyProperty.Register("Description", typeof(string), typeof(QuickStartTask), new PropertyMetadata(default(string))); } }  
    ```  
  
    ```vb  
    Partial Public Class QuickStartTask Inherits UserControl Public Sub New() Me.InitializeComponent() Me.DataContext = Me End Sub Public Property Number() As Integer Get Return CInt(Fix(GetValue(NumberProperty))) End Get Set(ByVal value As Integer) SetValue(NumberProperty, value) End Set End Property ' Using a DependencyProperty as the backing store for Number.  This enables animation, styling, binding, etc... Public Shared ReadOnly NumberProperty As DependencyProperty = DependencyProperty.Register("Number", GetType(Integer), GetType(QuickStartTask), New PropertyMetadata(0)) Public Property Title() As String Get Return CStr(GetValue(TitleProperty)) End Get Set(ByVal value As String) SetValue(TitleProperty, value) End Set End Property ' Using a DependencyProperty as the backing store for Title.  This enables animation, styling, binding, etc... Public Shared ReadOnly TitleProperty As DependencyProperty = DependencyProperty.Register("Title", GetType(String), GetType(QuickStartTask), New PropertyMetadata(Nothing)) Public Property Description() As String Get Return CStr(GetValue(DescriptionProperty)) End Get Set(ByVal value As String) SetValue(DescriptionProperty, value) End Set End Property ' Using a DependencyProperty as the backing store for Description.  This enables animation, styling, binding, etc... Public Shared ReadOnly DescriptionProperty As DependencyProperty = DependencyProperty.Register("Description", GetType(String), GetType(QuickStartTask), New PropertyMetadata(Nothing)) End Class  
    ```  
  
     Este código usa las propiedades de dependencia para establecer los valores de los campos de número, título y descripción en tiempo de ejecución.  
  
8.  En la barra de menús, elija **Compilar**, **Compilar WPFQuickStart** para compilar el control de usuario.  
  
#### Para crear y modificar la ventana principal  
  
1.  En el **Explorador de soluciones**, abra el archivo **MainWindow.xaml**.  
  
2.  **Importante** Este paso es solo para C\#. Si está usando Visual Basic, vaya al paso siguiente. En el panel inferior del diseñador, localice la línea `xmlns:local=”clr-namespace:WPFQuickStart”` y reemplácela con el siguiente código XAML:  
  
    ```xaml  
    xmlns:local=”clr-namespace:WPFQuickStart.Common”  
    ```  
  
3.  En la ventana **Propiedades**, expanda el nodo de categoría **Common** y elija la propiedad **Title**. A continuación, escriba `WPF Todo List` y presione la tecla **Entrar**.  
  
     Tenga en cuenta que el elemento **Título** de la ventana XAML cambia para que coincida con el nuevo valor. Puede modificar las propiedades XAML en la ventana XAML o en la ventana **Propiedades** para que se sincronicen los cambios.  
  
4.  En la ventana XAML, establezca el valor del elemento **Alto** en `768` y establezca el valor de la propiedad **Ancho** en `1280`.  
  
     Estos elementos corresponden a las propiedades **Alto** y **Ancho**, que se encuentran en la categoría **Diseño** en la ventana **Propiedades**.  
  
5.  Seleccione las etiquetas `<Grid>` y `</Grid>` y reemplácelas con el siguiente código XAML:  
  
    ```xaml  
    <Grid> <Grid Margin="50,50,10,10"> <Grid.ColumnDefinitions> <ColumnDefinition Width="*" /> <ColumnDefinition Width="*" /> </Grid.ColumnDefinitions> <Grid.RowDefinitions> <RowDefinition Height="Auto" /> <RowDefinition Height="*" /> </Grid.RowDefinitions> <Grid Grid.Row="0" Grid.ColumnSpan="2" Margin="0,0,0,20"> <StackPanel> <TextBlock Foreground="#0094ff" FontFamily="Segoe UI Light" Margin="0,0,0,6">MICROSOFT AZURE MOBILE SERVICES</TextBlock> <TextBlock Foreground="Gray" FontFamily="Segoe UI Light" FontSize="45" ><Run Text="My Todo List"/></TextBlock> </StackPanel> </Grid> <Grid Grid.Row="1"> <StackPanel> <local:QuickStartTask Number="1" Title="Insert a TodoItem" Description="Enter some text below and click Save to insert a new todo item into the list." /> <StackPanel Orientation="Horizontal" Margin="72,0,0,0"> <TextBox x:Name="TodoInput" Margin="5" MinWidth="300"/> <Button x:Name="ButtonSave" Click="ButtonSave_Click" Content="Save"/> </StackPanel> </StackPanel> </Grid> <Grid Grid.Row="1" Grid.Column="1"> <Grid.RowDefinitions> <RowDefinition Height="Auto" /> <RowDefinition /> </Grid.RowDefinitions> <StackPanel> <local:QuickStartTask Number="2" Title="Query and Update Data" Description="Click the Refresh button to load the unfinished TodoItems from the Azure Mobile Service. Select the checkbox to mark a ToDo item as complete and update the list." /> <Button Margin="72,0,0,0" Name="ButtonRefresh" Click="ButtonRefresh_Click">Refresh</Button> </StackPanel> <ListView Name="ListItems" Margin="62,10,0,0" Grid.Row="1"> <ListView.ItemTemplate> <DataTemplate> <StackPanel Orientation="Horizontal"> <CheckBox Name="CheckBoxComplete" IsChecked="{Binding Complete, Mode=TwoWay}" Checked="CheckBoxComplete_Checked" Content="{Binding Text}" Margin="10,5" VerticalAlignment="Center"/> </StackPanel> </DataTemplate> </ListView.ItemTemplate> </ListView> </Grid> </Grid> </Grid>  
    ```  
  
     Tenga en cuenta que los cambios se reflejan en la ventana de diseño. Una vez más, también podría haber definido la interfaz de usuario agregando controles desde la ventana **Cuadro de herramientas** y estableciendo las propiedades en la ventana **Propiedades**. Todo lo que puede hacer en el diseñador puede realizarse en el código XAML y viceversa.  
  
     En este punto, el diseño debería tener un aspecto similar al de la siguiente ilustración.  
  
     ![The MainWindow in the designer](../designers/media/wpfquickstart2.PNG "WPFQuickStart2")  
  
    > [!NOTE]
    >  Conforme avance en los procedimientos siguientes, podrían aparecer errores algunos podrían aparecer errores en la **Lista de errores** si está abierta. No se preocupe, estos errores desaparecerán una vez completados los procedimientos restantes.  
  
6.  En el **Explorador de soluciones**, expanda el nodo **MainWindow.xaml** y abra el archivo **MainWindow.xaml.cs** o **MainWindow.saml.vb**.  
  
7.  En el Editor de código, agregue las directivas `using` o `Imports` siguientes al principio del archivo.  
  
    ```c#  
    using Microsoft.WindowsAzure.MobileServices; using Newtonsoft.Json;   
    ```  
  
    ```vb  
    Imports Microsoft.WindowsAzure.MobileServices Imports Newtonsoft.Json  
    ```  
  
8.  Reemplace todo el código del espacio de nombres **WPFQuickStart** \(C\#\) o de la clase **MainWindow** \(VB\) con el código siguiente:  
  
    ```c#  
    namespace WPFQuickStart { /// <summary> /// Interaction logic for MainWindow.xaml /// </summary> public class TodoItem { public string Id { get; set; } [JsonProperty(PropertyName = "text")] public string Text { get; set; } [JsonProperty(PropertyName = "complete")] public bool Complete { get; set; } } public partial class MainWindow : Window { private MobileServiceCollection<TodoItem, TodoItem> items; private IMobileServiceTable<TodoItem> todoTable = App.MobileService.GetTable<TodoItem>(); public MainWindow() { InitializeComponent(); } private async void InsertTodoItem(TodoItem todoItem) { // This code inserts a new TodoItem into the database. When the operation completes // and Mobile Services has assigned an Id, the item is added to the CollectionView await todoTable.InsertAsync(todoItem); items.Add(todoItem); } private async void RefreshTodoItems() { try { // This code refreshes the entries in the list view by querying the TodoItem table. // The query excludes completed TodoItems items = await todoTable .Where(todoItem => todoItem.Complete == false) .ToCollectionAsync(); ListItems.ItemsSource = items; } catch (MobileServiceInvalidOperationException e) { MessageBox.Show(e.Message, "Error loading items"); } } private async void UpdateCheckedTodoItem(TodoItem item) { // This code takes a freshly completed TodoItem and updates the database. When the MobileService // responds, the item is removed from the list await todoTable.UpdateAsync(item); items.Remove(item); } private void ButtonRefresh_Click(object sender, RoutedEventArgs e) { RefreshTodoItems(); } private void ButtonSave_Click(object sender, RoutedEventArgs e) { var todoItem = new TodoItem { Text = TodoInput.Text }; InsertTodoItem(todoItem); TodoInput.Text = ""; } private void CheckBoxComplete_Checked(object sender, RoutedEventArgs e) { CheckBox cb = (CheckBox)sender; TodoItem item = cb.DataContext as TodoItem; UpdateCheckedTodoItem(item); } protected override void OnActivated(EventArgs e) { RefreshTodoItems(); } } }  
    ```  
  
    ```vb  
    Public Class TodoItem Public Property Id() As String <JsonProperty(PropertyName:="text")> Public Property Text() As String <JsonProperty(PropertyName:="complete")> Public Property Complete() As Boolean End Class Partial Public Class MainWindow Inherits Window Private items As MobileServiceCollection(Of TodoItem, TodoItem) Private todoTable As IMobileServiceTable(Of TodoItem) = Application.MobileService.GetTable(Of TodoItem)() Public Sub New() InitializeComponent() End Sub Private Async Sub InsertTodoItem(ByVal todoItem As TodoItem) ' This code inserts a new TodoItem into the database. When the operation completes ' and Mobile Services has assigned an Id, the item is added to the CollectionView Await todoTable.InsertAsync(todoItem) items.Add(todoItem) End Sub Private Async Sub RefreshTodoItems() Dim exception As MobileServiceInvalidOperationException = Nothing Try ' This code refreshes the entries in the list view by querying the TodoItem table. ' The query excludes completed TodoItems items = Await todoTable.Where(Function(todoItem) todoItem.Complete = False).ToCollectionAsync() Catch e As MobileServiceInvalidOperationException exception = e End Try If exception IsNot Nothing Then MessageBox.Show(exception.Message, "Error loading items") Else ListItems.ItemsSource = items End If End Sub Private Async Sub UpdateCheckedTodoItem(ByVal item As TodoItem) ' This code takes a freshly completed TodoItem and updates the database. When the MobileService ' responds, the item is removed from the list Await todoTable.UpdateAsync(item) items.Remove(item) End Sub Private Sub ButtonRefresh_Click(ByVal sender As Object, ByVal e As RoutedEventArgs) RefreshTodoItems() End Sub Private Sub ButtonSave_Click(ByVal sender As Object, ByVal e As RoutedEventArgs) Dim todoItem = New TodoItem With {.Text = TodoInput.Text} InsertTodoItem(todoItem) TodoInput.Text = "" End Sub Private Sub CheckBoxComplete_Checked(ByVal sender As Object, ByVal e As RoutedEventArgs) Dim cb As CheckBox = DirectCast(sender, CheckBox) Dim item As TodoItem = TryCast(cb.DataContext, TodoItem) UpdateCheckedTodoItem(item) End Sub Protected Overrides Sub OnActivated(ByVal e As EventArgs) RefreshTodoItems() End Sub End Class  
    ```  
  
     Este código define la interacción entre la interfaz de usuario y la base de datos en el servicio móvil mediante métodos asincrónicos.  
  
## Crear el servicio móvil de Azure  
 El paso final consiste en crear un servicio móvil en Microsoft Azure, agregar una tabla para almacenar los datos y, a continuación, hacer referencia a la instancia de servicio desde la aplicación.  
  
#### Para crear un servicio móvil  
  
1.  Abra un explorador web, e inicie sesión en el portal de Microsoft Azure y, a continuación, elija la pestaña **SERVICIOS MÓVILES**.  
  
2.  Elija el botón **NUEVO** y, en el cuadro de diálogo emergente, elija **PROCESO**, **SERVICIO MÓVIL, CREAR**.  
  
3.  En el cuadro de diálogo **NUEVO SERVICIO MÓVIL**, elija el cuadro de texto **URL** y escriba `wpfquickstart01`.  
  
    > [!NOTE]
    >  Puede que necesite cambiar la parte numérica de la dirección URL. Microsoft Azure requiere una dirección URL única para cada servicio móvil.  
  
     Esto establece la dirección URL del servicio a *https:\/\/wpfquickstart01.azure\-mobile.net\/*.  
  
4.  En la lista **BASE DE DATOS** elija una opción de base de datos. Puesto que se trata de una aplicación que probablemente no obtendrá una gran cantidad de uso, puede que prefiera usar la opción **Crear una base de datos SQL de 20 MB gratuita**. También puede elegir la base de datos gratuita ya asociada a su suscripción.  
  
5.  En la lista **REGIÓN**, elija el centro de datos en el que desea implementar el servicio móvil y, a continuación, elija el botón **Siguiente** \(flecha derecha\).  
  
    > [!NOTE]
    >  Para este servicio, usará la configuración predeterminada **BACK\-END**, **JavaScript**.  
  
6.  Si va a crear una base de datos nueva, en la página **Especificar configuración de la base de datos**, en la lista **SERVER**, elija **Nuevo servidor de bases de datos SQL**, escriba su **NOMBRE DE INICIO DE SESIÓN SQL** y la **CONTRASEÑA** y, a continuación, elija el botón **Completar** \(marca de verificación\).  
  
7.  Si eligió una base de datos existente, en la página **Configuración de base de datos**, escriba su **CONTRASEÑA DE INICIO DE SESIÓN** y, a continuación, elija el botón **Completar** \(marca de verificación\).  
  
     Se iniciará el proceso de creación del servicio móvil. Una vez completado el proceso, el estado cambiará a **Listo** y podrá seguir adelante con el paso siguiente.  
  
8.  En el portal, seleccione el servicio móvil recién creado y, a continuación, elija el botón **ADMINISTRAR CLAVES**.  
  
9. En el cuadro de diálogo **Administrar claves de acceso**, copie la **CLAVE DE APLICACIÓN**.  
  
     Usará esta clave en el procedimiento siguiente.  
  
#### Para crear una tabla  
  
1.  En el portal de Microsoft Azure, elija la flecha derecha situada junto al nombre del servicio móvil y, en la barra de menús, elija **DATOS**. A continuación, elija el vínculo **AGREGAR UNA TABLA**.  
  
2.  En el cuadro de diálogo **Crear nueva tabla**, en el cuadro de texto **NOMBRE DE TABLA**, escriba `TodoItem` y, a continuación, elija el botón **Completar** \(marca de verificación\).  
  
     Espere a que la tabla que se cree y, a continuación, pase al procedimiento final.  
  
#### Para agregar una declaración para el servicio móvil  
  
1.  Vuelva a Visual Studio En el **Explorador de soluciones**, expanda el nodo **App.xaml** \(C\#\) o **Application.xaml** \(Visual Basic\) y abra el archivo **App.xaml.cs** o **App.xaml.vb**.  
  
2.  En el Editor de código, agregue las directivas `using` o **Importaciones** al principio del archivo.  
  
    ```c#  
    using Microsoft.WindowsAzure.MobileServices;  
    ```  
  
    ```vb  
    Imports Microsoft.WindowsAzure.MobileServices  
    ```  
  
3.  Agregue la declaración siguiente a la clase, reemplazando *YOUR\-SERVICE\_HERE* con el nombre de la dirección URL para el servicio y *YOUR\-KEY\-HERE* con la clave de aplicación copiada en el procedimiento anterior:  
  
    ```c#  
    public static MobileServiceClient MobileService = new MobileServiceClient( "https://YOUR-SERVICE-HERE.azure-mobile.net/", "YOUR-KEY-HERE" );  
    ```  
  
    ```vb  
    Public Shared MobileService As New MobileServiceClient("https://YOUR-SERVICE-HERE.azure-mobile.net/", "YOUR-KEY-HERE")  
    ```  
  
     Este código permite a la aplicación tener acceso al servicio móvil que se ejecuta en Microsoft Azure.  
  
## Probar la aplicación  
 Eso es todo. Ha creado una aplicación de escritorio de WPF que tiene acceso a un servicio móvil de Azure. Ahora lo único que queda por hacer es ejecutar la aplicación y verla en acción.  
  
#### Para ejecutar la aplicación  
  
1.  En la barra de menús, elija **Depurar**, **Iniciar depuración** \(o presione F5\).  
  
2.  En el cuadro de texto **Insertar un TodoItem**, escriba `Hacer algo` y, a continuación, elija el botón **Guardar**.  
  
3.  Escriba `Hacer algo más` y, a continuación, vuelva a elegir el botón **Guardar**.  
  
     Observe que las dos entradas se agregan a la lista **Consultar y actualizar datos**, tal como se muestra en la siguiente ilustración.  
  
     ![The Todo items are added to the list.](../designers/media/wpfquickstart3.PNG "WPFQuickStart3")  
  
4.  Active la casilla de la entrada **Hacer algo más** de la lista.  
  
     Esto llamará al método **UpdateCheckedTodoItem** y quitará el elemento de la lista y la base de datos.  
  
## Pasos siguientes  
 Ha completado un ejemplo bastante sencillo de aplicación de escritorio de WPF con un back\-end de Azure. Por supuesto, probablemente una aplicación real resulte mucho más compleja; sin embargo, se aplican los mismos conceptos básicos. Vea [WPF en .NET Framework](https://msdn.microsoft.com/en-us/library/ms754130\(v=vs.100\).aspx).  
  
 Puede hacer la interfaz de usuario más atractiva mediante la adición de colores, formas, gráficos o incluso animaciones. Vea [Designing XAML in Visual Studio and Blend for Visual Studio](../designers/designing-xaml-in-visual-studio.md).  
  
 Puede conectarse a las bases de datos SQL existentes u otros orígenes de datos mediante servicios móviles de Azure. Vea [Documentación de servicios móviles](http://azure.microsoft.com/en-us/services/app-service/mobile/).  
  
## Vea también  
 [Tutorial: Mi primera aplicación de escritorio WPF](../designers/walkthrough-my-first-wpf-desktop-application2.md)   
 [Crear aplicaciones de escritorio modernas con Windows Presentation Foundation](../designers/create-modern-desktop-applications-with-windows-presentation-foundation.md)