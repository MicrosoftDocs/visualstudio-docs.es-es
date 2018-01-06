---
title: Agregar un comando a la barra de herramientas del explorador de soluciones | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbars [Visual Studio], adding buttons
- buttons [Visual Studio], adding to Solution Explorer
- Solution Explorer, adding buttons
ms.assetid: f6411557-2f4b-4e9f-b02e-fce12a6ac7e9
caps.latest.revision: "39"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 85d38f2347009d75c5e06365c757d2d51339bf06
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="adding-a-command-to-the-solution-explorer-toolbar"></a>Agregar un comando a la barra de herramientas del explorador de soluciones
Este tutorial muestra cómo agregar un botón a la **el Explorador de soluciones** barra de herramientas.  
  
 Cualquier comando en un menú o barra de herramientas se llama a un botón en Visual Studio. Cuando se hace clic en el botón, se ejecuta el código en el controlador de comandos. Normalmente, los comandos relacionados se agrupan conjuntamente para formar un grupo. Los menús o barras de herramientas actúan como contenedores para los grupos. La prioridad determina el orden en que aparecen los comandos individuales de un grupo en el menú o en la barra de herramientas. Puede impedir que un botón que aparezcan en la barra de herramientas o el menú mediante el control de su visibilidad. Un comando que se muestra en un `<VisibilityConstraints>` sección del archivo .vsct sólo aparece en el contexto asociado. La visibilidad no se puede aplicar a los grupos.  
  
 Para obtener más información acerca de los menús, los comandos de barra de herramientas y archivos de vsct, consulte [comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md).  
  
> [!NOTE]
>  Usar archivos de tabla de comandos de XML (.vsct) en lugar de archivos de configuración (.ctc) de tabla de comandos para definir cómo se muestran los menús y comandos en los VSPackages. Para obtener más información, consulta [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="prerequisites"></a>Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-an-extension-with-a-menu-command"></a>Crear una extensión con un comando de menú  
 Crear un proyecto VSIX denominado `SolutionToolbar`. Agregar una plantilla de elemento de comando de menú denominada **ToolbarButton**. Para obtener información acerca de cómo hacerlo, consulte [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="adding-a-button-to-the-solution-explorer-toolbar"></a>Agregar un botón a la barra de herramientas del explorador de soluciones  
 En esta sección del tutorial muestra cómo agregar un botón a la **el Explorador de soluciones** barra de herramientas. Cuando se hace clic en el botón, se ejecuta el código en el método de devolución de llamada.  
  
1.  En el archivo ToolbarButtonPackage.vsct, vaya a la `<Symbols>` sección. El `<GuidSymbol>` nodo contiene el grupo de menús y el comando generado por la plantilla de paquete. Agregar un `<IDSymbol>` elemento a este nodo para declarar el grupo que contendrá el comando.  
  
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
  
     Defina el elemento primario par GUID: ID `guidSHLMainMenu` y `IDM_VS_TOOL_PROJWIN` coloca este grupo en el **el Explorador de soluciones** barra de herramientas y establecer un valor de prioridad alta se coloca después de los otros grupos de comandos.  
  
3.  En el `<Buttons>` sección, cambie el identificador principal de los botones generados `<Button>` entrada para reflejar el grupo que ha definido en el paso anterior. Modificados `<Button>` elemento debe ser similar al siguiente:  
  
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
  
     Un cuadro de diálogo con el mensaje **ToolbarButtonPackage en SolutionToolbar.ToolbarButton.MenuItemCallback()** debe mostrarse.  
  
## <a name="controlling-the-visibility-of-a-button"></a>Controlar la visibilidad de un botón  
 Esta sección del tutorial muestra cómo controlar la visibilidad de un botón en una barra de herramientas. Al establecer un contexto en uno o varios proyectos en la `<VisibilityConstraints>` sección del archivo SolutionToolbar.vsct, restringir un botón para que aparezca sólo cuando un proyecto o proyectos están abiertos.  
  
#### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>Para mostrar un botón cuando uno o varios proyectos que estén abiertos  
  
1.  En el `<Buttons>` sección de ToolbarButtonPackage.vsct, agregue dos marcadores de comando a la existente `<Button>` elemento, entre el `<Strings>` y `<Icons>` etiquetas.  
  
    ```xml  
    <CommandFlag>DefaultInvisible</CommandFlag>  
    <CommandFlag>DynamicVisibility</CommandFlag>  
    ```  
  
     El `DefaultInvisible` y `DynamicVisibility` se deben establecer marcas lo que las entradas en la `<VisibilityConstraints>` sección surta efecto.  
  
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
  
     El **el Explorador de soluciones** barra de herramientas no contiene el botón de tachado.  
  
4.  Abra cualquier solución que contiene un proyecto.  
  
     Aparece el botón de tachado en la barra de herramientas a la derecha de los botones existentes.  
  
5.  En el **archivo** menú, haga clic en **Cerrar solución**. El botón desaparece de la barra de herramientas.  
  
 La visibilidad del botón se controla mediante [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] hasta que se cargue el VSPackage. Después de carga el VSPackage, la visibilidad del botón se controla por el VSPackage.  Para obtener más información, vea [MenuCommands frente a. OleMenuCommands](../extensibility/menucommands-vs-olemenucommands.md).  
  
## <a name="see-also"></a>Vea también  
 [Comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md)