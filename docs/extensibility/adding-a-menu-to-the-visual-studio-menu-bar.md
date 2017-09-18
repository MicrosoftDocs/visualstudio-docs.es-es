---
title: "Agregar un men&#250; a la barra de men&#250;s de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "menús, creación de nivel superior"
  - "menús de nivel superior"
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
caps.latest.revision: 51
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 51
---
# Agregar un men&#250; a la barra de men&#250;s de Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este tutorial muestra cómo agregar un menú a la barra de menús del entorno de desarrollo integrado \(IDE\) de Visual Studio. La barra de menús IDE contiene categorías de menú como **archivo**, **Editar**, **vista**, **ventana**, y **Ayuda**.  
  
 Antes de agregar un nuevo menú en la barra de menús de Visual Studio, considere si los comandos se deben colocar dentro de un menú existente. Para obtener más información acerca de la selección del comando, consulte [Menús y comandos de Visual Studio](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md).  
  
 Los menús se declaran en el archivo .vsct del proyecto. Para obtener más información acerca de los menús y los archivos .vsct, vea [Barras de herramientas, menús y comandos](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Después de completar este tutorial, puede crear un menú denominado **TestMenu** que contiene un comando.  
  
## Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional de la instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulta [Instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Crear un proyecto de VSIX que tiene una plantilla de elemento de comando personalizado  
  
1.  Cree un proyecto VSIX denominado `TopLevelMenu`. Puede encontrar la plantilla de proyecto VSIX en la **nuevo proyecto** en el cuadro de diálogo **Visual C\#** \/ **extensibilidad**.  Para obtener más información, consulta [Crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Cuando se abre el proyecto, agregue una plantilla de elemento de comando personalizado denominada **TestCommand**. En el **el Explorador de soluciones**, haga clic en el nodo del proyecto y seleccione **Agregar \/ nuevo elemento**. En el **Agregar nuevo elemento** cuadro de diálogo, vaya a **Visual C\# \/ extensibilidad** y seleccione **comando personalizado**. En el **nombre** campo en la parte inferior de la ventana, el nombre del archivo de comandos **TestCommand.cs**.  
  
## Crear un menú en la barra de menús del IDE  
  
#### Para crear un menú  
  
1.  En **el Explorador de soluciones**, abra TestCommandPackage.vsct.  
  
     Al final del archivo, hay un nodo \< símbolos \> que contiene varios nodos de \< GuidSymbol \>. En el nodo denominado guidTestCommandPackageCmdSet, agregue un nuevo símbolo, como sigue:  
  
    ```xml  
    <IDSymbol name="TopLevelMenu" value="0x1021"/>  
    ```  
  
2.  Crear un nodo \< menús \> vacío en el nodo \< comandos \>, justo antes de \< grupos \>. En el nodo \< menús \>, agregue un nodo \< Menu \>, como sigue:  
  
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
  
     El `guid` y `id` valores del elemento primario colocar el menú en la sección de la barra de menús de Visual Studio que contiene los menús herramientas y complementos.  
  
     El valor de la `CommandName` cadena especifica que el texto debe aparecer en el elemento de menú.  
  
3.  En la sección \< grupos \>, \< grupo \> encuentra y cambie el elemento \< principal \> seleccione el menú que acaba de agregar:  
  
    ```c#  
    <Groups>  
          <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">  
            <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>  
          </Group>  
        </Groups>  
    ```  
  
     Esto hace que el elemento de grupo del nuevo menú.  
  
4.  Busque la `Buttons` sección. Observe que el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] plantilla de paquetes ha generado un `Button` elemento con su elemento primario establecido en `MyMenuGroup`. Como resultado, este comando aparecerá en el menú.  
  
## Compilar y probar la extensión  
  
1.  Compile la solución y comience la depuración. Debe aparecer una instancia de la instancia experimental.  
  
2.  La barra de menús en la instancia experimental debe contener una **TestMenu** menú.  
  
3.  En el **TestMenu** menú, haga clic en **invocar el comando de prueba**.  
  
     Debería aparecer un cuadro de mensaje y se mostrará el mensaje "TestCommand paquete dentro de TopLevelMenu.TestCommand.MenuItemCallback\(\)". Esto indica que el nuevo comando funciona.  
  
## Vea también  
 [Barras de herramientas, menús y comandos](../extensibility/internals/commands-menus-and-toolbars.md)