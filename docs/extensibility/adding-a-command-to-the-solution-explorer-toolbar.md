---
title: "Agregar un comando a la barra de herramientas del explorador de soluciones | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "barras de herramientas [Visual Studio], agregar botones"
  - "botones [Visual Studio], agregar al explorador de soluciones"
  - "Explorador de soluciones, agregar botones"
ms.assetid: f6411557-2f4b-4e9f-b02e-fce12a6ac7e9
caps.latest.revision: 39
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 39
---
# Agregar un comando a la barra de herramientas del explorador de soluciones
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este tutorial muestra cómo agregar un botón a la **el Explorador de soluciones** barra de herramientas.  
  
 Cualquier comando en un menú o barra de herramientas se denomina un botón en Visual Studio. Cuando se hace clic en el botón, se ejecuta el código en el controlador de comandos. Normalmente, los comandos relacionados se agrupan para formar un grupo. Los menús o barras de herramientas actúan como contenedores para los grupos. La prioridad determina el orden en que los comandos individuales de un grupo aparecen en el menú o en la barra de herramientas. Puede impedir que un botón que se muestra en la barra de herramientas o el menú controlando su visibilidad. Un comando que aparece en un `<VisibilityConstraints>` sección del archivo vsct sólo aparece en el contexto asociado. La visibilidad no se puede aplicar a grupos.  
  
 Para obtener más información acerca de los menús, comandos de barra de herramientas y los archivos .vsct, vea [Barras de herramientas, menús y comandos](../extensibility/internals/commands-menus-and-toolbars.md).  
  
> [!NOTE]
>  Usar archivos de la tabla de comandos de XML \(.vsct\) en lugar de archivos de configuración \(.ctc\) de tabla de comandos para definir la aparecen de los menús y comandos en los VSPackages. Para obtener más información, consulta [Tabla de comandos de Visual Studio \(. Archivos de Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional de la instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulta [Instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Crear una extensión con un comando de menú  
 Cree un proyecto VSIX denominado `SolutionToolbar`. Agregar una plantilla de elemento de comando de menú denominada **ToolbarButton**. Para obtener información acerca de cómo hacerlo, consulte [Crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## Agregar un botón a la barra de herramientas del explorador de soluciones  
 Esta sección del tutorial muestra cómo agregar un botón a la **el Explorador de soluciones** barra de herramientas. Cuando se hace clic en el botón, se ejecuta el código en el método de devolución de llamada.  
  
1.  En el archivo ToolbarButtonPackage.vsct, vaya a la  `<Symbols>` sección. El `<GuidSymbol>`  nodo contiene el grupo de menús y el comando generado por la plantilla de paquete. Agregar un `<IDSymbol>` elemento a este nodo para declarar el grupo que contenga el comando.  
  
    ```xml  
    <IDSymbol name="SolutionToolbarGroup" value="0x0190"/>  
    ```  
  
2.  En la `<Groups>` sección, después de la entrada de grupo existente, definir el nuevo grupo que declaró en el paso anterior.  
  
    ```xml  
    <Group guid="guidToolbarButtonPackageCmdSet"  
           id="SolutionToolbarGroup" priority="0xF000">  
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>  
          </Group>  
    ```  
  
     Establecer el elemento primario par GUID:ID en `guidSHLMainMenu` y `IDM_VS_TOOL_PROJWIN` coloca este grupo en el **el Explorador de soluciones** barra de herramientas y establecer un valor de prioridad alta se coloca después de los otros grupos de comandos.  
  
3.  En la `<Buttons>` sección, cambie el identificador principal de generado `<Button>` entrada para reflejar el grupo que ha definido en el paso anterior. Modificado `<Button>` elemento tendrá este aspecto:  
  
    ```xml  
    <Button guid="guidToolbarButtonPackageCmdSet" id="ToolbarButtonId" priority="0x0100" type="Button">  
        <Parent guid="guidToolbarButtonPackageCmdSet" id="SolutionToolbarGroup" />  
        <Icon guid="guidImages" id="bmpPicStrikethrough" />  
        <Strings>  
            <ButtonText>Invoke ToolbarButton</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
4.  Compile la solución y comience la depuración. Aparece la instancia experimental.  
  
     El **el Explorador de soluciones** barra de herramientas debe mostrar el nuevo botón de comando a la derecha de los botones existentes. El icono del botón es el tachado.  
  
5.  Haga clic en el botón nuevo.  
  
     Un cuadro de diálogo con el mensaje **ToolbarButtonPackage en SolutionToolbar.ToolbarButton.MenuItemCallback\(\)** debe mostrarse.  
  
## Controlar la visibilidad de un botón  
 Esta sección del tutorial muestra cómo controlar la visibilidad de un botón en una barra de herramientas. Al establecer un contexto en uno o varios proyectos en la `<VisibilityConstraints>` sección del archivo SolutionToolbar.vsct, restringir un botón para que aparezca sólo cuando un proyecto o proyectos están abiertos.  
  
#### Para mostrar un botón cuando se abren uno o varios proyectos  
  
1.  En la `<Buttons>` sección de ToolbarButtonPackage.vsct, agregue dos marcadores de comando a la existente `<Button>` elemento, entre el `<Strings>` y `<Icons>` etiquetas.  
  
    ```xml  
    <CommandFlag>DefaultInvisible</CommandFlag>  
    <CommandFlag>DynamicVisibility</CommandFlag>  
    ```  
  
     El `DefaultInvisible` y `DynamicVisibility` marcas se deben establecerlo que las entradas de la `<VisibilityConstraints>` sección surtan efecto.  
  
2.  Crear un `<VisibilityConstraints>` sección que tiene dos `<VisibilityItem>` entradas. Colocar la nueva sección justo después del cierre `</Commands>` etiqueta.  
  
    ```xml  
    <VisibilityConstraints>  
        <VisibilityItem guid="guidToolbarButtonPackageCmdSet"  
              id="ToolbarButtonId"  
              context="UICONTEXT_SolutionHasSingleProject" />  
        <VisibilityItem guid="guidToolbarButtonPackageCmdSet"  
              id="ToolbarButtonId"  
              context="UICONTEXT_SolutionHasMultipleProjects" />  
    </VisibilityConstraints>  
    ```  
  
     Cada elemento de visibilidad representa una condición en la que se muestra el botón especificado. Para aplicar varias condiciones, debe crear varias entradas para el mismo botón.  
  
3.  Compile la solución y comience la depuración. Aparece la instancia experimental.  
  
     El **el Explorador de soluciones** barra de herramientas no contiene el botón tachado.  
  
4.  Abra cualquier solución que contenga un proyecto.  
  
     El botón tachado aparece en la barra de herramientas a la derecha de los botones existentes.  
  
5.  En el **archivo** menú, haga clic en **Cerrar solución**. El botón desaparece de la barra de herramientas.  
  
 Controla la visibilidad del botón [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] hasta que se cargue el paquete VSPackage. Una vez cargado el VSPackage, la visibilidad del botón se controla mediante el VSPackage.  Para obtener más información, consulta [MenuCommands frente a OleMenuCommands](../misc/menucommands-vs-olemenucommands.md).  
  
## Vea también  
 [Barras de herramientas, menús y comandos](../extensibility/internals/commands-menus-and-toolbars.md)