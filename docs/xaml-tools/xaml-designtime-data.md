---
title: Uso de datos de tiempo de diseño con el Diseñador XAML en Visual Studio
description: Aprenda a usar los datos en tiempo de diseño en XAML.
ms.date: 04/22/2021
ms.topic: overview
author: alihamie
ms.author: tglee
manager: jmartens
monikerRange: '>=vs-2019'
ms.openlocfilehash: 47bf978bc32c651cb90130ecc90517bfe1c29cdd
ms.sourcegitcommit: 01a411cd7ae3488b7b979a947bca92fd296a98e9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2021
ms.locfileid: "111761113"
---
# <a name="use-design-time-data-with-the-xaml-designer-in-visual-studio"></a>Uso de datos de tiempo de diseño con el Diseñador XAML en Visual Studio

Algunos diseños son difíciles de visualizar sin datos. En este documento, revisaremos uno de los enfoques que pueden usar los desarrolladores que trabajan en proyectos de escritorio para simular datos en el diseñador XAML. Este enfoque se realiza mediante el espacio de nombres "d:" omitible existente. Con este enfoque puede agregar rápidamente datos en tiempo de diseño a las páginas o controles sin necesidad de crear un modelo de presentación ficticio completo, o simplemente probar cómo puede afectar un cambio de propiedad a la aplicación sin preocuparse de que estos cambios tengan un impacto en las compilaciones de versión. Todos los datos de d: los usa únicamente el diseñador XAML y los valores de espacio de nombres que no se pueden omitir se compilan en la aplicación.

> [!NOTE]
> Si usa Xamarin.Forms, consulte [Datos de tiempo de diseño de Xamarin.Forms](/xamarin/xamarin-forms/xaml/xaml-previewer/design-time-data)

## <a name="design-time-data-basics"></a>Aspectos básicos de los datos en tiempo de diseño

Los datos en tiempo de diseño son datos ficticios que se establecen para que los controles sean más fáciles de visualizar en el diseñador XAML. Para empezar, agregue las siguientes líneas de código al encabezado del documento XAML si todavía no están presentes:

```xml
xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
mc:Ignorable="d"
```

Después de agregar los espacios de nombres, puede colocar `d:` delante de cualquier atributo o control para mostrarlo solo en el diseñador XAML pero no en tiempo de ejecución.

Por ejemplo, puede agregar texto a un TextBlock que normalmente tiene datos enlazados a él.

```xml
<TextBlock Text="{Binding Name}" d:Text="Name!" />
```

