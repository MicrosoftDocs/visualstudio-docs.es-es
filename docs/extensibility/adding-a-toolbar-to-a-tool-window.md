---
title: Adición de una barra de herramientas a una ventana de herramientas ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding toolbars
- toolbars [Visual Studio], adding to tool windows
ms.assetid: 172f64b3-87f8-4292-9c1c-65bffa2b0970
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 094515eb94279623974bd7b55cc9923c49625a70
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740246"
---
# <a name="add-a-toolbar-to-a-tool-window"></a>Añadir una barra de herramientas a una ventana de herramientas
En este tutorial se muestra cómo agregar una barra de herramientas a una ventana de herramientas.

 Una barra de herramientas es una franja horizontal o vertical que contiene botones enlazados a comandos. La longitud de una barra de herramientas en una ventana de herramientas es siempre la misma que la anchura o la altura de la ventana de herramientas, dependiendo de dónde esté acoplada la barra de herramientas.

 A diferencia de las barras de herramientas del IDE, una barra de herramientas de una ventana de herramientas debe estar acoplada y no se puede mover ni personalizar. Si el VSPackage se escribe en código uadministrado, la barra de herramientas se puede acoplar en cualquier borde.

 Para obtener más información sobre cómo agregar una barra de herramientas, consulte [Agregar una barra](../extensibility/adding-a-toolbar.md)de herramientas .

## <a name="prerequisites"></a>Prerrequisitos
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en la configuración de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [Instalar el SDK](../extensibility/installing-the-visual-studio-sdk.md)de Visual Studio .

## <a name="create-a-toolbar-for-a-tool-window"></a>Crear una barra de herramientas para una ventana de herramientas

1. Cree un proyecto `TWToolbar` VSIX denominado que tenga un comando de menú denominado **TWTestCommand** y una ventana de herramientas denominada **TestToolWindow**. Para obtener más información, consulte [Crear una extensión con un comando](../extensibility/creating-an-extension-with-a-menu-command.md) de menú y Crear una extensión con una ventana de [herramientas.](../extensibility/creating-an-extension-with-a-tool-window.md) Debe agregar la plantilla de elemento de comando antes de agregar la plantilla de ventana de herramientas.

2. En *TWTestCommandPackage.vsct*, busque la sección Symbols. En el GuidSymbol nodo denominado guidTWTestCommandPackageCmdSet declarar una barra de herramientas y un grupo de barra de herramientas, como se indica a continuación.

    ```xml
    <IDSymbol name="TWToolbar" value="0x1000" />
    <IDSymbol name="TWToolbarGroup" value="0x1050" />
    ```

3. En la parte `Commands` superior de `Menus` la sección, cree una sección. Agregue `Menu` un elemento para definir la barra de herramientas.

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

     Las barras de herramientas no se pueden anidar como submenús. Por lo tanto, no es posible asignar un elemento primario. Además, no tiene que establecer una prioridad, ya que el usuario puede mover barras de herramientas. Normalmente, la ubicación inicial de una barra de herramientas se define mediante programación, pero se conservan los cambios posteriores realizados por el usuario.

4. En la sección Grupos, defina un grupo que contenga los comandos de la barra de herramientas.

    ```xml

    <Group guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" priority="0x0000">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" />
    </Group>
    ```

5. En la sección Botones, cambie el elemento primario del elemento Button existente al grupo de barra de herramientas para que se muestre la barra de herramientas.

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

## <a name="add-the-toolbar-to-the-tool-window"></a>Agregue la barra de herramientas a la ventana de herramientas

1. En *TWTestCommandPackageGuids.cs* agregue las siguientes líneas.

    ```csharp
    public const string guidTWTestCommandPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file
    public const int TWToolbar = 0x1000;
    ```

2. En *TestToolWindow.cs* agregue la siguiente instrucción using.

    ```csharp
    using System.ComponentModel.Design;
    ```

3. En el TestToolWindow constructor agregue la siguiente línea.

    ```csharp
    this.ToolBar = new CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), TWTestCommandPackageGuids.TWToolbar);
    ```

## <a name="test-the-toolbar-in-the-tool-window"></a>Pruebe la barra de herramientas en la ventana de herramientas

1. Compile la solución y comience la depuración. Debe aparecer la instancia experimental de Visual Studio.

2. En el menú **Ver / Otras ventanas,** haga clic en **Probar Ventana de herramienta** para mostrar la ventana de herramientas.

     Debería ver una barra de herramientas (parece el icono predeterminado) en la parte superior izquierda de la ventana de herramientas, justo debajo del título.

3. En la barra de herramientas, haga clic en el icono para mostrar el mensaje **TWTestCommandPackage Inside TWToolbar.TWTestCommand.MenuItemCallback()**.

## <a name="see-also"></a>Vea también
- [Añadir una barra de herramientas](../extensibility/adding-a-toolbar.md)
