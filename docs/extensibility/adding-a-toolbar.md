---
title: Adición de una barra de herramientas ( Toolbar) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding to IDE
- IDE, adding toolbars
ms.assetid: 17302c25-6f59-4e97-8c85-54f95336a07f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 655cd87fe59cf4f42361cc24a63eb56653caae1a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740221"
---
# <a name="add-a-toolbar"></a>Añadir una barra de herramientas
En este tutorial se muestra cómo agregar una barra de herramientas al IDE de Visual Studio.

 Una barra de herramientas es una franja horizontal o vertical que contiene botones enlazados a comandos. Dependiendo de su implementación, una barra de herramientas en el IDE se puede cambiar de posición, acoplar en cualquier lado de la ventana principal del IDE o hacer que permanezca delante de otras ventanas.

 Además, los usuarios pueden agregar comandos a una barra de herramientas o quitarlos de ella mediante el cuadro de diálogo **Personalizar.** Normalmente, las barras de herramientas de VSPackages son personalizables por el usuario. El IDE controla toda la personalización y el VSPackage responde a los comandos. El VSPackage no tiene que saber dónde se encuentra físicamente un comando.

 Para obtener más información acerca de los menús, consulte [Comandos, menús y barras](../extensibility/internals/commands-menus-and-toolbars.md)de herramientas .

## <a name="prerequisites"></a>Prerrequisitos
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en la configuración de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [Instalar el SDK](../extensibility/installing-the-visual-studio-sdk.md)de Visual Studio .

## <a name="create-an-extension-with-a-toolbar"></a>Crear una extensión con una barra de herramientas
 Cree un proyecto `IDEToolbar`VSIX denominado . Agregue una plantilla de elemento de comando de menú denominada **ToolbarTestCommand**. Para obtener información sobre cómo hacerlo, consulte [Crear una extensión con un comando](../extensibility/creating-an-extension-with-a-menu-command.md)de menú .

## <a name="create-a-toolbar-for-the-ide"></a>Crear una barra de herramientas para el IDE

1. En *ToolbarTestCommandPackage.vsct*, busque la sección Símbolos. En el guidSymbol elemento denominado guidToolbarTestCommandPackageCmdSet, agregue declaraciones para una barra de herramientas y un grupo de barra de herramientas, como se indica a continuación.

    ```xml
    <IDSymbol name="Toolbar" value="0x1000" />
    <IDSymbol name="ToolbarGroup" value="0x1050" />

    ```

2. En la parte superior de la sección Comandos, cree una sección Menús. Agregue un elemento Menu a la sección Menus para definir la barra de herramientas.

    ```xml
    <Menus>
        <Menu guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"
            type="Toolbar" >
            <CommandFlag>DefaultDocked</CommandFlag>
            <Strings>
                <ButtonText>Test Toolbar</ButtonText>
                <CommandName>Test Toolbar</CommandName>
            </Strings>
          </Menu>
    </Menus>
    ```

     Las barras de herramientas no se pueden anidar como submenús. Por lo tanto, no es necesario asignar un grupo primario. Además, no es necesario establecer una prioridad, ya que el usuario puede mover barras de herramientas. Normalmente, la ubicación inicial de una barra de herramientas se define mediante programación, pero se conservan los cambios posteriores realizados por el usuario.

3. En la sección [Grupos,](../extensibility/groups-element.md) después de la entrada de grupo existente, defina un elemento [Group](../extensibility/group-element.md) que contenga los comandos de la barra de herramientas.

    ```xml
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"
          priority="0x0000">
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>
    </Group>
    ```

4. Haga que el botón aparezca en la barra de herramientas. En la sección Botones, reemplace el bloque Padre del botón a la barra de herramientas. El bloque Button resultante debería tener este aspecto:

    ```xml
    <Button guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarTestCommandId" priority="0x0100" type="Button">
        <Parent guid= "guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup" />
                <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ToolbarTestCommand</ButtonText>
        </Strings>
    </Button>
    ```

     De forma predeterminada, si una barra de herramientas no tiene comandos, no aparece.

5. Compile la solución y comience la depuración. Debería aparecer la instancia experimental.

6. Haga clic con el botón derecho en la barra de menús de Visual Studio para obtener la lista de barras de herramientas. Seleccione **Probar barra de herramientas**.

7. Ahora debería ver la barra de herramientas como un icono a la derecha del icono Buscar en archivos. Al hacer clic en el icono, debería ver un cuadro de mensaje que dice **ToolbarTestCommandPackage. En El interior de IDEToolbar.ToolbarTestCommand.MenuItemCallback()**.

## <a name="see-also"></a>Vea también
- [Comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md)
