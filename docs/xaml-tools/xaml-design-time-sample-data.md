---
title: Uso de datos de ejemplo en tiempo de diseño con la Diseñador XAML en Visual Studio
description: Obtenga información sobre cómo usar datos de ejemplo en tiempo de diseño en XAML.
ms.date: 05/28/2021
ms.topic: conceptual
author: alihamie
ms.author: tglee
manager: jmartens
monikerRange: vs-2019
ms.openlocfilehash: a987435d454771bdecf078e78af089405718d261
ms.sourcegitcommit: 5366c6bca3fb217a2fbf847998387578f51ec45c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748055"
---
# <a name="use-design-time-sample-data-with-the-xaml-designer-in-visual-studio"></a>Uso de datos de ejemplo en tiempo de diseño con la Diseñador XAML en Visual Studio

Algunos controles dependientes de los datos, como ListView, ListBox o DataGrid, son difíciles de visualizar sin datos. En este documento revisaremos un nuevo enfoque que permite a los desarrolladores que trabajan en proyectos **de WPF .NET Core** o proyectos de WPF **.NET Framework** con el nuevo diseñador habilitar datos de ejemplo en estos controles. 

## <a name="sample-data-feature-basics"></a>Aspectos básicos de las características de datos de ejemplo

Los datos de ejemplo son solo para la visualización en tiempo de diseño, lo que significa que solo aparecen en el diseñador XAML, no en la aplicación en ejecución. Por lo tanto, se aplica a la versión en tiempo de diseño de la propiedad ItemsSource `d:ItemsSource` . Los datos de ejemplo necesitan que el espacio de nombres en tiempo de diseño funcione. Para empezar, agregue las siguientes líneas de código al encabezado del documento XAML si todavía no están presentes:

> [!NOTE]
> Visite [las propiedades en tiempo de diseño de XAML](/xaml/xaml-tools/xaml/xaml-designtime-data.md) para obtener más información sobre las propiedades en tiempo de diseño en XAML.

```xml
xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
mc:Ignorable="d"
```

Después de agregar los espacios de nombres, puede usar para habilitar los datos de `d:ItemsSource="{d:SampleData}"` ejemplo en ListView, Listbox o DataGrid. Por ejemplo:

```xml
<DataGrid d:ItemsSource="{d:SampleData}"/>
```

[![Datos de ejemplo con DataGrid](media\xaml-sample-data-empty-datagrid.png "Datos de ejemplo habilitados en un datagrid")](media\xaml-sample-data-empty-datagrid.png#lightbox)

En este ejemplo, sin `d:ItemsSource="{d:SampleData}"` el Diseñador XAML mostraría un elemento DataGrid vacío. En su lugar, `d:SampleData` con ahora se muestran los datos de ejemplo predeterminados generados.

De forma predeterminada, se muestran 5 elementos. Sin embargo, puede usar la **propiedad ItemCount** para especificar cuántos elementos desea mostrar. por ejemplo: `d:ItemsSource="{d:SampleData ItemCount=2}"`

## <a name="sample-data-works-with-datatemplates"></a>Los datos de ejemplo funcionan con las datatemplates

Los datos de ejemplo funcionan para los controles ListBox, ListView o DataGrid cuando se usan plantillas de datos. La característica Datos de ejemplo analizará datatemplate e intentará generar los datos adecuados para ella. Los datos de ejemplo solo se generarán para los elementos de DataTemplates que usan enlaces. Los datos de ejemplo se generarán incluso si los enlaces aún no tienen un origen.
Por ejemplo:

```xml
<ListView d:ItemsSource="{d:SampleData ItemCount=3}">
     <ListView.ItemTemplate>
        <DataTemplate>
            <StackPanel Orientation="Horizontal">
                <Image Width="50" Source="{Binding ProfilePicture}"/>
                <StackPanel Orientation="Vertical">
                    <TextBlock Text="{Binding FirstName}" Margin="5"/>
                    <Label Content="{Binding LastName}"/>
                </StackPanel>
            </StackPanel>
        </DataTemplate>
    </ListView.ItemTemplate>
</ListView>
```

[![Vista de lista de datos de ejemplo con una clase DataTemplate](media\xaml-sample-data-templated-listview.png "Datos de ejemplo usados en un control ListView con una clase DataTemplate")](media\xaml-sample-data-templated-listview.png#lightbox)

## <a name="enable-sample-data-with-suggested-actions"></a>Habilitación de datos de ejemplo con acciones sugeridas

Para habilitar o deshabilitar fácilmente datos de ejemplo para un control desde el diseñador, puede usar la característica Acciones sugeridas. Acciones sugeridas es una bombilla en el diseñador que se muestra en la parte superior derecha al seleccionar un control. Para habilitar datos de ejemplo, seleccione el control , haga clic en la bombilla y, a continuación, haga clic en `Show Sample Data` . Por ejemplo:

[![Acciones sugeridas de datos de ejemplo](media\xaml-sample-data-suggested-actions.png "Habilitar datos de ejemplo con acciones sugeridas")](media\xaml-sample-data-suggested-actions.png#lightbox)

## <a name="sample-data-with-ivalueconverters"></a>Datos de ejemplo con IValueConverters 

Los convertidores no son totalmente compatibles con la característica Datos de ejemplo. Sin embargo, puede conseguir que funcione haciendo una o ambas de las siguientes acciones:
- Asegúrese de que la `Convert` función puede controlar un escenario en el que el valor ya es su targetType.

- Implemente `ConvertBack` la función que convertirá el valor al tipo original. 

## <a name="troubleshooting"></a>Solución de problemas

Si los datos de ejemplo no muestran nada o no muestran el tipo correcto, puede intentar actualizar el diseñador o cerrar y volver a abrir la página.

Si experimenta un problema que no aparece en esta sección o no se puede solucionar actualizando la página, háganoslo saber mediante la herramienta Notificar [un problema.](../ide/how-to-report-a-problem-with-visual-studio.md)

### <a name="requirements"></a>Requisitos

- Los datos de ejemplo Visual Studio la versión [16.10](/visualstudio/releases/2019/release-notes-v16.10) de 2019 o posterior.

- Admite proyectos de escritorio de Windows Windows Presentation Foundation (WPF) para .NET Core o .NET Framework cuando se usa el nuevo diseñador. Para habilitar el nuevo diseñador para .NET Framework vaya a Herramientas > Opciones de > Environment > Preview Features (Herramientas > Opciones de > Environment > Preview Features), seleccione New WPF Diseñador XAML for .NET Framework (Nuevas características de WPF Diseñador XAML para .NET Framework y, a continuación, reinicie Visual Studio.

## <a name="see-also"></a>Consulte también

- [Propiedades en tiempo de diseño de XAML](/xaml/xaml-tools/xaml/xaml-designtime-data)
- [XAML en aplicaciones de WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [XAML en aplicaciones de UWP](/windows/uwp/xaml-platform/xaml-overview)
- [XAML en aplicaciones de Xamarin.Forms](/xamarin/xamarin-forms/xaml/)