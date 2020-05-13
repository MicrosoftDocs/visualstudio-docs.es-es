---
title: Adición de un menú a la barra de menús de Visual Studio . Microsoft Docs
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
ms.openlocfilehash: 91e5a6e1714dbb87abc67fbf722c3bbd1a194a5b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740311"
---
# <a name="add-a-menu-to-the-visual-studio-menu-bar"></a>Agregue un menú a la barra de menús de Visual Studio

En este tutorial se muestra cómo agregar un menú a la barra de menús del entorno de desarrollo integrado (IDE) de Visual Studio. La barra de menús IDE contiene categorías de menú como **Archivo**, **Editar**, **Ver**, **Ventana**y **Ayuda**.

Antes de agregar un nuevo menú a la barra de menús de Visual Studio, considere si los comandos deben colocarse dentro de un menú existente. Para obtener más información acerca de la colocación de [comandos, vea Menús y comandos para Visual Studio](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md).

Los menús se declaran en el archivo *.vsct* del proyecto. Para obtener más información acerca de los menús y archivos *.vsct,* vea [Comandos, menús y barras](../extensibility/internals/commands-menus-and-toolbars.md)de herramientas .

Al completar este tutorial, puede crear un menú denominado **TestMenu** que contenga un comando.

> [!NOTE]
> En VS 2019, los menús de nivel superior aportados por las extensiones se colocan en el menú **Extensiones.**

## <a name="prerequisites"></a>Prerrequisitos

A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en la configuración de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [Instalar el SDK](../extensibility/installing-the-visual-studio-sdk.md)de Visual Studio .

## <a name="create-a-vsix-project-that-has-a-custom-command-item-template"></a>Cree un proyecto VSIX que tenga una plantilla de elemento de comando personalizada

1. Cree un proyecto `TopLevelMenu`VSIX denominado . Puede encontrar la plantilla de proyecto VSIX en el cuadro de diálogo **Nuevo proyecto** buscando "vsix".  Para obtener más información, consulte [Crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Cuando se abra el proyecto, agregue una plantilla de elemento de comando personalizada denominada **TestCommand**. En el **Explorador**de soluciones , haga clic con el botón secundario en el nodo del proyecto y seleccione **Agregar** >  **nuevo elemento**. En el cuadro de diálogo **Agregar nuevo elemento** , vaya a Visual **C/ Extensibilidad** y seleccione **Comando personalizado**. En el campo **Nombre** en la parte inferior de la ventana, cambie el nombre del archivo de comandos a *TestCommand.cs*.

## <a name="create-a-menu-on-the-ide-menu-bar"></a>Crear un menú en la barra de menús IDE

::: moniker range="vs-2017"

1. En **el Explorador**de soluciones , abra *TestCommandPackage.vsct*.

    Al final del archivo, hay \<un nodo de \<> Symbols que contiene varios nodos GuidSymbol>. En el nodo denominado guidTestCommandPackageCmdSet, agregue un nuevo símbolo, como se indica a continuación:

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. Cree un \<nodo> de \<menús vacío en \<el nodo comandos>, justo antes de que> Grupos. En \<el nodo de> \<De menús, agregue un nodo de> Demenú, como se indica a continuación:

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

    Los `guid` `id` valores y los valores del menú especifican el conjunto de comandos y el menú específico del conjunto de comandos.

    Los `guid` `id` valores y los valores del elemento primario colocan el menú en la sección de la barra de menús de Visual Studio que contiene los menús Herramientas y Complementos.

    El valor `CommandName` de la cadena especifica que el texto debe aparecer en el elemento de menú.

3. En \<la sección> \<de grupos, \<busque el> de grupo y cambie el elemento> padre para que apunte al menú que acabamos de agregar:

   ```csharp
   <Groups>
         <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>
         </Group>
       </Groups>
   ```

    Esto hace que el grupo forme parte del nuevo menú.

::: moniker-end

::: moniker range=">=vs-2019"

1. En **el Explorador**de soluciones , abra *TopLevelMenuPackage.vsct*.

    Al final del archivo, hay \<un nodo de \<> Symbols que contiene varios nodos GuidSymbol>. En el nodo denominado guidTopLevelMenuPackageCmdSet, agregue un nuevo símbolo, como se indica a continuación:

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. Cree un \<nodo> de \<menús vacío en \<el nodo comandos>, justo antes de que> Grupos. En \<el nodo de> \<De menús, agregue un nodo de> Demenú, como se indica a continuación:

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

    Los `guid` `id` valores y los valores del menú especifican el conjunto de comandos y el menú específico del conjunto de comandos.

    Los `guid` `id` valores y los valores del elemento primario colocan el menú en la sección de la barra de menús de Visual Studio que contiene los menús Herramientas y Complementos.

    El valor `CommandName` de la cadena especifica que el texto debe aparecer en el elemento de menú.

3. En \<la sección> \<de grupos, \<busque el> de grupo y cambie el elemento> padre para que apunte al menú que acabamos de agregar:

   ```csharp
   <Groups>
         <Group guid="guidTopLevelMenuPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTopLevelMenuPackageCmdSet" id="TopLevelMenu"/>
         </Group>
       </Groups>
   ```

    Esto hace que el grupo forme parte del nuevo menú.

::: moniker-end

4. Busque la sección `Buttons`. Observe que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] la plantilla Package `Button` ha generado un `MyMenuGroup`elemento que tiene su elemento primario establecido en . Como resultado, este comando aparece en el menú.

## <a name="build-and-test-the-extension"></a>Compile y pruebe la extensión

1. Compile la solución y comience la depuración. Debería aparecer una instancia de la instancia experimental.

::: moniker range="vs-2017"

2. La barra de menús de la instancia experimental debe contener un menú **TestMenu.**

::: moniker-end

::: moniker range=">=vs-2019"

2. El menú **Extensiones** de la instancia experimental debe contener un menú **TestMenu.**

::: moniker-end

3. En el menú **TestMenu** , haga clic en **Invocar comando**de prueba .

     Debe aparecer un cuadro de mensaje y mostrar el mensaje "TestCommand Package Inside TopLevelMenu.TestCommand.MenuItemCallback()".

## <a name="see-also"></a>Vea también

- [Comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md)