[![Datos en tiempo de diseño con texto en un TextBlock](media\xaml-design-time-textblock.png "Datos en tiempo de diseño con texto en una etiqueta")](media\xaml-design-time-textblock.png#lightbox)

En este ejemplo, sin `d:Text`, el diseñador XAML no mostraría nada para el TextBlock. En su lugar, muestra "Name!" donde el TextBlock tendrá datos reales en tiempo de ejecución.

Puede usar `d:` con atributos para cualquier control de .NET Core para UWP o WPF, como colores, tamaños de fuente y espaciado. Incluso puede agregarlos al control en sí.

```xml
<d:Button Content="Design Time Button" />
```

[![Datos en tiempo de diseño con un control de botón](media\xaml-design-time-button.png "Datos en tiempo de diseño con un control de botón")](media\xaml-design-time-button.png#lightbox)

En este ejemplo, el botón solo aparece en tiempo de diseño. Utilice este método para colocar un marcador de posición para un control personalizado o para probar distintos controles. Todos los atributos y controles de `d:` se omitirán durante el tiempo de ejecución.

## <a name="preview-images-at-design-time"></a>Vista previa de imágenes en tiempo de diseño

Puede establecer un origen de tiempo de diseño para las imágenes enlazadas a la página o cargadas dinámicamente. Agregue al proyecto la imagen que quiere mostrar en el diseñador XAML. Después, puede mostrar dicha imagen en el diseñador XAML en tiempo de diseño:

```xml
<Image Source={Binding ProfilePicture} d:Source="DesignTimePicture.jpg" />
```

> [!NOTE]
> La imagen de este ejemplo debe existir en la solución.

## <a name="design-time-data-for-listviews"></a>Datos en tiempo de diseño para ListView

Los controles ListView son una manera popular de mostrar los datos en la aplicación de escritorio, pero son difíciles de visualizar sin datos. Puede usar esta característica para crear elementos o un ItemSource de datos en tiempo de diseño en línea. En el diseñador XAML se muestra lo que hay en esa matriz en el objeto ListView en tiempo de diseño.

### <a name="wpf-net-core-example"></a>Ejemplo de .NET Core para WPF
Para usar el tipo system:String, asegúrese de incluir `xmlns:system="clr-namespace:System;assembly=mscorlib` en el encabezado XAML.

```xml
<StackPanel>
    <ListView ItemsSource="{Binding Items}">
        <d:ListView.ItemsSource>
            <x:Array Type="{x:Type system:String}">
                <system:String>Item One</system:String>
                <system:String>Item Two</system:String>
                <system:String>Item Three</system:String>
            </x:Array>
        </d:ListView.ItemsSource>
    <ListView.ItemTemplate>
        <DataTemplate>
            <TextBlock Text="{Binding ItemName}" d:Text="{Binding .}" />
        </DataTemplate>
    </ListView.ItemTemplate>
   </ListView>
</StackPanel>
```

[![Datos en tiempo de diseño con un control ListView](media\xaml-design-time-listview-strings.png "Datos en tiempo de diseño con un control ListView")](media\xaml-design-time-listview-strings.png#lightbox)

En el ejemplo anterior se muestra un control ListView con tres TextBlock en el diseñador XAML.

También puede crear una matriz de objetos de datos. Por ejemplo, las propiedades públicas de un objeto de datos `City` se pueden construir como datos en tiempo de diseño.

```csharp
namespace Cities.Models
{
    public class City
    {
        public string Name { get; set; }
        public string Country { get; set; }
    }
}
```

Para usar la clase en XAML, debe importar el espacio de nombres en el nodo raíz.

```xaml
xmlns:models="clr-namespace:Cities.Models"
```

```xml
<StackPanel>
    <ListView ItemsSource="{Binding Items}">
        <d:ListView.ItemsSource>
            <x:Array Type="{x:Type models:City}">
                <models:City Name="Seattle" Country="United States"/>
                <models:City Name="London" Country="United Kingdom"/>
                <models:City Name="Panama City" Country="Panama"/>
            </x:Array>
        </d:ListView.ItemsSource>
        <ListView.ItemTemplate>
            <DataTemplate>
                 <StackPanel Orientation="Horizontal" >
                    <TextBlock Text="{Binding Name}" Margin="0,0,5,0" />
                    <TextBlock Text="{Binding Country}" />
                 </StackPanel>
            </DataTemplate>
        </ListView.ItemTemplate>
    </ListView>
</StackPanel>
```

[![Modelo real de datos en tiempo de diseño con un control ListView](media\xaml-design-time-listview-models.png "Modelo real de datos en tiempo de diseño con un control ListView")](media\xaml-design-time-listview-models.png#lightbox)

La ventaja es que puede enlazar los controles a una versión estática en tiempo de diseño del modelo.

### <a name="uwp-example"></a>Ejemplo de UWP

x:Array no se admite en UWP. Por lo tanto, podemos usar `<d:ListView.Items>` en su lugar. Para usar el tipo system:String, asegúrese de incluir `http://schemas.microsoft.com/winfx/2009/xaml` en el encabezado XAML.

```xml
    <StackPanel>
        <ListView>
            <d:ListView.Items>
                <system:String>Item One</system:String>
                <system:String>Item Two</system:String>
                <system:String>Item Three</system:String>
            </d:ListView.Items>
        </ListView>
    </StackPanel>
```

## <a name="use-design-time-data-with-custom-types-and-properties"></a>Uso de datos en tiempo de diseño con tipos y propiedades personalizados

De forma predeterminada, esta característica solo funciona con controles y propiedades de plataforma. En esta sección se habla de los pasos necesarios para que pueda usar sus propios controles personalizados como controles en tiempo de diseño, una nueva capacidad disponible para los clientes que usan Visual Studio 2019, versión [16.8](/visualstudio/releases/2019/release-notes/) o posterior. Hay tres requisitos para habilitarla:

- Un espacio de nombres xmlns personalizado.

    ```xml
    xmlns:myControls="http://MyCustomControls"
    ```

- Una versión en tiempo de diseño del espacio de nombres. Para conseguirlo, basta con anexar /design al final.

     ```xml
    xmlns:myDesignTimeControls="http://MyCustomControls/design"
    ```

- Incorporación del prefijo en tiempo de diseño a mc:Ignorable

    ```xml
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d myDesignTimeControls"
    ```

Una vez realizados todos estos pasos, puede usar el prefijo `myDesignTimeControls` para crear los controles en tiempo de diseño.

```xml
<myDesignTimeControls:MyButton>I am a design time Button</myDesignTimeControls:MyButton>
```

### <a name="creating-a-custom-xmlns-namespace"></a>Creación de un espacio de nombres xmlns personalizado

Para crear un espacio de nombres xmlns personalizado en WPF para .NET Core, debe asignar el espacio de nombres XML personalizado al espacio de nombres CLR en el que se encuentran los controles. Para ello, agregue el atributo de nivel de ensamblado `XmlnsDefinition` al archivo `AssemblyInfo.cs`. El archivo se encuentra en la jerarquía raíz del proyecto.

   ```C#
[assembly: XmlnsDefinition("http://MyCustomControls", "MyViews.MyButtons")]
   ```

## <a name="troubleshooting"></a>Solución de problemas

Si experimenta un problema que no aparece en esta sección, háganoslo saber mediante la herramienta [Notificar un problema](../ide/how-to-report-a-problem-with-visual-studio.md).

### <a name="requirements"></a>Requisitos

- Los datos en tiempo de diseño requieren la versión [16.7](/visualstudio/releases/2019/release-notes-v16.7) de Visual Studio 2019 o posterior.

- Admite proyectos de escritorio de Windows dirigidos a Windows Presentation Foundation (WPF) para .NET Core y UWP. Esta característica también está disponible para .NET Framework en el [canal de versión preliminar](/visualstudio/releases/2019/release-notes-preview). Para habilitarla, vaya a **Herramientas** > **Opciones** > **Entorno** > **Características en versión preliminar**, seleccione **Nuevo Diseñador XAML de WPF para .NET Framework** y, luego, reinicie Visual Studio.

- A partir de la versión 16.7 de Visual Studio 2019, esta característica funciona con todos los controles integrados de los marcos de trabajo de WPF y UWP. La compatibilidad con controles de terceros ahora está disponible en la [versión 16.8](/visualstudio/releases/2019/release-notes/).

### <a name="the-xaml-designer-stopped-working"></a>El diseñador de consultas dejó de funcionar

Pruebe a cerrar y volver a abrir el archivo XAML, y limpie y vuelva a compilar el proyecto.

## <a name="see-also"></a>Consulte también

- [Datos de tiempo de diseño con el controlador de vista previa de Xamarin.Forms](/xamarin/xamarin-forms/xaml/xaml-Designer/design-time-data/)
- [XAML en aplicaciones de WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [XAML en aplicaciones de UWP](/windows/uwp/xaml-platform/xaml-overview)
- [XAML en aplicaciones de Xamarin.Forms](/xamarin/xamarin-forms/xaml/)