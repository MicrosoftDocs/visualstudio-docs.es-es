---
title: Agregar una barra de herramientas | Microsoft Docs
description: Obtenga información sobre cómo agregar una barra de herramientas que contenga botones que estén enlazados a comandos al entorno de desarrollo integrado (IDE) de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- toolbars [Visual Studio], adding to IDE
- IDE, adding toolbars
ms.assetid: 17302c25-6f59-4e97-8c85-54f95336a07f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 62d32a07ec046bc42d69818346450e5a94a668ba
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951334"
---
# <a name="add-a-toolbar"></a>Agregar una barra de herramientas
En este tutorial se muestra cómo agregar una barra de herramientas al IDE de Visual Studio.

 Una barra de herramientas es una franja horizontal o vertical que contiene botones enlazados a comandos. En función de su implementación, se puede cambiar la posición de una barra de herramientas en el IDE, acoplar en cualquier lado de la ventana principal del IDE o hacer que permanezca delante de otras ventanas.

 Además, los usuarios pueden agregar comandos a una barra de herramientas o quitarlos de él mediante el cuadro de diálogo **personalizar** . Normalmente, las barras de herramientas de los VSPackages son personalizables por el usuario. El IDE controla toda la personalización y el VSPackage responde a los comandos. El VSPackage no tiene que saber dónde se encuentra un comando físicamente.

 Para obtener más información sobre los menús, vea [comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md).

## <a name="prerequisites"></a>Requisitos previos
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS después. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-toolbar"></a>Crear una extensión con una barra de herramientas
 Cree un proyecto VSIX denominado `IDEToolbar` . Agregue una plantilla de elemento de comando de menú denominada **ToolbarTestCommand**. Para obtener información sobre cómo hacerlo, vea [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="create-a-toolbar-for-the-ide"></a>Crear una barra de herramientas para el IDE

1. En *ToolbarTestCommandPackage. Vsct*, busque la sección Symbols. En el elemento GuidSymbol denominado guidToolbarTestCommandPackageCmdSet, agregue las declaraciones de una barra de herramientas y un grupo de barras de herramientas, como se indica a continuación.

    ```xml
    <IDSymbol name="Toolbar" value="0x1000" />
    <IDSymbol name="ToolbarGroup" value="0x1050" />

    ```

2. En la parte superior de la sección comandos, cree una sección de menús. Agregue un elemento de menú a la sección de menús para definir la barra de herramientas.

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

     Las barras de herramientas no se pueden anidar como submenús. Por lo tanto, no es necesario asignar un grupo primario. Además, no es necesario establecer una prioridad, ya que el usuario puede desplace las barras de herramientas. Normalmente, la posición inicial de una barra de herramientas se define mediante programación, pero se conservan los cambios subsiguientes del usuario.

3. En la sección [grupos](../extensibility/groups-element.md) , después de la entrada de grupo existente, defina un elemento de [Grupo](../extensibility/group-element.md) para que contenga los comandos de la barra de herramientas.

    ```xml
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"
          priority="0x0000">
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>
    </Group>
    ```

4. Haga que el botón aparezca en la barra de herramientas. En la sección botones, reemplace el bloque primario del botón a la barra de herramientas. El bloque de botón resultante debe tener el siguiente aspecto:

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

6. Haga clic con el botón secundario en la barra de menús de Visual Studio para obtener la lista de barras de herramientas. Seleccione la **barra de herramientas prueba**.

7. Ahora debería ver la barra de herramientas como un icono a la derecha del icono Buscar en archivos. Al hacer clic en el icono, debería ver un cuadro de mensaje que dice **ToolbarTestCommandPackage. Dentro de IDEToolbar. ToolbarTestCommand. MenuItemCallback ()**.

## <a name="see-also"></a>Vea también
- [Comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md)
