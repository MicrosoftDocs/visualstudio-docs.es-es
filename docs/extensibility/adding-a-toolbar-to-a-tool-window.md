---
title: "Agregar una barra de herramientas a una ventana de herramientas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ventanas de herramientas, agregar barras de herramientas"
  - "barras de herramientas [Visual Studio], agregar a las ventanas de herramientas"
ms.assetid: 172f64b3-87f8-4292-9c1c-65bffa2b0970
caps.latest.revision: 48
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 48
---
# Agregar una barra de herramientas a una ventana de herramientas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este tutorial muestra cómo agregar una barra de herramientas a una ventana de herramientas.  
  
 Una barra de herramientas es una barra horizontal o vertical que contiene botones que se enlaza a los comandos. La longitud de una barra de herramientas en una ventana de herramientas siempre es el mismo que el ancho o alto de la ventana de herramientas, dependiendo de dónde se acopla la barra de herramientas.  
  
 A diferencia de las barras de herramientas en el IDE, una barra de herramientas en una ventana de herramientas debe acoplarse y no se puede mover o personalizado. Si el VSPackage se escribe en código umanaged, la barra de herramientas se puede acoplar en un borde.  
  
 Para obtener más información sobre cómo agregar una barra de herramientas, consulte [Agregar una barra de herramientas](../extensibility/adding-a-toolbar.md).  
  
## Requisitos previos  
 Para seguir este tutorial, debe instalar el SDK de Visual Studio. Para obtener más información, consulta [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## Creación de una barra de herramientas para una ventana de herramientas  
  
1.  Cree un proyecto VSIX denominado `TWToolbar` que tiene un comando de menú llamado **TWTestCommand** y una ventana de herramientas denominado **TestToolWindow**. Para obtener más información, vea [Crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md) y [Crear una extensión con una ventana de herramientas](../extensibility/creating-an-extension-with-a-tool-window.md). Debe agregar la plantilla de elemento de comando antes de agregar la plantilla de la ventana de herramienta.  
  
2.  En TWTestCommandPackage.vsct, busque la sección de símbolos. En el nodo GuidSymbol denominado guidTWTestCommandPackageCmdSet declarar una barra de herramientas y un grupo de la barra de herramientas, como sigue.  
  
    ```xml  
    <IDSymbol name="TWToolbar" value="0x1000" />  
    <IDSymbol name="TWToolbarGroup" value="0x1050" />  
    ```  
  
3.  En la parte superior de la `Commands` debe crearse un `Menus` sección. Agregar un `Menu` elemento para definir la barra de herramientas.  
  
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
  
     No se pueden anidar las barras de herramientas como submenús. Por lo tanto, no es necesario asignar a un elemento primario. Además, no es necesario establecer una prioridad, porque el usuario puede mover las barras de herramientas. Normalmente, la ubicación inicial de una barra de herramientas se define mediante programación, pero se conservan los cambios posteriores por el usuario.  
  
4.  En la sección grupos, definir un grupo para que contenga los comandos de la barra de herramientas.  
  
    ```xml  
  
    <Group guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" priority="0x0000">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" />  
    </Group>  
    ```  
  
5.  En la sección de botones, cambiar al elemento primario del elemento Button existente para el grupo de la barra de herramientas para que se mostrará la barra de herramientas.  
  
    ```xml  
    <Button guid="guidTWTestCommandPackageCmdSet" id="TWTestCommandId" priority="0x0100" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke TWTestCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
     De forma predeterminada, si una barra de herramientas no tiene comandos, no aparece.  
  
     Dado que la nueva barra de herramientas no se agrega automáticamente a la ventana de herramientas, la barra de herramientas debe agregarse explícitamente. Esta técnica se analiza en la sección siguiente.  
  
## Agregar la barra de herramientas a la ventana de herramientas  
  
1.  En TWTestCommandPackageGuids.cs agregue las siguientes líneas.  
  
    ```c#  
    public const string guidTWTestCommandPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file  
    public const int TWToolbar = 0x1000;  
    ```  
  
2.  En TestToolWindow.cs, agregue la siguiente instrucción using.  
  
    ```c#  
    using System.ComponentModel.Design;  
    ```  
  
3.  En el constructor de TestToolWindow, agregue la siguiente línea.  
  
    ```c#  
    this.ToolBar = new CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), TWTestCommandPackageGuids.TWToolbar);  
    ```  
  
## Probar la barra de herramientas en la ventana de herramientas  
  
1.  Compile la solución y comience la depuración. Debe aparecer la instancia experimental de Visual Studio.  
  
2.  En el **vista y otras ventanas** menú, haga clic en **ventana de herramientas de prueba** para mostrar la ventana de herramientas.  
  
     Verá una barra de herramientas \(parece que el icono predeterminado\) en la parte superior izquierda de la ventana de herramienta, justo debajo del título.  
  
3.  En la barra de herramientas, haga clic en el icono para mostrar el mensaje **TWTestCommandPackage en TWToolbar.TWTestCommand.MenuItemCallback\(\)**.  
  
## Vea también  
 [Agregar una barra de herramientas](../extensibility/adding-a-toolbar.md)