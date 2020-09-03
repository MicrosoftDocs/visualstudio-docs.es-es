---
title: Agregar un menú a la barra de menús | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
caps.latest.revision: 52
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 64ab627d785e8b00b5159969a01dc1102df30359
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184926"
---
# <a name="adding-a-menu-to-the-visual-studio-menu-bar"></a>Adición de un menú a la barra de menús de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tutorial se muestra cómo agregar un menú a la barra de menús del entorno de desarrollo integrado (IDE) de Visual Studio. La barra de menús del IDE contiene categorías de menús como **archivo**, **edición**, **Ver**, **ventana**y **ayuda**.

 Antes de agregar un nuevo menú a la barra de menús de Visual Studio, tenga en cuenta si los comandos deben colocarse en un menú existente. Para obtener más información sobre la selección de ubicación de comandos, vea [menús y comandos para Visual Studio](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md).

 Los menús se declaran en el archivo. Vsct del proyecto. Para obtener más información sobre los menús y los archivos. Vsct, vea [comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md).

 Al completar este tutorial, puede crear un menú denominado **TestMenu** que contenga un comando.

## <a name="prerequisites"></a>Prerrequisitos
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="creating-a-vsix-project-that-has-a-custom-command-item-template"></a>Crear un proyecto VSIX que tenga una plantilla de elemento de comando personalizada

1. Cree un proyecto VSIX denominado `TopLevelMenu` . Puede encontrar la plantilla de Proyecto VSIX en el cuadro de diálogo **nuevo proyecto** , en extensibilidad de **Visual C#**  /  **Extensibility**.  Para obtener más información, vea [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Cuando se abra el proyecto, agregue una plantilla de elemento de comando personalizada denominada **prueba**. En el **Explorador de soluciones**, haga clic con el botón secundario en el nodo del proyecto y seleccione **Agregar o nuevo elemento**. En el cuadro de diálogo **Agregar nuevo elemento** , vaya a **Visual C#/extensibilidad** y seleccione **comando personalizado**. En el campo **nombre** situado en la parte inferior de la ventana, cambie el nombre del archivo de comandos a **TestCommand.CS**.

## <a name="creating-a-menu-on-the-ide-menu-bar"></a>Crear un menú en la barra de menús del IDE

#### <a name="to-create-a-menu"></a>Para crear un menú

1. En **Explorador de soluciones**, abra TestCommandPackage. Vsct.

     Al final del archivo, hay un \<Symbols> nodo que contiene varios \<GuidSymbol> nodos. En el nodo denominado guidTestCommandPackageCmdSet, agregue un nuevo símbolo, como se indica a continuación:

    ```xml
    <IDSymbol name="TopLevelMenu" value="0x1021"/>
    ```

2. Cree un \<Menus> nodo vacío en el \<Commands> nodo, justo antes de \<Groups> . En el \<Menus> nodo, agregue un \<Menu> nodo, como se indica a continuación:

    ```xml
    <Menus>
          <Menu guid="guidTestCommandPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
            <Parent guid="guidSHLMainMenu"
                    id="IDG_VS_MM_TOOLSADDINS" />
            <Strings>
              <ButtonText>TestMenu</ButtonText>
              <CommandName>TestMenu</CommandName>
            </Strings>
        </Menu>
    </Menus>
    ```

     Los `guid` `id` valores y del menú especifican el conjunto de comandos y el menú específico del conjunto de comandos.

     Los `guid` `id` valores y del elemento primario sitúan el menú en la sección de la barra de menús de Visual Studio que contiene los menús herramientas y complementos.

     El valor de la `CommandName` cadena especifica que el texto debe aparecer en el elemento de menú.

3. En la \<Groups> sección, busque \<Group> y cambie el \<Parent> elemento para que apunte al menú que acabamos de agregar:

    ```csharp
    <Groups>
          <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
            <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>
          </Group>
        </Groups>
    ```

     Esto hace que el grupo forme parte del nuevo menú.

4. Busque la sección `Buttons`. Observe que la [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] plantilla de paquete ha generado un `Button` elemento que tiene su elemento primario establecido en `MyMenuGroup` . Como resultado, este comando aparecerá en el menú.

## <a name="building-and-testing-the-extension"></a>Compilar y probar la extensión

1. Compile la solución y comience la depuración. Debería aparecer una instancia de la instancia experimental.

2. La barra de menús de la instancia experimental debe contener un menú **TestMenu** .

3. En el menú **TestMenu** , haga clic en **invocar comando de prueba**.

     Debe aparecer un cuadro de mensaje y mostrar el mensaje "prueba Package Inside TopLevelMenu. prueba. MenuItemCallback ()". Esto indica que el nuevo comando funciona.

## <a name="see-also"></a>Consulte también
 [Comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md)
