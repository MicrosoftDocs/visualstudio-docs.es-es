---
title: Agregar un comando a la barra de herramientas del explorador de soluciones | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- toolbars [Visual Studio], adding buttons
- buttons [Visual Studio], adding to Solution Explorer
- Solution Explorer, adding buttons
ms.assetid: f6411557-2f4b-4e9f-b02e-fce12a6ac7e9
caps.latest.revision: 40
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0dfc2aeb0b0e73e48fd0dcf64b5b7c09fcbea9f1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47581301"
---
# <a name="adding-a-command-to-the-solution-explorer-toolbar"></a>Adición de un comando a la barra de herramientas del Explorador de soluciones
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [agregar un comando a la barra de herramientas del explorador de soluciones](https://docs.microsoft.com/visualstudio/extensibility/adding-a-command-to-the-solution-explorer-toolbar).  
  
En este tutorial se muestra cómo agregar un botón a la **el Explorador de soluciones** barra de herramientas.  
  
 Cualquier comando en un menú o barra de herramientas se denomina un botón en Visual Studio. Cuando se hace clic en el botón, se ejecuta el código en el controlador de comandos. Normalmente, los comandos relacionados se agrupan para formar un grupo. Los menús o barras de herramientas actúan como contenedores para los grupos. La prioridad determina el orden en que los comandos individuales en un grupo aparecen en el menú o en la barra de herramientas. Puede impedir que un botón que se muestra en la barra de herramientas o en el menú controlando su visibilidad. Un comando que aparece en un `<VisibilityConstraints>` sección del archivo .vsct sólo aparece en el contexto asociado. La visibilidad no se puede aplicar a grupos.  
  
 Para obtener más información acerca de los menús, comandos de la barra de herramientas y los archivos .vsct, vea [comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md).  
  
> [!NOTE]
>  Usar archivos de tabla de comandos XML (.vsct) en lugar de archivos de configuración (.ctc) de tabla de comandos para definir cómo los menús y comandos que aparecen en los VSPackages. Para obtener más información, consulta [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="prerequisites"></a>Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-an-extension-with-a-menu-command"></a>Creación de una extensión con un comando de menú  
 Cree un proyecto VSIX denominado `SolutionToolbar`. Agregar una plantilla de elemento de comando de menú denominada **ToolbarButton**. Para obtener información acerca de cómo hacerlo, consulte [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="adding-a-button-to-the-solution-explorer-toolbar"></a>Agregar un botón a la barra de herramientas del explorador de soluciones  
 En esta sección del tutorial se muestra cómo agregar un botón a la **el Explorador de soluciones** barra de herramientas. Cuando se hace clic en el botón, se ejecuta el código en el método de devolución de llamada.  
  
1.  En el archivo ToolbarButtonPackage.vsct, vaya a la `<Symbols>` sección. El `<GuidSymbol>` nodo contiene el grupo de menús y el comando generado por la plantilla de paquete. Agregar un `<IDSymbol>` elemento a este nodo para declarar el grupo que contenga el comando.  
  
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
  
3.  En el `<Buttons>` sección, cambie el identificador principal de generado `<Button>` entrada para reflejar el grupo que ha definido en el paso anterior. Modificado `<Button>` elemento debe tener este aspecto:  
  
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
  
     Un cuadro de diálogo que tiene el mensaje **ToolbarButtonPackage dentro SolutionToolbar.ToolbarButton.MenuItemCallback()** debe mostrarse.  
  
## <a name="controlling-the-visibility-of-a-button"></a>Controlar la visibilidad de un botón  
 Esta sección del tutorial muestra cómo controlar la visibilidad de un botón en una barra de herramientas. Al establecer un contexto en uno o varios proyectos en la `<VisibilityConstraints>` sección del archivo SolutionToolbar.vsct, restringe un botón para que aparezca solo cuando un proyecto o proyectos están abiertos.  
  
#### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>Para mostrar un botón cuando se abren uno o varios proyectos  
  
1.  En el `<Buttons>` sección de ToolbarButtonPackage.vsct, agregue dos marcadores de comando existente `<Button>` elemento, entre el `<Strings>` y `<Icons>` etiquetas.  
  
    ```xml  
    <CommandFlag>DefaultInvisible</CommandFlag>  
    <CommandFlag>DynamicVisibility</CommandFlag>  
    ```  
  
     El `DefaultInvisible` y `DynamicVisibility` marcas se deben establecerlo que las entradas de la `<VisibilityConstraints>` sección surta efecto.  
  
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
  
 Controla la visibilidad del botón [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hasta que se carga el VSPackage. Una vez cargado el VSPackage, la visibilidad del botón se controla mediante el VSPackage.  Para obtener más información, consulte [MenuCommands frente a. OleMenuCommands](../misc/menucommands-vs-olemenucommands.md).  
  
## <a name="see-also"></a>Vea también  
 [Comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md)

