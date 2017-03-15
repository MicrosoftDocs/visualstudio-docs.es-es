---
title: "Agregar comandos de Visual Studio a una página de inicio | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: c75d9b41d0e51d6db2e78d0afa0e1ddf37e87b8a
ms.lasthandoff: 02/22/2017

---
# <a name="adding-visual-studio-commands-to-a-start-page"></a>Agregar comandos de Visual Studio a una página de inicio
Cuando se crea una página principal personalizada, puede agregar comandos de Visual Studio a él. Este documento describen las distintas formas de enlazar a objetos XAML en una página de inicio de comandos de Visual Studio.  
  
 Para obtener más información acerca de los comandos en XAML, vea [introducción de comandos](http://msdn.microsoft.com/Library/bc208dfe-367d-426a-99de-52b7e7511e81)  
  
## <a name="adding-commands-from-the-command-well"></a>Agregar comandos desde el comando también  
 La página de inicio que se creó en [crear una página de inicio personalizada](../extensibility/creating-a-custom-start-page.md) agregado el <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName>y <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName>espacios de nombres, como se indica a continuación.</xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> </xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName>  
  
```  
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
```  
  
 Agregue otro espacio de nombres para Microsoft.VisualStudio.Shell desde el ensamblado Microsoft.VisualStudio.Shell.Immutable.11.0.dll. (Necesitará agregar una referencia a este ensamblado en el proyecto.)  
  
```xml  
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"  
```  
  
 Puede usar el `vscom:` alias para enlazar comandos de Visual Studio a XAML a los controles de la página estableciendo la <xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A>propiedad del control `vscom:VSCommands.ExecuteCommand`.</xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A> A continuación, puede establecer el <xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A>en el nombre del comando para ejecutar, como se muestra en el ejemplo siguiente.</xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A>  
  
```xml  
<Button Name="btnNewProj" Content="New Project"   
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
    CommandParameter="File.NewProject" >  
</Button>  
```  
  
> [!NOTE]
>  El `x:` alias, que hace referencia al esquema XAML, es necesario al principio de todos los comandos.  
  
 Puede establecer el valor de la `Command` propiedad cualquier comando al que puede obtenerse acceso desde el **comando** ventana. Para obtener una lista de comandos disponibles, consulte [alias de comandos de Visual Studio](../ide/reference/visual-studio-command-aliases.md).  
  
 Si el comando para agregar requiere un parámetro adicional, puede agregar al valor de la `CommandParameter` propiedad. Parámetros separados de los comandos mediante el uso de espacios en blanco, tal como se muestra en el ejemplo siguiente.  
  
```xml  
<Button Content="Web Search"   
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
        CommandParameter="View.WebBrowser www.bing.com" />  
```  
  
### <a name="calling-extensions-from-the-command-well"></a>Llamar a las extensiones desde el comando también  
 Puede llamar a comandos de VSPackages registrado utilizando la misma sintaxis que se utiliza para llamar a otros comandos de Visual Studio. Por ejemplo, si agrega un VSPackage instalado un **página principal** comando a la **vista** menú, puede llamar a ese comando estableciendo `CommandParameter` a `View.HomePage`.  
  
> [!NOTE]
>  Si se llama a un comando que está asociado a un paquete VSPackage, el paquete debe cargarse cuando se invoca el comando.  
  
## <a name="adding-commands-from-assemblies"></a>Agregar comandos de ensamblados  
 Para llamar a un comando de un ensamblado, o al código de acceso en un VSPackage que no está asociado a un comando de menú, debe crear un alias para el ensamblado y, a continuación, llame el alias.  
  
#### <a name="to-call-a-command-from-an-assembly"></a>Para llamar a un comando desde un ensamblado  
  
1.  En la solución, agregue una referencia al ensamblado.  
  
2.  En la parte superior del archivo StartPage.xaml, agregue una directiva de espacio de nombres para el ensamblado, tal como se muestra en el ejemplo siguiente.  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3.  Invocar el comando estableciendo el `Command` propiedad de un objeto XAML, como se muestra en el ejemplo siguiente.  
  
     XAML  
  
    ```  
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>  
    ```  
  
> [!NOTE]
>  Debe copiar el ensamblado y, a continuación, péguelo en... \\ *Carpeta de instalación de visual Studio*\Common7\IDE\PrivateAssemblies\ para asegurarse de que esté cargado antes de que se llama.  
  
## <a name="adding-commands-with-the-dte-object"></a>Agregar comandos con el objeto DTE  
 Puede acceder al objeto DTE desde una página de inicio, en el marcado y en código.  
  
 En el marcado, puede tener acceso mediante el uso de la [enlazar extensión de marcado](http://msdn.microsoft.com/Library/83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63) sintaxis para llamar a la <xref:EnvDTE.DTE>objeto.</xref:EnvDTE.DTE> Puede utilizar este método para enlazar a propiedades sencillas, como los que devuelven colecciones, pero no se puede enlazar a los métodos o servicios. El ejemplo siguiente muestra un <xref:System.Windows.Controls.TextBlock>control que se enlaza a la <xref:EnvDTE._DTE.Name%2A>propiedad y un <xref:System.Windows.Controls.ListBox>control que enumera el <xref:EnvDTE.Window.Caption%2A>Propiedades de la colección devuelta por la <xref:EnvDTE._DTE.Windows%2A>propiedad.</xref:EnvDTE._DTE.Windows%2A> </xref:EnvDTE.Window.Caption%2A> </xref:System.Windows.Controls.ListBox> </xref:EnvDTE._DTE.Name%2A> </xref:System.Windows.Controls.TextBlock>  
  
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
  
 Para obtener un ejemplo, vea [Tutorial: guardar la configuración de usuario en una página de inicio](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md).  
  
## <a name="see-also"></a>Vea también  
 [Agregar Control de usuario a la página de inicio](../extensibility/adding-user-control-to-the-start-page.md)
