---
title: Agregar Visual Studio comandos a una página de inicio | Microsoft Docs
description: Obtenga información sobre las distintas formas de enlazar Visual Studio comandos a objetos XAML en una página de inicio personalizada en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 0bf0f9a3db21dd93b1a497731bca9142a4377acc
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901518"
---
# <a name="add-visual-studio-commands-to-a-start-page"></a>Agregar Visual Studio comandos a una página de inicio

Al crear una página de inicio personalizada, puede agregarle Visual Studio comandos. En este documento se de abordan las distintas formas de enlazar Visual Studio comandos a objetos XAML en una página de inicio.

Para obtener más información sobre los comandos en XAML, vea [Información general sobre comandos.](/dotnet/framework/wpf/advanced/commanding-overview)

## <a name="add-commands-from-the-command-well"></a>Agregar comandos desde el cuadro de comandos

La página de inicio creada en [Crear una página de inicio personalizada](../extensibility/creating-a-custom-start-page.md) agregó los espacios de nombres y , como se muestra a <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName> <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> continuación.

```xml
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
```

Agregue otro espacio de nombres para Microsoft.VisualStudio.Shell desde el ensamblado *Microsoft.VisualStudio.Shell.Immutable.11.0.dll*. (Es posible que tenga que agregar una referencia a este ensamblado en el proyecto).

```xml
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"
```

Puede usar el alias para enlazar Visual Studio comandos a controles XAML en la página estableciendo la propiedad `vscom:` <xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A> del control en `vscom:VSCommands.ExecuteCommand` . A continuación, puede <xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A> establecer la propiedad en el nombre del comando que se va a ejecutar, como se muestra en el ejemplo siguiente.

```xml
<Button Name="btnNewProj" Content="New Project"
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"
    CommandParameter="File.NewProject" >
</Button>
```

> [!NOTE]
> El `x:` alias, que hace referencia al esquema XAML, es necesario al principio de todos los comandos.

 Puede establecer el valor de la propiedad en cualquier comando al que se pueda acceder `Command` desde la **ventana** Comando. Para obtener una lista de los comandos disponibles, [vea Visual Studio alias de comando .](../ide/reference/visual-studio-command-aliases.md)

 Si el comando para agregar requiere un parámetro adicional, puede agregarlo al valor de la `CommandParameter` propiedad . Separe los parámetros de los comandos mediante espacios, como se muestra en el ejemplo siguiente.

```xml
<Button Content="Web Search"
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"
        CommandParameter="View.WebBrowser www.bing.com" />
```

### <a name="call-extensions-from-the-command-well"></a>Llamar a extensiones desde el cuadro de comandos
 Puede llamar a comandos desde VSPackages registrados mediante la misma sintaxis que se usa para llamar a otros Visual Studio comandos. Por ejemplo, si un VSPackage instalado agrega  un comando Página principal al menú Ver, puede llamar **a** ese comando estableciendo `CommandParameter` en `View.HomePage` .

> [!NOTE]
> Si llama a un comando asociado a un VSPackage, el paquete se debe cargar cuando se invoca el comando.

## <a name="add-commands-from-assemblies"></a>Adición de comandos desde ensamblados
 Para llamar a un comando desde un ensamblado o para obtener acceso al código de un VSPackage que no está asociado a un comando de menú, debe crear un alias para el ensamblado y, a continuación, llamar al alias.

### <a name="to-call-a-command-from-an-assembly"></a>Para llamar a un comando desde un ensamblado

1. En la solución, agregue una referencia al ensamblado.

2. En la parte superior del *archivo StartPage.xaml,* agregue una directiva de espacio de nombres para el ensamblado, como se muestra en el ejemplo siguiente.

    ```xml
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"
    ```

3. Invoque el comando `Command` estableciendo la propiedad de un objeto XAML, como se muestra en el ejemplo siguiente.

     Xaml

    ```
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>
    ```

> [!NOTE]
> Debe copiar el ensamblado y, a continuación, pegarlo en *.. \\ {Visual Studio carpeta de instalación}\Common7\IDE\PrivateAssemblies para asegurarse de que se carga antes \* de llamarla.

## <a name="add-commands-with-the-dte-object"></a>Adición de comandos con el objeto DTE
 Puede acceder al objeto DTE desde una página de inicio, tanto en el marcado como en el código.

 En el marcado, puede acceder a él mediante la sintaxis [de extensión de marcado de](/dotnet/framework/wpf/advanced/binding-markup-extension) enlace para llamar al objeto <xref:EnvDTE.DTE> . Puede usar este enfoque para enlazar a propiedades simples como las que devuelven colecciones, pero no puede enlazar a métodos o servicios. En el ejemplo siguiente se muestra un control que se enlaza a la propiedad y un control que enumera las propiedades de la colección <xref:System.Windows.Controls.TextBlock> <xref:EnvDTE._DTE.Name%2A> <xref:System.Windows.Controls.ListBox> devueltas <xref:EnvDTE.Window.Caption%2A> por la propiedad <xref:EnvDTE._DTE.Windows%2A> .

```xml
<TextBlock Text="{Binding Path=DTE.Name}" FontSize="12" HorizontalAlignment="Center"/>
<ListBox ItemsSource="{Binding Path=DTE.Windows}">
    <ListBox.ItemTemplate>
        <DataTemplate>
            <TextBlock Text="{Binding Path=Caption}"/>
        </DataTemplate>
    </ListBox.ItemTemplate>
</ListBox
```

 Para obtener un ejemplo, vea [Tutorial: Guardar la configuración de usuario en una página de inicio](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md).

## <a name="see-also"></a>Consulta también

- [Agregar control de usuario a la página de inicio](../extensibility/adding-user-control-to-the-start-page.md)
