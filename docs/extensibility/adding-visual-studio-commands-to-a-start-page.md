---
title: Adición de comandos de Visual Studio a una página de inicio de visualía . Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 13dd40006039209b06cc6a71760fdbaa240db4fe
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740118"
---
# <a name="add-visual-studio-commands-to-a-start-page"></a>Agregar comandos de Visual Studio a una página de inicio

Al crear una página de inicio personalizada, puede agregarle comandos de Visual Studio. En este documento se describen las diferentes formas de enlazar comandos de Visual Studio a objetos XAML en una página de inicio.

Para obtener más información acerca de los comandos en XAML, vea [Información general sobre comandos](/dotnet/framework/wpf/advanced/commanding-overview)

## <a name="add-commands-from-the-command-well"></a>Añadir comandos desde el pozo de comandos

La página de inicio creada en <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName> Crear <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> una página de [inicio personalizada](../extensibility/creating-a-custom-start-page.md) agregó los espacios de nombres y, como se indica a continuación.

```xml
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
```

Agregue otro espacio de nombres para Microsoft.VisualStudio.Shell desde el ensamblado *Microsoft.VisualStudio.Shell.Immutable.11.0.dll*. (Es posible que deba agregar una referencia a este ensamblado en el proyecto.)

```xml
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"
```

Puede usar `vscom:` el alias para enlazar comandos de Visual <xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A> Studio a controles `vscom:VSCommands.ExecuteCommand`XAML en la página estableciendo la propiedad del control en . A continuación, <xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A> puede establecer la propiedad en el nombre del comando que se va a ejecutar, como se muestra en el ejemplo siguiente.

```xml
<Button Name="btnNewProj" Content="New Project"
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"
    CommandParameter="File.NewProject" >
</Button>
```

> [!NOTE]
> El `x:` alias, que hace referencia al esquema XAML, es necesario al principio de todos los comandos.

 Puede establecer el valor `Command` de la propiedad en cualquier comando al que se pueda tener acceso desde la ventana **Comando.** Para obtener una lista de los comandos disponibles, vea Alias de [comandos](../ide/reference/visual-studio-command-aliases.md)de Visual Studio .

 Si el comando que se va a agregar requiere un `CommandParameter` parámetro adicional, puede agregarlo al valor de la propiedad. Separe los parámetros de los comandos mediante espacios, como se muestra en el ejemplo siguiente.

```xml
<Button Content="Web Search"
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"
        CommandParameter="View.WebBrowser www.bing.com" />
```

### <a name="call-extensions-from-the-command-well"></a>Extensiones de llamada desde el pozo de comandos
 Puede llamar a comandos de VSPackages registrados mediante la misma sintaxis que se usa para llamar a otros comandos de Visual Studio. Por ejemplo, si un VSPackage instalado agrega un comando **de página principal** al menú **Ver,** puede llamar a ese comando estableciendo `CommandParameter` en `View.HomePage`.

> [!NOTE]
> Si llama a un comando asociado a un VSPackage, el paquete debe cargarse cuando se invoca el comando.

## <a name="add-commands-from-assemblies"></a>Agregar comandos desde ensamblados
 Para llamar a un comando desde un ensamblado o para tener acceso al código de un VSPackage que no está asociado a un comando de menú, debe crear un alias para el ensamblado y, a continuación, llamar al alias.

### <a name="to-call-a-command-from-an-assembly"></a>Para llamar a un comando desde un ensamblado

1. En la solución, agregue una referencia al ensamblado.

2. En la parte superior del archivo *StartPage.xaml,* agregue una directiva de espacio de nombres para el ensamblado, como se muestra en el ejemplo siguiente.

    ```xml
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"
    ```

3. Invoque el `Command` comando estableciendo la propiedad de un objeto XAML, como se muestra en el ejemplo siguiente.

     Xaml

    ```
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>
    ```

> [!NOTE]
> Debe copiar el ensamblado y, a continuación, pegarlo en *.. \\Para asegurarse de que se carga antes de llamara, para asegurarse de que se carga antes de llamarla.\*

## <a name="add-commands-with-the-dte-object"></a>Añadir comandos con el objeto DTE
 Puede tener acceso al objeto DTE desde una página de inicio, tanto en el marcado como en el código.

 En el marcado, puede tener acceso a él <xref:EnvDTE.DTE> mediante el uso de la extensión de [marcado](/dotnet/framework/wpf/advanced/binding-markup-extension) de enlace sintaxis para llamar al objeto. Puede usar este enfoque para enlazar a propiedades simples como las que devuelven colecciones, pero no puede enlazar a métodos o servicios. En el ejemplo <xref:System.Windows.Controls.TextBlock> siguiente se muestra <xref:EnvDTE._DTE.Name%2A> un control <xref:System.Windows.Controls.ListBox> que se enlaza <xref:EnvDTE.Window.Caption%2A> a la propiedad y <xref:EnvDTE._DTE.Windows%2A> un control que enumera las propiedades de la colección devuelta por la propiedad.

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

 Para obtener un ejemplo, vea [Tutorial: Guardar la configuración](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)de usuario en una página de inicio .

## <a name="see-also"></a>Vea también

- [Adición de control de usuario a la página de inicio](../extensibility/adding-user-control-to-the-start-page.md)
