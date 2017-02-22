---
title: "Inspeccionar las propiedades XAML durante la depuraci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 390edde4-7b8d-4c89-8d69-55106b7e6b11
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Inspeccionar las propiedades XAML durante la depuraci&#243;n
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede obtener una vista en tiempo real del código XAML en ejecución con **Live Visual Tree** y **Live Property Explorer**.  Estas herramientas le proporcionan una vista de árbol de los elementos de interfaz de usuario de la aplicación XAML en ejecución y le muestran las propiedades en tiempo de ejecución de cualquier elemento de interfaz de usuario que seleccione.  
  
 Puede usar estas herramientas en las siguientes configuraciones:  
  
|Tipo de aplicación|Sistema operativo y herramientas|  
|------------------------|--------------------------------------|  
|Aplicaciones de Windows Presentation Foundation \(4.0 y versiones posteriores\)|Windows 7 y versiones posteriores|  
|Aplicaciones de la Tienda Windows y de Windows Phone 8.1|Windows 10 y posteriores, con el [SDK de Windows 10](https://dev.windows.com/es-es/downloads/windows-10-sdk)|  
|Aplicaciones Windows universales|Windows 10 y posteriores, con el [SDK de Windows 10](https://dev.windows.com/es-es/downloads/windows-10-sdk)|  
  
## Inspeccionar elementos en Live Visual Tree  
 Comencemos con una aplicación WPF muy sencilla que tiene una vista de lista y un botón.  Al hacer clic en el botón, se agrega otro elemento a la lista.  Los elementos con números pares se muestran en color gris, mientras que los elementos con números impares se muestran de color amarillo.  
  
 Cree una nueva aplicación WPF de C\# \(Archivo \/ Nuevo \/ Proyecto, seleccione C\# y busque Aplicación WPF\).  Asígnele el nombre TestXAML.  
  
 Cambie el archivo MainWindow.xaml por lo siguiente:  
  
```xaml  
<Window x:Class="WpfApplication1.MainWindow"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    xmlns:local="clr-namespace:WpfApplication1"  
    mc:Ignorable="d"  
     Title="MainWindow" Height="350" Width="525">  
    <Grid>  
        <Button x:Name="button" Background="LightBlue" Content="Add Item" HorizontalAlignment="Left" Margin="216,206,0,0" VerticalAlignment="Top" Width="75" Click="button_Click"/>  
        <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="100" VerticalAlignment="Top" Width="100" Margin="205,80,0,0"/>  
    </Grid>  
</Window>  
```  
  
 Agregue el siguiente controlador de comandos al archivo MainWindow.xaml.cs:  
  
```c#  
private void button_Click(object sender, RoutedEventArgs e)  
{  
    ListBoxItem item = new ListBoxItem();  
    item.Content = "Item" + ++count;  
    if (count % 2 == 0)  
    {  
        item.Background = Brushes.LightGray;  
    }  
    else  
    {  
        item.Background = Brushes.LightYellow;  
    }  
    listBox.Items.Add(item);  
}  
```  
  
 Compile la solución y comience la depuración.  La configuración de compilación debe ser Depurar, no Liberar.  Para obtener más información sobre las configuraciones de compilación, vea [Descripción de las configuraciones de compilación](../ide/understanding-build-configurations.md).  
  
 Cuando aparezca la ventana, haga clic un par de veces en el botón **Agregar elemento**.  Verá algo parecido a esto:  
  
 ![Ventana principal de la aplicación](../debugger/media/livevisualtree-app.png "LiveVIsualTree\-App")  
  
 Abra la ventana **Live Visual Tree** \(**Depurar \/ Ventanas \/ Live Visual Tree** o búsquela en el lado izquierdo del IDE\).  Arrástrela de su posición de acoplamiento, de modo que podamos ver esta ventana junto con la ventana **Live Properties**.  En la ventana **Live Visual Tree**, expanda el nodo **ContentPresenter**.  Debe contener nodos para el botón y el cuadro de lista.  Expanda el cuadro de lista \(y luego **ScrollContentPresenter** e **ItemsPresenter**\) para buscar los elementos del cuadro de lista.  La ventana debe ser similar a la que se muestra a continuación:  
  
 ![ListBoxItems en el Árbol visual dinámico](../debugger/media/livevisualtree-listboxitems.png "LiveVisualTree\-ListBoxItems")  
  
 Vuelva a la ventana de la aplicación y agregue algunos elementos más.  Debería ver más elementos del cuadro de lista en **Live Visual Tree**.  
  
 Ahora echemos un vistazo a las propiedades de uno de los elementos del cuadro de lista.  Seleccione el primer elemento del cuadro de lista de **Live Visual Tree** y haga clic en el icono **Mostrar propiedades** de la barra de herramientas.  Debería aparecer **Live Property Explorer**.  Tenga en cuenta que el campo **Contenido** es «Item1» y el campo **Fondo** es **\#FFFFFFE0** \(amarillo claro\).  Vuelva a **Live Visual Tree** y seleccione el segundo elemento del cuadro de lista.  **Live Property Explorer** debería mostrar que el campo **Contenido** es «Item2» y que el campo **Fondo** es **\#FFD3D3D3** \(gris claro\).  
  
 La estructura real del XAML tiene muchos elementos que probablemente no le interesen, y si no conoce bien el código tal vez tenga que perder bastante tiempo navegando por el árbol para encontrar lo que está buscando.  **Live Visual Tree** tiene un par de maneras que le permiten usar la interfaz de usuario de la aplicación para poder encontrar el elemento que desea examinar.  
  
 **Habilitar la selección en la aplicación en ejecución**.  Puede habilitar este modo al seleccionar el botón situado más a la izquierda de la barra de herramientas de **Live Visual Tree**.  Con este modo activado puede seleccionar un elemento de interfaz de usuario en la aplicación; **Live Visual Tree** \(y **Live Property Viewer**\) se actualiza automáticamente para mostrar el nodo en el árbol correspondiente a dicho elemento y sus propiedades.  
  
 **Mostrar adornos de diseño en la aplicación en ejecución**.  Puede habilitar este modo al seleccionar el botón que está justo a la derecha del botón Habilitar selección.  Cuando la opción **Mostrar adornos de diseño** está activada, la ventana de la aplicación muestra líneas horizontales y verticales a lo largo de los límites del objeto seleccionado para que pueda ver lo que alinea, así como rectángulos que muestran los márgenes.  Por ejemplo, active las opciones **Habilitar selección** y **Mostrar adornos de diseño** y seleccione el bloque de texto **Agregar elemento** en la aplicación.  Debería ver el nodo del bloque de texto en **Live Visual Tree** y las propiedades del bloque de texto en **Live Property Viewer**, así como las líneas horizontales y verticales en los límites del bloque de texto.  
  
 ![LivePropertyViewer en DisplayLayout](../debugger/media/livevisualtreelivepropertyviewer-displaylayout.png "LiveVisualTreeLivePropertyViewer\-DisplayLayout")  
  
 **Obtener una vista previa de la selección**.  Puede habilitar este modo seleccionando el tercer botón de la izquierda en la barra de herramientas de Live Visual Tree.  Este modo muestra el XAML donde se ha declarado el elemento, siempre y cuando tenga acceso al código fuente de la aplicación.  Seleccione **Habilitar selección** y **Obtener una vista previa de la selección** y, luego, seleccione el botón de nuestra aplicación de prueba.  Se abre el archivo MainWindow.xaml en Visual Studio y se coloca el cursor en la línea en la que se define el botón.  
  
## Usar herramientas XAML con las aplicaciones en ejecución  
 Puede usar estas herramientas XAML, aunque no disponga del código fuente.  Al adjuntar a una aplicación XAML en ejecución, también puede usar **Live Visual Tree** en los elementos de interfaz de usuario de la aplicación.  Esto es un ejemplo, en el que se ha usado la misma aplicación de prueba WPF que hemos usado antes.  
  
1.  Inicie la aplicación TestXaml en la configuración Liberar.  No puede adjuntar a un proceso que se está ejecutando en una configuración **Depurar**.  
  
2.  Abra una segunda instancia de Visual Studio y haga clic en **Depurar \/ Adjuntar al proceso**.  Busque **TestXaml.exe** en la lista de procesos disponibles y haga clic en **Adjuntar**.  
  
3.  La aplicación comienza a ejecutarse.  
  
4.  En la segunda instancia de Visual Studio, abra **Live Visual Tree** \(**Depurar \/ Ventanas \/ Live Visual Tree**\).  Debería ver los elementos de interfaz de usuario TestXaml y debería poder manipularlos como lo hizo al depurar directamente la aplicación.