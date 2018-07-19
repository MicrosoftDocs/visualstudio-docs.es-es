---
title: Adición de un menú en la barra de menús de Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c95007ed5b740812ca2b1a269390fbad6ffbc2ba
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2018
ms.locfileid: "39079538"
---
# <a name="add-a-menu-to-the-visual-studio-menu-bar"></a>Agregar un menú en la barra de menús de Visual Studio
Este tutorial muestra cómo agregar un menú en la barra de menús del entorno de desarrollo integrado (IDE) de Visual Studio. La barra de menús IDE contiene categorías de menú como **archivo**, **editar**, **vista**, **ventana**, y **ayuda** .  
  
 Antes de agregar un nuevo menú en la barra de menús de Visual Studio, considere si los comandos deben colocarse dentro de un menú existente. Para obtener más información acerca de la ubicación del comando, consulte [menús y comandos para Visual Studio](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md).  
  
 Los menús se declaran en el *.vsct* archivo del proyecto. Para obtener más información acerca de los menús y *.vsct* archivos, consulte [comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Tras completar este tutorial, puede crear un menú denominado **TestMenu** que contiene un comando.  
  
## <a name="prerequisites"></a>Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-vsix-project-that-has-a-custom-command-item-template"></a>Cree un proyecto VSIX que tiene una plantilla de elemento de comando personalizado  
  
1.  Cree un proyecto VSIX denominado `TopLevelMenu`. Puede encontrar la plantilla de proyecto VSIX en el **nuevo proyecto** en el cuadro de diálogo **Visual C#** / **extensibilidad**.  Para obtener más información, consulte [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Cuando se abra el proyecto, agregue una plantilla de elemento de comando personalizado denominada **comando de prueba**. En el **el Explorador de soluciones**, haga clic en el nodo del proyecto y seleccione **Agregar / nuevo elemento**. En el **Agregar nuevo elemento** cuadro de diálogo, vaya a **Visual C# / extensibilidad** y seleccione **comando personalizado**. En el **nombre** campo en la parte inferior de la ventana, cambie el nombre de archivo de comandos para *TestCommand.cs*.  
  
## <a name="create-a-menu-on-the-ide-menu-bar"></a>Crear un menú en la barra de menús IDE  
  
1.  En **el Explorador de soluciones**, abra *TestCommandPackage.vsct*.  
  
     Al final del archivo, hay un \<símbolos > nodo que contenga varias \<GuidSymbol > los nodos. En el nodo denominado guidTestCommandPackageCmdSet, agregue un nuevo símbolo, como sigue:  
  
    ```xml  
    <IDSymbol name="TopLevelMenu" value="0x1021"/>  
    ```  
  
2.  Crear vacío \<menús > nodo en el \<comandos > nodo, justo antes \<grupos >. En el \<menús > nodo, agregue un \<menú > nodo, como se indica a continuación:  
  
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
  
     El `guid` y `id` valores del menú especifican el conjunto de comandos y el menú específico en el conjunto de comandos.  
  
     El `guid` y `id` valores del elemento primario colocar el menú en la sección de la barra de menús de Visual Studio que contiene los menús de las herramientas y complementos.  
  
     El valor de la `CommandName` cadena especifica que el texto debe aparecer en el elemento de menú.  
  
3.  En el \<grupos > sección, busque la \<grupo > y cambie el \<primario > elemento para que apunte al menú que acabamos de agregar:  
  
    ```csharp  
    <Groups>  
          <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">  
            <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>  
          </Group>  
        </Groups>  
    ```  
  
     Esto hace que la parte del grupo del nuevo menú.  
  
4.  Buscar el `Buttons` sección. Tenga en cuenta que el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] plantilla de paquete se ha generado un `Button` elemento que tiene a su elemento primario establecido en `MyMenuGroup`. Como resultado, este comando aparece en el menú.  
  
## <a name="build-and-test-the-extension"></a>Compilar y probar la extensión  
  
1.  Compile la solución y comience la depuración. Debe aparecer una instancia de la instancia experimental.  
  
2.  La barra de menús en la instancia experimental debe contener un **TestMenu** menú.  
  
3.  En el **TestMenu** menú, haga clic en **invocar el comando de prueba**.  
  
     Debe aparecer un cuadro de mensaje y se mostrará el mensaje "Paquete de comando de prueba dentro de TopLevelMenu.TestCommand.MenuItemCallback()". Esto indica que funciona el nuevo comando.  
  
## <a name="see-also"></a>Vea también  
 [Los comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md)