---
title: "Agregar una barra de herramientas | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "barras de herramientas [Visual Studio], agregar a IDE"
  - "IDE, agregar barras de herramientas"
ms.assetid: 17302c25-6f59-4e97-8c85-54f95336a07f
caps.latest.revision: 38
caps.handback.revision: 38
ms.author: "gregvanl"
manager: "ghogen"
---
# Agregar una barra de herramientas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este tutorial muestra cómo agregar una barra de herramientas al IDE de Visual Studio.  
  
 Una barra de herramientas es una barra horizontal o vertical que contiene botones que están enlazados a los comandos. Dependiendo de su implementación, una barra de herramientas en el IDE se puede cambiar de posición, acoplar en cualquier lado de la ventana principal del IDE o permanezcan delante de otras ventanas.  
  
 Además, los usuarios pueden agregar comandos a una barra de herramientas o quitarlos de ella mediante el **Personalizar** cuadro de diálogo. Normalmente, las barras de herramientas VSPackages son personalizables por el usuario. El IDE administra todas las personalizaciones y VSPackage responde a los comandos. El VSPackage no debe saber dónde se encuentran físicamente un comando.  
  
 Para obtener más información acerca de los menús, consulte [Barras de herramientas, menús y comandos](../extensibility/internals/commands-menus-and-toolbars.md).  
  
## Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional de la instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulta [Instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Crear una extensión con una barra de herramientas  
 Cree un proyecto VSIX denominado `IDEToolbar`. Agregar una plantilla de elemento de comando de menú denominada **ToolbarTestCommand**. Para obtener información acerca de cómo hacerlo, consulte [Crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## Crear una barra de herramientas del IDE  
  
1.  En ToolbarTestCommandPackage.vsct, busque la sección de símbolos. En el elemento GuidSymbol denominado guidToolbarTestCommandPackageCmdSet, agregue las declaraciones para una barra de herramientas y un grupo de la barra de herramientas, como sigue.  
  
    ```xml  
    <IDSymbol name="Toolbar" value="0x1000" />  
    <IDSymbol name="ToolbarGroup" value="0x1050" />  
  
    ```  
  
2.  En la parte superior de la sección de comandos, cree una sección de menús. Agregue un elemento de menú a la sección de menús para definir la barra de herramientas.  
  
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
  
     No se pueden anidar las barras de herramientas como submenús. Por lo tanto, no es necesario asignar a un grupo primario. Además, no es necesario establecer una prioridad, porque el usuario puede mover las barras de herramientas. Normalmente, la ubicación inicial de una barra de herramientas se define mediante programación, pero se conservan los cambios posteriores por el usuario.  
  
3.  En el [grupos](../extensibility/groups-element.md) sección, después de la entrada de grupo existente, defina un [grupo](../extensibility/group-element.md) el elemento para que contenga los comandos de la barra de herramientas.  
  
    ```xml  
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"  
          priority="0x0000">  
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>  
    </Group>  
    ```  
  
4.  Hacer que el botón aparezca en la barra de herramientas. En la sección de botones, reemplace el bloque primario, en el botón de la barra de herramientas. El bloque de botón resultante debería tener este aspecto:  
  
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
  
5.  Compile la solución y comience la depuración. Debe aparecer la instancia experimental.  
  
6.  Haga clic en la barra de menús de Visual Studio para obtener la lista de barras de herramientas. Seleccione **barra de herramientas de prueba**.  
  
7.  Ahora debería ver la barra de herramientas como un icono a la derecha del icono de búsqueda en archivos. Al hacer clic en el icono, verá un cuadro de mensaje que dice **ToolbarTestCommandPackage. En IDEToolbar.ToolbarTestCommand.MenuItemCallback\(\)**.  
  
## Vea también  
 [Barras de herramientas, menús y comandos](../extensibility/internals/commands-menus-and-toolbars.md)