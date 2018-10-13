---
title: Inspeccionar las propiedades XAML durante la depuración | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 390edde4-7b8d-4c89-8d69-55106b7e6b11
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 282b93ac9f04f5e547567e8380e65826f433ba2d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49282261"
---
# <a name="inspect-xaml-properties-while-debugging"></a>Inspeccionar las propiedades XAML durante la depuración
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede obtener una vista en tiempo real de la ejecución de código XAML con el **Live Visual Tree** y **Live Property Explorer**. Estas herramientas le proporcionan una vista de árbol de los elementos de interfaz de usuario de la aplicación XAML en ejecución y le muestran las propiedades en runtime de cualquier elemento de interfaz de usuario que seleccione.  
  
 Puede usar estas herramientas en las siguientes configuraciones:  
  
|Tipo de aplicación|Sistema operativo y herramientas|  
|-----------------|--------------------------------|  
|Aplicaciones de Windows Presentation Foundation (4.0 y versiones posteriores)|Windows 7 y versiones posteriores|  
|Aplicaciones de la Tienda Windows y de Windows Phone 8.1|Windows 10 y versiones posteriores, con el [Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk)|  
|Aplicaciones Windows universales|Windows 10 y versiones posteriores, con el [Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk)|  
  
## <a name="looking-at-elements-in-the-live-visual-tree"></a>Inspeccionar elementos en Live Visual Tree  
 Comencemos con una aplicación WPF muy sencilla que tiene una vista de lista y un botón. Al hacer clic en el botón, se agrega otro elemento a la lista. Los elementos con números pares se muestran en color gris, mientras que los elementos con números impares se muestran de color amarillo.  
  
 Cree una nueva aplicación WPF de C# (Archivo / Nuevo / Proyecto, seleccione C# y busque Aplicación WPF). Asígnele el nombre **TestXAML**.  
  
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
  
```csharp  
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
  
 Compile la solución y comience la depuración. La configuración de compilación debe ser Depurar, no Liberar. Para obtener más información acerca de las configuraciones de compilación, véase [descripción de las configuraciones de compilación](../ide/understanding-build-configurations.md).)  
  
 Cuando aparezca la ventana, haga clic en el **Agregar elemento** botón un par de veces. Verá algo parecido a esto:  
  
 ![Ventana principal de la aplicación](../debugger/media/livevisualtree-app.png "LiveVIsualTree-App")  
  
 Abra ahora el **Live Visual Tree** ventana (**depurar / Windows / Live Visual Tree**, o búsquela en el lado izquierdo del IDE). Arrástrela de manera que podamos analizar esta ventana su posición de acoplamiento y la **Live Properties** ventana en paralelo. En el **Live Visual Tree** ventana, expanda el **ContentPresenter** nodo. Debe contener nodos para el botón y el cuadro de lista. Expanda el cuadro de lista (y, a continuación, el **ScrollContentPresenter** y **ItemsPresenter**) para encontrar la lista de elementos del cuadro. La ventana debe ser similar a la que se muestra a continuación:  
  
 ![ListBoxItems en el árbol Visual](../debugger/media/livevisualtree-listboxitems.png "LiveVisualTree ListBoxItems")  
  
 Vuelva a la ventana de la aplicación y agregue algunos elementos más. Debería ver más elementos de cuadro de lista que aparece en el **Live Visual Tree**.  
  
 Ahora echemos un vistazo a las propiedades de uno de los elementos del cuadro de lista. Seleccione el primer elemento de cuadro de lista en el **Live Visual Tree** y haga clic en el **mostrar propiedades** icono en la barra de herramientas. El **Live Property Explorer** debería aparecer. Tenga en cuenta que el **contenido** campo es «Item1» y el **en segundo plano** campo es **#ffffffe0** (amarillo claro). Vuelva a la **Live Visual Tree** y seleccione el segundo elemento del cuadro de lista. El **Live Property Explorer** debe mostrar que el **contenido** campo es «Item2» y el **en segundo plano** campo es **#ffd3d3d3** (gris claro ).  
  
 La estructura real del XAML tiene muchos elementos que probablemente no le interesen, y si no conoce bien el código tal vez tenga que perder bastante tiempo navegando por el árbol para encontrar lo que está buscando. Por lo que la **Live Visual Tree** tiene un par de métodos que permiten usar la interfaz de usuario de la aplicación que le ayudarán a encontrar el elemento que desea examinar.  
  
 **Habilitar la selección en la aplicación en ejecución**. Puede habilitar este modo al seleccionar el botón situado en la **Live Visual Tree** barra de herramientas. Con este modo activado, puede seleccionar un elemento de interfaz de usuario en la aplicación y el **Live Visual Tree** (y el **Live Property Viewer**) se actualiza automáticamente para mostrar el nodo en el árbol correspondiente a ese elemento, y sus propiedades.  
  
 **Mostrar adorners de diseño en la aplicación en ejecución**. Puede habilitar este modo al seleccionar el botón que está justo a la derecha del botón Habilitar selección. Cuando **mostrar adornos de diseño** está activada, hace que la ventana de la aplicación mostrar las líneas horizontales y verticales a lo largo de los límites del objeto seleccionado para que pueda ver lo que alinea, así como los rectángulos que muestran los márgenes. Por ejemplo, active las opciones **Habilitar selección** y **presentación** y seleccione el **Agregar elemento** bloque de texto en la aplicación. Debería ver el nodo de bloque de texto en el **Live Visual Tree** y propiedades del bloque de texto el **Live Property Viewer**, así como las líneas horizontales y verticales en los límites del bloque de texto.  
  
 ![LivePropertyViewer en DisplayLayout](../debugger/media/livevisualtreelivepropertyviewer-displaylayout.png "LiveVisualTreeLivePropertyViewer DisplayLayout")  
  
 **Obtener una vista previa de selección**. Puede habilitar este modo seleccionando el tercer botón de la izquierda en la barra de herramientas de Live Visual Tree. Este modo muestra el XAML donde se ha declarado el elemento, siempre y cuando tenga acceso al código fuente de la aplicación. Seleccione **Habilitar selección** y **obtener una vista previa de selección**, y, a continuación, seleccione el botón en nuestra aplicación de prueba. Se abre el archivo MainWindow.xaml en Visual Studio y se coloca el cursor en la línea en la que se define el botón.  
  
## <a name="using-xaml-tools-with-running-applications"></a>Usar herramientas XAML con las aplicaciones en ejecución  
 Puede usar estas herramientas XAML, aunque no disponga del código fuente. Cuando se adjunta a una aplicación XAML en ejecución, puede usar el **Live Visual Tree** en los elementos de interfaz de usuario de la aplicación demasiado. Esto es un ejemplo, en el que se ha usado la misma aplicación de prueba WPF que hemos usado antes.  
  
1.  Iniciar el **TestXaml** aplicación en la configuración de lanzamiento. No se puede adjuntar a un proceso que se está ejecutando en un **depurar** configuración.  
  
2.  Abra una segunda instancia de Visual Studio y haga clic en **depurar / asociar al proceso**. Buscar **TestXaml.exe** en la lista de procesos disponibles y haga clic en **adjuntar**.  
  
3.  La aplicación comienza a ejecutarse.  
  
4.  En la segunda instancia de Visual Studio, abra el **Live Visual Tree** (**depurar / Windows / Live Visual Tree**). Debería ver el **TestXaml** elementos de interfaz de usuario y se debería poder manipularlos como lo hizo al depurar la aplicación directamente.



