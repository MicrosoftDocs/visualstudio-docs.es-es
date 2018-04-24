---
title: Inspeccionar las propiedades XAML durante la depuración | Documentos de Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 390edde4-7b8d-4c89-8d69-55106b7e6b11
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: fcb2877a79afc310985102972d870caae560b393
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="inspect-xaml-properties-while-debugging"></a>Inspeccionar las propiedades XAML durante la depuración
Puede obtener una vista en tiempo real del código XAML en ejecución con el **Live Visual Tree** y **Live Property Explorer**. Estas herramientas le proporcionan una vista de árbol de los elementos de interfaz de usuario de la aplicación XAML en ejecución y le muestran las propiedades en runtime de cualquier elemento de interfaz de usuario que seleccione.  
  
 Puede usar estas herramientas en las siguientes configuraciones:  
  
|Tipo de aplicación|Sistema operativo y herramientas|  
|-----------------|--------------------------------|  
|Aplicaciones de Windows Presentation Foundation (4.0 y versiones posteriores)|Windows 7 y versiones posteriores|  
|Aplicaciones Windows universales|Windows 10 y versiones posteriores, con el [Windows 10 SDK](https://dev.windows.com/en-us/downloads/windows-10-sdk)|  
  
## <a name="looking-at-elements-in-the-live-visual-tree"></a>Inspeccionar elementos en Live Visual Tree  
 Comencemos con una aplicación WPF muy sencilla que tiene una vista de lista y un botón. Al hacer clic en el botón, se agrega otro elemento a la lista. Los elementos con números pares se muestran en color gris, mientras que los elementos con números impares se muestran de color amarillo.  
  
 Cree una nueva aplicación de WPF de C# (archivo > Nuevo > proyecto, a continuación, seleccione C# y busque aplicación WPF). Asígnele el nombre **TestXAML**.  
  
 Cambie el archivo MainWindow.xaml por lo siguiente:  
  
```xaml  
<Window x:Class="TestXAML.MainWindow"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    xmlns:local="clr-namespace:TestXAML"  
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
int count;

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
  
 Compile la solución y comience la depuración. La configuración de compilación debe ser Depurar, no Liberar. Para obtener más información acerca de las configuraciones de compilación, consulte [descripción de las configuraciones de compilación](../ide/understanding-build-configurations.md).)  
  
 Cuando aparezca la ventana, haga clic en el **Agregar elemento** botón un par de veces. Verá algo parecido a esto:  
  
 ![Ventana principal de la aplicación](../debugger/media/livevisualtree-app.png "LiveVIsualTree aplicación")  
  
 Abra ahora el **Live Visual Tree** ventana (**Depurar > Windows > Live Visual Tree**, o búsquela en el lado izquierdo del IDE). Arrástrela de manera que podamos buscar en esta ventana su posición de acoplamiento y la **Live Properties** ventana en paralelo. En el **Live Visual Tree** ventana, expanda la **ContentPresenter** nodo. Debe contener nodos para el botón y el cuadro de lista. Expanda el cuadro de lista (y, a continuación, el **ScrollContentPresenter** y **ItemsPresenter**) para buscar la lista de elementos del cuadro. La ventana debe ser similar a la que se muestra a continuación:  
  
 ![Elementos ListBoxItem en Live Visual Tree](../debugger/media/livevisualtree-listboxitems.png "LiveVisualTree-elementos ListBoxItem")  
  
 Vuelva a la ventana de la aplicación y agregue algunos elementos más. Debería ver más elementos del cuadro de lista aparecen en la **Live Visual Tree**.  
  
 Ahora Echemos un vistazo a las propiedades de uno de los elementos del cuadro de lista. Seleccione el primer elemento del cuadro de lista en la **Live Visual Tree** y haga clic en el **mostrar propiedades** icono en la barra de herramientas. El **Live Property Explorer** debería aparecer. Tenga en cuenta que la **contenido** campo es "Elemento1" y el **fondo** campo es **#ffffffe0** (amarillo claro). Vuelva a la **Live Visual Tree** y seleccione el segundo elemento de cuadro de lista. El **Live Property Explorer** debe mostrar que el **contenido** campo es «Item2» y **fondo** campo es **#ffd3d3d3** (gris claro ).  
  
 La estructura real del XAML tiene una gran cantidad de elementos que probablemente no le interesa directamente y, si no conoce bien el código podría tener un bastante tiempo navegando por el árbol para encontrar lo está buscando. Por lo que la **Live Visual Tree** tiene un par de maneras que permiten usar la interfaz de usuario de la aplicación para encontrar el elemento que desea examinar.  
  
 **Habilitar la selección de la aplicación en ejecución**. Puede habilitar este modo al seleccionar el botón situado en la **Live Visual Tree** barra de herramientas. Con este modo activado, puede seleccionar un elemento de interfaz de usuario en la aplicación y el **Live Visual Tree** (y la **Live Property Viewer**) se actualiza automáticamente para mostrar el nodo en el árbol correspondiente a ese elemento, y sus propiedades.  
  
 **Mostrar adornos de diseño de la aplicación en ejecución**. Puede habilitar este modo al seleccionar el botón que está justo a la derecha del botón Habilitar selección. Cuando **mostrar adornos de diseño** está activado, hace que la ventana de la aplicación mostrar las líneas horizontales y verticales a lo largo de los límites del objeto seleccionado para que pueda ver lo que alinea, así como rectángulos que muestran los márgenes. Por ejemplo, active las opciones **Habilitar selección** y **presentación** en y, a continuación, seleccione la **Agregar elemento** bloque de texto en la aplicación. Debería ver el nodo del bloque de texto en el **Live Visual Tree** y propiedades del bloque de texto el **Live Property Viewer**, así como las líneas horizontales y verticales en los límites del bloque de texto.  
  
 ![LivePropertyViewer en DisplayLayout](../debugger/media/livevisualtreelivepropertyviewer-displaylayout.png "LiveVisualTreeLivePropertyViewer DisplayLayout")  
  
 **Obtener una vista previa selección**. Puede habilitar este modo seleccionando el tercer botón de la izquierda en la barra de herramientas de Live Visual Tree. Este modo muestra el XAML donde se ha declarado el elemento, siempre y cuando tenga acceso al código fuente de la aplicación. Seleccione **Habilitar selección** y **obtener una vista previa selección**, y, a continuación, seleccione el botón de nuestra aplicación de prueba. Se abre el archivo MainWindow.xaml en Visual Studio y se coloca el cursor en la línea en la que se define el botón.  
  
## <a name="using-xaml-tools-with-running-applications"></a>Usar herramientas XAML con las aplicaciones en ejecución  
 Puede usar estas herramientas XAML, incluso si no tiene el código fuente. Cuando se asocia a una aplicación XAML en ejecución, puede utilizar el **Live Visual Tree** en los elementos de interfaz de usuario de esa aplicación demasiado. Este es un ejemplo, mediante la misma aplicación de prueba WPF que hemos usado antes.  
  
1.  Iniciar el **TestXaml** aplicación en la configuración de lanzamiento. No se puede adjuntar a un proceso que se ejecuta en un **depurar** configuración.  
  
2.  Abra una segunda instancia de Visual Studio y haga clic en **Depurar > asociar al proceso**. Buscar **TestXaml.exe** en la lista de procesos disponibles y haga clic en **adjuntar**.  
  
3.  La aplicación comienza a ejecutarse.  
  
4.  En la segunda instancia de Visual Studio, abra el **Live Visual Tree** (**Depurar > Windows > Live Visual Tree**). Debería ver el **TestXaml** elementos de interfaz de usuario y se debería poder manipularlos como lo hizo al depurar la aplicación directamente.