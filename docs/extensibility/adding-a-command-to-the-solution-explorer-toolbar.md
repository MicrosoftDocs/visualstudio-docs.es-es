---
title: Agregar un comando a la barra de herramientas Explorador de soluciones | Microsoft Docs
description: Obtenga información sobre cómo agregar un botón que ejecute un comando a la barra de herramientas Explorador de soluciones en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding buttons
- buttons [Visual Studio], adding to Solution Explorer
- Solution Explorer, adding buttons
ms.assetid: f6411557-2f4b-4e9f-b02e-fce12a6ac7e9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 305966a4cd4ec67994ac3dbd6c7ba0e25a14172f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951698"
---
# <a name="add-a-command-to-the-solution-explorer-toolbar"></a>Agregar un comando a la barra de herramientas Explorador de soluciones
En este tutorial se muestra cómo agregar un botón a la barra de herramientas **Explorador de soluciones** .

 Cualquier comando de una barra de herramientas o un menú se denomina botón en Visual Studio. Al hacer clic en el botón, se ejecuta el código del controlador de comandos. Normalmente, los comandos relacionados se agrupan para formar un grupo. Los menús o las barras de herramientas actúan como contenedores para los grupos. Prioridad determina el orden en que aparecen los comandos individuales en un grupo en el menú o en la barra de herramientas. Puede evitar que se muestre un botón en la barra de herramientas o en el menú controlando su visibilidad. Un comando que aparece en una `<VisibilityConstraints>` sección del archivo *. Vsct* solo aparece en el contexto asociado. No se puede aplicar la visibilidad a los grupos.

 Para obtener más información sobre los menús, los comandos de la barra de herramientas y los archivos *. Vsct* , vea [comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md).

> [!NOTE]
> Use archivos de tabla de comandos XML (*. Vsct*) en lugar de archivos de configuración de tabla de comandos (*. CTC*) para definir el modo en que los menús y comandos aparecen en los VSPackages. Para obtener más información, vea [tabla de comandos de Visual Studio (. Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

## <a name="prerequisites"></a>Requisitos previos
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS después. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-menu-command"></a>Crear una extensión con un comando de menú
 Cree un proyecto VSIX denominado `SolutionToolbar` . Agregue una plantilla de elemento de comando de menú denominada **ToolbarButton**. Para obtener información sobre cómo hacerlo, vea [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="add-a-button-to-the-solution-explorer-toolbar"></a>Agregar un botón a la barra de herramientas Explorador de soluciones
 En esta sección del tutorial se muestra cómo agregar un botón a la barra de herramientas **Explorador de soluciones** . Al hacer clic en el botón, se ejecuta el código del método de devolución de llamada.

1. En el archivo *ToolbarButtonPackage. Vsct* , vaya a la  `<Symbols>` sección. El `<GuidSymbol>`  nodo contiene el grupo de menús y el comando generado por la plantilla de paquete. Agregue un `<IDSymbol>` elemento a este nodo para declarar el grupo que va a contener el comando.

    ```xml
    <IDSymbol name="SolutionToolbarGroup" value="0x0190"/>
    ```

2. En la `<Groups>` sección, después de la entrada de grupo existente, defina el nuevo grupo que declaró en el paso anterior.

    ```xml
    <Group guid="guidToolbarButtonPackageCmdSet"
           id="SolutionToolbarGroup" priority="0xF000">
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>
          </Group>
    ```

     Al establecer el par GUID: ID en `guidSHLMainMenu` y se `IDM_VS_TOOL_PROJWIN` coloca este grupo en la barra de herramientas **Explorador de soluciones** , y al establecer un valor de prioridad alta, se coloca después de los otros grupos de comandos.

3. En la `<Buttons>` sección, cambie el identificador primario de la entrada generada `<Button>` para que refleje el grupo que definió en el paso anterior. El `<Button>` elemento modificado debería tener el siguiente aspecto:

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

     En la barra de herramientas **Explorador de soluciones** debe mostrarse el botón nuevo comando a la derecha de los botones existentes. El icono del botón es el tachado.

5. Haga clic en el botón nuevo.

     Se debe mostrar un cuadro de diálogo que tenga el mensaje **ToolbarButtonPackage dentro de SolutionToolbar. ToolbarButton. MenuItemCallback ()** .

## <a name="control-the-visibility-of-a-button"></a>Controlar la visibilidad de un botón
 En esta sección del tutorial se muestra cómo controlar la visibilidad de un botón en una barra de herramientas. Al establecer un contexto en uno o varios proyectos de la `<VisibilityConstraints>` sección del archivo *SolutionToolbar. Vsct* , se restringe un botón para que aparezca solo cuando se abra un proyecto o proyectos.

### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>Para mostrar un botón cuando uno o varios proyectos están abiertos

1. En la `<Buttons>` sección de *ToolbarButtonPackage. Vsct*, agregue dos marcadores de comando al `<Button>` elemento existente, entre las `<Strings>` `<Icons>` etiquetas y.

   ```xml
   <CommandFlag>DefaultInvisible</CommandFlag>
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

    `DefaultInvisible` `DynamicVisibility` Se deben establecer las marcas y para que las entradas de la `<VisibilityConstraints>` sección surtan efecto.

2. Cree una `<VisibilityConstraints>` sección que tenga dos `<VisibilityItem>` entradas. Coloque la nueva sección justo después de la `</Commands>` etiqueta de cierre.

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

    La barra de herramientas **Explorador de soluciones** no contiene el botón tachado.

4. Abra cualquier solución que contenga un proyecto.

    El botón tachado aparece en la barra de herramientas situada a la derecha de los botones existentes.

5. En el menú **Archivo** , haga clic en **Cerrar solución**. El botón desaparece de la barra de herramientas.

   Controla la visibilidad del botón [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] hasta que se carga el VSPackage. Una vez cargado el VSPackage, el VSPackage controla la visibilidad del botón.  Para obtener más información, consulte [MenuCommands frente a OleMenuCommands](/previous-versions/visualstudio/visual-studio-2015/misc/menucommands-vs-olemenucommands?preserve-view=true&view=vs-2015).

## <a name="see-also"></a>Vea también
- [Comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md)