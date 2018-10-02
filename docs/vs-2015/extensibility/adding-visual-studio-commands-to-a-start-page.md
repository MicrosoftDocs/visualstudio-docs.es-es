---
title: Adición de comandos de Visual Studio a una página de inicio | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b3625f64686265123cd0b7e6f432db47cd978ae3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47565878"
---
# <a name="adding-visual-studio-commands-to-a-start-page"></a>Adición de comandos de Visual Studio a una página de inicio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [agregar comandos de Microsoft Visual Studio a una página de inicio](https://docs.microsoft.com/visualstudio/extensibility/adding-visual-studio-commands-to-a-start-page).  
  
Cuando se crea una página principal personalizada, puede agregar comandos de Visual Studio a él. Este documento describen las distintas formas para enlazar comandos de Visual Studio con objetos XAML en una página de inicio.  
  
 Para obtener más información acerca de los comandos en XAML, vea [información general sobre comandos](http://msdn.microsoft.com/library/bc208dfe-367d-426a-99de-52b7e7511e81)  
  
## <a name="adding-commands-from-the-command-well"></a>Adición de comandos desde el comando también  
 Crea la página de inicio en [creación de una página de inicio personalizada](../extensibility/creating-a-custom-start-page.md) agrega el <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName> y <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> espacios de nombres, como se indica a continuación.  
  
```  
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
```  
  
 Agregue otro espacio de nombres para Microsoft.VisualStudio.Shell desde el ensamblado Microsoft.VisualStudio.Shell.Immutable.11.0.dll. (Es posible que deba agregar una referencia a este ensamblado en el proyecto.)  
  
```xml  
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"  
```  
  
 Puede usar el `vscom:` alias para enlazar comandos de Visual Studio con XAML se controla en la página estableciendo la <xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A> propiedad del control a `vscom:VSCommands.ExecuteCommand`. A continuación, puede establecer el <xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A> propiedad en el nombre de comando para ejecutar, como se muestra en el ejemplo siguiente.  
  
```xml  
<Button Name="btnNewProj" Content="New Project"   
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
    CommandParameter="File.NewProject" >  
</Button>  
```  
  
> [!NOTE]
>  El `x:` alias, lo que hace referencia al esquema XAML, es necesario al principio de todos los comandos.  
  
 Puede establecer el valor de la `Command` propiedad con cualquier comando que se puede acceder desde el **comando** ventana. Para obtener una lista de comandos disponibles, consulte [Visual Studio Command Aliases](../ide/reference/visual-studio-command-aliases.md).  
  
 Si el comando para agregar requiere un parámetro adicional, puede agregarlo al valor de la `CommandParameter` propiedad. Separan los parámetros de comandos mediante el uso de espacios en blanco, tal como se muestra en el ejemplo siguiente.  
  
```xml  
<Button Content="Web Search"   
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
        CommandParameter="View.WebBrowser www.bing.com" />  
```  
  
### <a name="calling-extensions-from-the-command-well"></a>Llamar a las extensiones desde el comando también  
 Puede llamar a comandos de VSPackages registrados mediante el uso de la misma sintaxis que se usa para llamar a otros comandos de Visual Studio. Por ejemplo, si agrega un VSPackage instalado un **página principal** comando a la **vista** menú, puede llamar a ese comando estableciendo `CommandParameter` a `View.HomePage`.  
  
> [!NOTE]
>  Si se llama a un comando que está asociado a un VSPackage, debe cargar el paquete cuando se invoca el comando.  
  
## <a name="adding-commands-from-assemblies"></a>Adición de comandos de los ensamblados  
 Para llamar a un comando desde un ensamblado, o al código de acceso en un VSPackage que no está asociado con un comando de menú, debe crear un alias para el ensamblado y, a continuación, llamar a lo alias.  
  
#### <a name="to-call-a-command-from-an-assembly"></a>Para llamar a un comando desde un ensamblado  
  
1.  En la solución, agregue una referencia al ensamblado.  
  
2.  En la parte superior del archivo StartPage.xaml, agregue una directiva de espacio de nombres para el ensamblado, tal como se muestra en el ejemplo siguiente.  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3.  Invoque el comando estableciendo el `Command` propiedad de un objeto XAML, como se muestra en el ejemplo siguiente.  
  
     XAML  
  
    ```  
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>  
    ```  
  
> [!NOTE]
>  Debe copiar el ensamblado y, a continuación, péguelo en... \\ *Carpeta de instalación de visual Studio*\Common7\IDE\PrivateAssemblies\ para asegurarse de que se carga antes de que se llama.  
  
## <a name="adding-commands-with-the-dte-object"></a>Adición de comandos con el objeto DTE  
 Puede acceder al objeto DTE desde una página de inicio tanto en el marcado en el código.  
  
 En el marcado, se puede acceder a ella mediante el [extensión de marcado de enlace](http://msdn.microsoft.com/library/83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63) sintaxis para llamar a la <xref:EnvDTE.DTE> objeto. Puede usar este enfoque para enlazar a propiedades sencillas, como los que devuelven colecciones, pero no se puede enlazar a los métodos o servicios. El ejemplo siguiente se muestra un <xref:System.Windows.Controls.TextBlock> control que se enlaza el <xref:EnvDTE._DTE.Name%2A> propiedad y un <xref:System.Windows.Controls.ListBox> control que enumera el <xref:EnvDTE.Window.Caption%2A> propiedades de la colección devuelta por la <xref:EnvDTE._DTE.Windows%2A> propiedad.  
  
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
  
 Para obtener un ejemplo, vea [Tutorial: Guardar configuración de usuario en una página de inicio](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md).  
  
## <a name="see-also"></a>Vea también  
 [Adición de control de usuario a la página de inicio](../extensibility/adding-user-control-to-the-start-page.md)

