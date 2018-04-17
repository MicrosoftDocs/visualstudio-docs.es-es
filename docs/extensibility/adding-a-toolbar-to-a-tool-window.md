---
title: Agregar una barra de herramientas a una ventana de herramientas | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding toolbars
- toolbars [Visual Studio], adding to tool windows
ms.assetid: 172f64b3-87f8-4292-9c1c-65bffa2b0970
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 47ff5f69ff559ea1c08d0ae9bdd7192a257c844e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="adding-a-toolbar-to-a-tool-window"></a>Agregar una barra de herramientas a una ventana de herramientas
Este tutorial muestra cómo agregar una barra de herramientas a una ventana de herramientas.  
  
 Una barra de herramientas es una barra horizontal o vertical que contiene botones que se enlaza a los comandos. La longitud de una barra de herramientas en una ventana de herramientas siempre es el mismo que el ancho o alto de la ventana de herramientas, dependiendo de dónde se acopla la barra de herramientas.  
  
 A diferencia de las barras de herramientas en el IDE, una barra de herramientas en una ventana de herramientas debe acoplarse y no puede moverse o personalizado. Si se ha escrito el VSPackage en código umanaged, la barra de herramientas se puede acoplar en un borde.  
  
 Para obtener más información sobre cómo agregar una barra de herramientas, consulte [agregar una barra de herramientas](../extensibility/adding-a-toolbar.md).  
  
## <a name="prerequisites"></a>Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-toolbar-for-a-tool-window"></a>Crear una barra de herramientas de una ventana de herramientas  
  
1.  Crear un proyecto VSIX denominado `TWToolbar` que tiene un comando de menú denominado **TWTestCommand** y una ventana de herramientas denominado **TestToolWindow**. Para obtener más información, consulte [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md) y [crear una extensión con una ventana de herramientas](../extensibility/creating-an-extension-with-a-tool-window.md). Debe agregar la plantilla de elemento de comando antes de agregar la plantilla de la ventana de herramienta.  
  
2.  En TWTestCommandPackage.vsct, busque la sección de símbolos. En el nodo de GuidSymbol denominado guidTWTestCommandPackageCmdSet declarar una barra de herramientas y un grupo de la barra de herramientas, como se indica a continuación.  
  
    ```xml  
    <IDSymbol name="TWToolbar" value="0x1000" />  
    <IDSymbol name="TWToolbarGroup" value="0x1050" />  
    ```  
  
3.  En la parte superior de la `Commands` , debe crearse un `Menus` sección. Agregar un `Menu` elemento para definir la barra de herramientas.  
  
    ```xml  
    <Menus>  
        <Menu guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" type="ToolWindowToolbar">  
            <CommandFlag>DefaultDocked</CommandFlag>  
            <Strings>  
                <ButtonText>Test Toolbar</ButtonText>  
                <CommandName>Test Toolbar</CommandName>  
            </Strings>  
        </Menu>  
    </Menus>  
    ```  
  
     No se pueden anidar las barras de herramientas como submenús. Por lo tanto, no es necesario asignar a un elemento primario. Además, no es necesario establecer una prioridad, porque el usuario puede mover las barras de herramientas. Normalmente, la posición inicial de una barra de herramientas se define mediante programación, pero se conservan los cambios posteriores por el usuario.  
  
4.  En la sección grupos, defina un grupo para que contenga los comandos de la barra de herramientas.  
  
    ```xml  
  
    <Group guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" priority="0x0000">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" />  
    </Group>  
    ```  
  
5.  En la sección de botones, cambie al elemento primario del elemento de botón existente para el grupo de la barra de herramientas para que se mostrará la barra de herramientas.  
  
    ```xml  
    <Button guid="guidTWTestCommandPackageCmdSet" id="TWTestCommandId" priority="0x0100" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke TWTestCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
     De forma predeterminada, si una barra de herramientas no tiene ningún comando, no aparece.  
  
     Dado que la nueva barra de herramientas no se agrega automáticamente a la ventana de herramientas, la barra de herramientas debe agregarse explícitamente. Esta técnica se analiza en la sección siguiente.  
  
## <a name="adding-the-toolbar-to-the-tool-window"></a>Agregar la barra de herramientas a la ventana de herramientas  
  
1.  En TWTestCommandPackageGuids.cs agregue las líneas siguientes.  
  
    ```csharp  
    public const string guidTWTestCommandPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file  
    public const int TWToolbar = 0x1000;  
    ```  
  
2.  En TestToolWindow.cs agregue la siguiente instrucción using.  
  
    ```csharp  
    using System.ComponentModel.Design;  
    ```  
  
3.  En el constructor TestToolWindow agregue la línea siguiente.  
  
    ```csharp  
    this.ToolBar = new CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), TWTestCommandPackageGuids.TWToolbar);  
    ```  
  
## <a name="testing-the-toolbar-in-the-tool-window"></a>Probar la barra de herramientas en la ventana de herramientas  
  
1.  Compile la solución y comience la depuración. Debe aparecer la instancia experimental de Visual Studio.  
  
2.  En el **vista / otras ventanas** menú, haga clic en **ventana de herramientas de pruebas paralelas** para mostrar la ventana de herramientas.  
  
     Verá una barra de herramientas (parece que el icono predeterminado) en la parte superior izquierda de la ventana de herramientas, justo debajo del título.  
  
3.  En la barra de herramientas, haga clic en el icono para mostrar el mensaje **TWTestCommandPackage en TWToolbar.TWTestCommand.MenuItemCallback()**.  
  
## <a name="see-also"></a>Vea también  
 [Adición de una barra de herramientas](../extensibility/adding-a-toolbar.md)