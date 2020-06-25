---
title: Agregar un menú a la barra de menús de Visual Studio | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b87fc73c1ed4b24ccfbd604e3bb08c9b02b62524
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/23/2020
ms.locfileid: "85285392"
---
# <a name="add-a-menu-to-the-visual-studio-menu-bar"></a>Agregar un menú a la barra de menús de Visual Studio

En este tutorial se muestra cómo agregar un menú a la barra de menús del entorno de desarrollo integrado (IDE) de Visual Studio. La barra de menús del IDE contiene categorías de menús como **archivo**, **edición**, **Ver**, **ventana**y **ayuda**.

Antes de agregar un nuevo menú a la barra de menús de Visual Studio, tenga en cuenta si los comandos deben colocarse en un menú existente. Para obtener más información sobre la selección de ubicación de comandos, vea [menús y comandos para Visual Studio](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md).

Los menús se declaran en el archivo *. Vsct* del proyecto. Para obtener más información sobre los menús y los archivos *. Vsct* , vea [comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md).

Al completar este tutorial, puede crear un menú denominado **TestMenu** que contenga un comando.

:::moniker range=">=vs-2019"
> [!NOTE]
> A partir de Visual Studio 2019, los menús de nivel superior aportados por las extensiones se colocan en el menú **extensiones** .
:::moniker-end

## <a name="prerequisites"></a>Requisitos previos

A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-vsix-project-that-has-a-custom-command-item-template"></a>Crear un proyecto VSIX que tenga una plantilla de elemento de comando personalizada

1. Cree un proyecto VSIX denominado `TopLevelMenu` . Para buscar la plantilla de Proyecto VSIX en el cuadro de diálogo **nuevo proyecto** , busque "VSIX".  Para obtener más información, vea [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Cuando se abra el proyecto, agregue una plantilla de elemento de comando personalizada denominada **prueba**. En el **Explorador de soluciones**, haga clic con el botón secundario en el nodo del proyecto y seleccione **Agregar**  >   **nuevo elemento**. En el cuadro de diálogo **Agregar nuevo elemento** , vaya a **Visual C#/extensibilidad** y seleccione **comando personalizado**. En el campo **nombre** situado en la parte inferior de la ventana, cambie el nombre del archivo de comandos a *TestCommand.CS*.

## <a name="create-a-menu-on-the-ide-menu-bar"></a>Crear un menú en la barra de menús del IDE

::: moniker range="vs-2017"

1. En **Explorador de soluciones**, Abra *TestCommandPackage. Vsct*.

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

   ```xml
   <Groups>
       <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>
       </Group>
   </Groups>
   ```

    Esto hace que el grupo forme parte del nuevo menú.

::: moniker-end

::: moniker range=">=vs-2019"

1. En **Explorador de soluciones**, Abra *TopLevelMenuPackage. Vsct*.

    Al final del archivo, hay un \<Symbols> nodo que contiene varios \<GuidSymbol> nodos. En el nodo denominado guidTopLevelMenuPackageCmdSet, agregue un nuevo símbolo, como se indica a continuación:

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. Cree un \<Menus> nodo vacío en el \<Commands> nodo, justo antes de \<Groups> . En el \<Menus> nodo, agregue un \<Menu> nodo, como se indica a continuación:

   ```xml
   <Menus>
         <Menu guid="guidTopLevelMenuPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
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

   ```xml
   <Groups>
       <Group guid="guidTopLevelMenuPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTopLevelMenuPackageCmdSet" id="TopLevelMenu"/>
       </Group>
   </Groups>
   ```

    Esto hace que el grupo forme parte del nuevo menú.

::: moniker-end

4. Busque la sección `Buttons`. Observe que la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] plantilla de paquete ha generado un `Button` elemento que tiene su elemento primario establecido en `MyMenuGroup` . Como resultado, este comando aparece en el menú.

## <a name="build-and-test-the-extension"></a>Compilar y probar la extensión

1. Compile la solución y comience la depuración. Debería aparecer una instancia de la instancia experimental.

::: moniker range="vs-2017"

2. La barra de menús de la instancia experimental debe contener un menú **TestMenu** .

::: moniker-end

::: moniker range=">=vs-2019"

2. El menú **extensiones** en la instancia experimental debe contener un menú **TestMenu** .

::: moniker-end

3. En el menú **TestMenu** , haga clic en **invocar comando de prueba**.

     Debe aparecer un cuadro de mensaje y mostrar el mensaje "prueba Package Inside TopLevelMenu. prueba. MenuItemCallback ()".

## <a name="see-also"></a>Vea también

- [Comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md)
