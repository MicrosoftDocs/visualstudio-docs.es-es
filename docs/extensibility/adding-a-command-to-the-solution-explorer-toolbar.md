---
title: Agregar un comando a la barra Explorador de soluciones barra | Microsoft Docs
description: Obtenga información sobre cómo agregar un botón que ejecuta un comando a la barra de herramientas Explorador de soluciones en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- toolbars [Visual Studio], adding buttons
- buttons [Visual Studio], adding to Solution Explorer
- Solution Explorer, adding buttons
ms.assetid: f6411557-2f4b-4e9f-b02e-fce12a6ac7e9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0aa75bd1a229be147e3462845a61266a650e072e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900244"
---
# <a name="add-a-command-to-the-solution-explorer-toolbar"></a>Agregar un comando a la barra Explorador de soluciones herramientas
En este tutorial se muestra cómo agregar un botón a la barra **Explorador de soluciones** de herramientas.

 Cualquier comando de una barra de herramientas o un menú se denomina botón en Visual Studio. Cuando se hace clic en el botón, se ejecuta el código en el controlador de comandos. Normalmente, los comandos relacionados se agrupan para formar un grupo. Los menús o las barras de herramientas actúan como contenedores para los grupos. Prioridad determina el orden en el que aparecen los comandos individuales de un grupo en el menú o en la barra de herramientas. Puede evitar que se muestre un botón en la barra de herramientas o en el menú controlando su visibilidad. Un comando que aparece en una `<VisibilityConstraints>` sección del *archivo .vsct* solo aparece en el contexto asociado. La visibilidad no se puede aplicar a los grupos.

 Para obtener más información sobre menús, comandos de barra de herramientas y *archivos .vsct,* vea [Comandos, menús y barras de herramientas.](../extensibility/internals/commands-menus-and-toolbars.md)

> [!NOTE]
> Use archivos de tabla de comandos XML *(.vsct)* en lugar de archivos de configuración de tabla de comandos *(.ctc)* para definir cómo aparecen los menús y comandos en los VSPackages. Para obtener más información, [vea Visual Studio tabla de comandos (. Archivos vsct).](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

## <a name="prerequisites"></a>Requisitos previos
 A partir Visual Studio 2015, no se instala el SDK Visual Studio desde el centro de descarga. Se incluye como una característica opcional en Visual Studio configuración. También puede instalar el SDK de VS después. Para obtener más información, consulte [Instalación del SDK Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-menu-command"></a>Creación de una extensión con un comando de menú
 Cree un proyecto VSIX denominado `SolutionToolbar` . Agregue una plantilla de elemento de comando de menú denominada **ToolbarButton**. Para obtener información sobre cómo hacerlo, vea [Crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="add-a-button-to-the-solution-explorer-toolbar"></a>Agregar un botón a la barra Explorador de soluciones herramientas
 En esta sección del tutorial se muestra cómo agregar un botón a la barra **Explorador de soluciones** de herramientas. Cuando se hace clic en el botón, se ejecuta el código del método de devolución de llamada.

1. En el *archivo ToolbarButtonPackage.vsct,* vaya a la  `<Symbols>` sección . El `<GuidSymbol>`  nodo contiene el grupo de menús y el comando generados por la plantilla de paquete. Agregue un `<IDSymbol>` elemento a este nodo para declarar el grupo que contendrán el comando.

    ```xml
    <IDSymbol name="SolutionToolbarGroup" value="0x0190"/>
    ```

2. En la `<Groups>` sección , después de la entrada de grupo existente, defina el nuevo grupo que declaró en el paso anterior.

    ```xml
    <Group guid="guidToolbarButtonPackageCmdSet"
           id="SolutionToolbarGroup" priority="0xF000">
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>
          </Group>
    ```

     Si establece el par GUID:ID primario en y coloca este grupo en la barra de herramientas Explorador de soluciones, y al establecer un valor de prioridad alta, lo coloca después de los otros grupos `guidSHLMainMenu` `IDM_VS_TOOL_PROJWIN` de comandos. 

3. En la sección , cambie el identificador primario de la entrada generada para reflejar el grupo que `<Buttons>` `<Button>` definió en el paso anterior. El elemento `<Button>` modificado debe tener este aspecto:

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

     La **Explorador de soluciones** de herramientas debe mostrar el nuevo botón de comando a la derecha de los botones existentes. El icono del botón es el tachado.

5. Haga clic en el botón nuevo.

     Se debe mostrar un cuadro de diálogo con el mensaje **ToolbarButtonPackage inside SolutionToolbar.ToolbarButton.MenuItemCallback().**

## <a name="control-the-visibility-of-a-button"></a>Control de la visibilidad de un botón
 En esta sección del tutorial se muestra cómo controlar la visibilidad de un botón en una barra de herramientas. Al establecer un contexto en uno o varios proyectos de la sección del archivo `<VisibilityConstraints>` *SolutionToolbar.vsct,* se restringe un botón para que solo aparezca cuando un proyecto o proyectos están abiertos.

### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>Para mostrar un botón cuando uno o varios proyectos están abiertos

1. En la `<Buttons>` sección de *ToolbarButtonPackage.vsct*, agregue dos marcas de comandos al elemento `<Button>` existente, entre las `<Strings>` etiquetas y `<Icons>` .

   ```xml
   <CommandFlag>DefaultInvisible</CommandFlag>
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

    Las `DefaultInvisible` marcas y deben `DynamicVisibility` establecerse para que las entradas de la sección `<VisibilityConstraints>` puedan tener efecto.

2. Cree una `<VisibilityConstraints>` sección que tenga dos `<VisibilityItem>` entradas. Coloque la nueva sección justo después de la etiqueta de `</Commands>` cierre.

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

    La **Explorador de soluciones** de herramientas no contiene el botón tachado.

4. Abra cualquier solución que contenga un proyecto.

    El botón tachado aparece en la barra de herramientas a la derecha de los botones existentes.

5. En el menú **Archivo** , haga clic en **Cerrar solución**. El botón desaparece de la barra de herramientas.

   La visibilidad del botón se controla mediante [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] hasta que se carga el VSPackage. Una vez cargado el VSPackage, el VSPackage controla la visibilidad del botón.  Para obtener más información, [vea MenuCommands frente a OleMenuCommands](/previous-versions/visualstudio/visual-studio-2015/misc/menucommands-vs-olemenucommands?preserve-view=true&view=vs-2015).

## <a name="see-also"></a>Consulta también
- [Comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md)