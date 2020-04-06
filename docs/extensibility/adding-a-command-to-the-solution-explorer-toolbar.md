---
title: Adición de un comando a la barra de herramientas del Explorador de soluciones ( S. Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding buttons
- buttons [Visual Studio], adding to Solution Explorer
- Solution Explorer, adding buttons
ms.assetid: f6411557-2f4b-4e9f-b02e-fce12a6ac7e9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44a14d87fbb5754d7af35d3add9e438351877a49
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740338"
---
# <a name="add-a-command-to-the-solution-explorer-toolbar"></a>Agregue un comando a la barra de herramientas del Explorador de soluciones
En este tutorial se muestra cómo agregar un botón a la barra de herramientas del **Explorador** de soluciones.

 Cualquier comando de una barra de herramientas o menú se denomina botón en Visual Studio. Cuando se hace clic en el botón, se ejecuta el código del controlador de comandos. Normalmente, los comandos relacionados se agrupan para formar un grupo. Los menús o barras de herramientas actúan como contenedores para grupos. La prioridad determina el orden en el que aparecen los comandos individuales de un grupo en el menú o en la barra de herramientas. Puede evitar que se muestre un botón en la barra de herramientas o en el menú controlando su visibilidad. Un comando que aparece `<VisibilityConstraints>` en una sección del archivo *.vsct* solo aparece en el contexto asociado. La visibilidad no se puede aplicar a los grupos.

 Para obtener más información acerca de los menús, comandos de barra de herramientas y archivos *.vsct,* vea [Comandos, menús y barras](../extensibility/internals/commands-menus-and-toolbars.md)de herramientas .

> [!NOTE]
> Utilice archivos de tabla de comandos XML (*.vsct*) en lugar de archivos de configuración de tabla de comandos (*.ctc*) para definir cómo aparecen los menús y comandos en los VSPackages. Para obtener más información, vea Tabla de comandos de [Visual Studio (. Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

## <a name="prerequisites"></a>Prerrequisitos
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en la configuración de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [Instalar el SDK](../extensibility/installing-the-visual-studio-sdk.md)de Visual Studio .

## <a name="create-an-extension-with-a-menu-command"></a>Crear una extensión con un comando de menú
 Cree un proyecto `SolutionToolbar`VSIX denominado . Agregue una plantilla de elemento de comando de menú denominada **ToolbarButton**. Para obtener información sobre cómo hacerlo, consulte [Crear una extensión con un comando](../extensibility/creating-an-extension-with-a-menu-command.md)de menú .

## <a name="add-a-button-to-the-solution-explorer-toolbar"></a>Agregue un botón a la barra de herramientas del Explorador de soluciones
 En esta sección del tutorial se muestra cómo agregar un botón a la barra de herramientas del **Explorador** de soluciones. Cuando se hace clic en el botón, se ejecuta el código del método de devolución de llamada.

1. En el archivo *ToolbarButtonPackage.vsct,* vaya a la `<Symbols>` sección. El `<GuidSymbol>` nodo contiene el grupo de menús y el comando generados por la plantilla de paquete. Agregue `<IDSymbol>` un elemento a este nodo para declarar el grupo que contendrá el comando.

    ```xml
    <IDSymbol name="SolutionToolbarGroup" value="0x0190"/>
    ```

2. En `<Groups>` la sección, después de la entrada de grupo existente, defina el nuevo grupo que declaró en el paso anterior.

    ```xml
    <Group guid="guidToolbarButtonPackageCmdSet"
           id="SolutionToolbarGroup" priority="0xF000">
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>
          </Group>
    ```

     Establecer el par GUID:ID primario `guidSHLMainMenu` y `IDM_VS_TOOL_PROJWIN` coloca este grupo en la barra de herramientas del **Explorador** de soluciones y establecer un valor de prioridad alta lo coloca después de los otros grupos de comandos.

3. En `<Buttons>` la sección, cambie el identificador `<Button>` primario de la entrada generada para reflejar el grupo que definió en el paso anterior. El `<Button>` elemento modificado debe tener este aspecto:

    ```xml
    <Button guid="guidToolbarButtonPackageCmdSet" id="ToolbarButtonId" priority="0x0100" type="Button">
        <Parent guid="guidToolbarButtonPackageCmdSet" id="SolutionToolbarGroup" />
        <Icon guid="guidImages" id="bmpPicStrikethrough" />
        <Strings>
            <ButtonText>Invoke ToolbarButton</ButtonText>
        </Strings>
    </Button>
    ```

4. Compile la solución y comience la depuración. Aparece la instancia experimental.

     La barra de **herramientas del Explorador** de soluciones debe mostrar el nuevo botón de comando a la derecha de los botones existentes. El icono del botón es el tachado.

5. Haga clic en el nuevo botón.

     Se debe mostrar un cuadro de diálogo que tenga el mensaje **ToolbarButtonPackage Inside SolutionToolbar.ToolbarButton.MenuItemCallback().**

## <a name="control-the-visibility-of-a-button"></a>Controlar la visibilidad de un botón
 En esta sección del tutorial se muestra cómo controlar la visibilidad de un botón en una barra de herramientas. Al establecer un contexto en uno `<VisibilityConstraints>` o varios proyectos en la sección del archivo *SolutionToolbar.vsct,* se restringe un botón para que aparezca solo cuando un proyecto o proyectos están abiertos.

### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>Para mostrar un botón cuando uno o más proyectos están abiertos

1. En `<Buttons>` la sección de *ToolbarButtonPackage.vsct*, agregue `<Button>` dos indicadores de comando al elemento existente, entre las `<Strings>` etiquetas y. `<Icons>`

   ```xml
   <CommandFlag>DefaultInvisible</CommandFlag>
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

    Los `DefaultInvisible` `DynamicVisibility` indicadores y deben establecerse `<VisibilityConstraints>` para que las entradas de la sección puedan surtir efecto.

2. Cree `<VisibilityConstraints>` una sección `<VisibilityItem>` que tenga dos entradas. Coloque la nueva sección `</Commands>` justo después de la etiqueta de cierre.

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

3. Compile la solución y comience la depuración. Aparece la instancia experimental.

    La barra de **herramientas del Explorador** de soluciones no contiene el botón de tachado.

4. Abra cualquier solución que contenga un proyecto.

    El botón de tachado aparece en la barra de herramientas a la derecha de los botones existentes.

5. En el menú **Archivo** , haga clic en **Cerrar solución**. El botón desaparece de la barra de herramientas.

   La visibilidad del botón [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se controla hasta que se carga el VSPackage. Después de cargar el VSPackage, el VSPackage controla la visibilidad del botón.  Para obtener más información, vea [MenuCommands vs OleMenuCommands](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015).

## <a name="see-also"></a>Vea también
- [Comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md)
