---
title: Agregar elementos de menú de forma dinámica | Microsoft Docs
description: Obtenga información sobre cómo usar la marca de comandos DynamicItemStart para agregar elementos de menú en tiempo de ejecución. En este artículo se muestra cómo establecer el proyecto de inicio en una solución de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- DYNAMICITEMSTART
- menu items, adding dynamically
- menus, adding dynamic items
ms.assetid: d281e9c9-b289-4d64-8d0a-094bac6c333c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fa85d5b5cf4b99840e181fb24b5913ff72a3fee0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070341"
---
# <a name="dynamically-add-menu-items"></a>Agregar elementos de menú de forma dinámica
Puede agregar elementos de menú en tiempo de ejecución si especifica la `DynamicItemStart` marca de comando en una definición de botón de marcador de posición en el archivo de tabla de comandos de Visual Studio (*. Vsct*) y, a continuación, define (en el código) el número de elementos de menú que se van a mostrar y controla los comandos. Cuando se carga el VSPackage, el marcador de posición se reemplaza por los elementos de menú dinámicos.

 Visual Studio usa listas dinámicas en la lista de elementos **usados más recientemente** (MRU), que muestra los nombres de los documentos que se han abierto recientemente, y la lista de **Windows** , que muestra los nombres de las ventanas que están abiertas actualmente.   La `DynamicItemStart` marca en una definición de comando especifica que el comando es un marcador de posición hasta que se abra el VSPackage. Cuando se abre el VSPackage, el marcador de posición se reemplaza por 0 o más comandos que se crean en tiempo de ejecución y se agregan a la lista dinámica. Es posible que no pueda ver la posición en el menú en el que aparece la lista dinámica hasta que se abra el VSPackage.  Para rellenar la lista dinámica, Visual Studio pide al VSPackage que busque un comando con un identificador cuyos primeros caracteres coincidan con el identificador del marcador de posición. Cuando Visual Studio encuentra un comando coincidente, agrega el nombre del comando a la lista dinámica. Después, incrementa el identificador y busca otro comando coincidente para agregarlo a la lista dinámica hasta que no haya más comandos dinámicos.

 En este tutorial se muestra cómo establecer el proyecto de inicio en una solución de Visual Studio con un comando en la barra de herramientas **Explorador de soluciones** . Usa un controlador de menú que tiene una lista desplegable dinámica de los proyectos de la solución activa. Para evitar que aparezca este comando cuando no hay ninguna solución abierta o cuando la solución abierta solo tiene un proyecto, el VSPackage solo se carga cuando una solución tiene varios proyectos.

 Para obtener más información acerca de los archivos *. Vsct* , consulte [archivos de tabla de comandos de Visual Studio (. Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

## <a name="create-an-extension-with-a-menu-command"></a>Crear una extensión con un comando de menú

1. Cree un proyecto VSIX denominado `DynamicMenuItems` .

2. Cuando se abra el proyecto, agregue una plantilla de elemento de comando personalizada y asígnele el nombre **DynamicMenu**. Para obtener más información, vea [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="setting-up-the-elements-in-the-vsct-file"></a>Configurar los elementos del archivo *. Vsct*
 Para crear un controlador de menú con elementos de menú dinámicos en una barra de herramientas, especifique los siguientes elementos:

- Dos grupos de comandos, uno que contiene el controlador de menú y otro que contiene los elementos de menú en la lista desplegable

- Un elemento de menú de tipo `MenuController`

- Dos botones, uno que actúa como marcador de posición para los elementos de menú y otro que proporciona el icono y la información sobre herramientas en la barra de herramientas.

1. En *DynamicMenuPackage. Vsct*, defina los identificadores de comando. Vaya a la sección Symbols y reemplace los elementos IDSymbol en el bloque GuidSymbol de **guidDynamicMenuPackageCmdSet** . Debe definir elementos IDSymbol para los dos grupos, el controlador de menú, el comando de marcador de posición y el comando de delimitador.

    ```xml
    <GuidSymbol name="guidDynamicMenuPackageCmdSet" value="{ your GUID here }">
        <IDSymbol name="MyToolbarItemGroup" value="0x1020" />
        <IDSymbol name="MyMenuControllerGroup" value="0x1025" />
        <IDSymbol name="MyMenuController" value ="0x1030"/>
        <IDSymbol name="cmdidMyAnchorCommand" value="0x0103" />
        <!-- NOTE: The following command expands at run time to some number of ids.
         Try not to place command ids after it (e.g. 0x0105, 0x0106).
         If you must add a command id after it, make the gap very large (e.g. 0x200) -->
        <IDSymbol name="cmdidMyDynamicStartCommand" value="0x0104" />
    </GuidSymbol>
    ```

2. En la sección grupos, elimine los grupos existentes y agregue los dos grupos que acaba de definir:

    ```xml
    <Groups>
        <!-- The group that adds the MenuController on the Solution Explorer toolbar.
             The 0x4000 priority adds this group after the group that contains the
             Preview Selected Items button, which is normally at the far right of the toolbar. -->
        <Group guid="guidDynamicMenuPackageCmdSet" id="MyToolbarItemGroup" priority="0x4000" >
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN" />
        </Group>
        <!-- The group for the items on the MenuController drop-down. It is added to the MenuController submenu. -->
        <Group guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" priority="0x4000" >
            <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" />
        </Group>
    </Groups>
    ```

     Agregue MenuController. Establezca la marca de comando DynamicVisibility, ya que no está siempre visible. No se muestra el ButtonText.

    ```xml
    <Menus>
        <!-- The MenuController to display on the Solution Explorer toolbar.
             Place it in the ToolbarItemGroup.-->
        <Menu guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" priority="0x1000" type="MenuController">
            <Parent guid="guidDynamicMenuPackageCmdSet" id="MyToolbarItemGroup" />
            <CommandFlag>DynamicVisibility</CommandFlag>
            <Strings>
               <ButtonText></ButtonText>
           </Strings>
        </Menu>
    </Menus>
    ```

3. Agregue dos botones, uno como marcador de posición para los elementos de menú dinámicos y otro como delimitador para MenuController.

     El elemento primario del botón de marcador de posición es **MyMenuControllerGroup**. Agregue las marcas de comando DynamicItemStart, DynamicVisibility y Textchanges al al botón de marcador de posición. No se muestra el ButtonText.

     El botón delimitador contiene el icono y el texto de información sobre herramientas. El elemento primario del botón delimitador también es **MyMenuControllerGroup**. Agregue la marca de comando NoShowOnMenuController para asegurarse de que el botón realmente no aparece en la lista desplegable controlador de menú y el marcador de comando FixMenuController para convertirlo en el delimitador permanente.

    ```xml
    <!-- The placeholder for the dynamic items that expand to N items at run time. -->
    <Buttons>
        <Button guid="guidDynamicMenuPackageCmdSet" id="cmdidMyDynamicStartCommand" priority="0x1000" >
          <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" />
          <CommandFlag>DynamicItemStart</CommandFlag>
          <CommandFlag>DynamicVisibility</CommandFlag>
          <CommandFlag>TextChanges</CommandFlag>
          <!-- This text does not appear. -->
          <Strings>
            <ButtonText>Project</ButtonText>
          </Strings>
        </Button>

        <!-- The anchor item to supply the icon/tooltip for the MenuController -->
        <Button guid="guidDynamicMenuPackageCmdSet" id="cmdidMyAnchorCommand" priority="0x0000" >
          <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" />
          <!-- This is the icon that appears on the Solution Explorer toolbar. -->
          <Icon guid="guidImages" id="bmpPicArrows"/>
          <!-- Do not show on the menu controller's drop down list-->
          <CommandFlag>NoShowOnMenuController</CommandFlag>
          <!-- Become the permanent anchor item for the menu controller -->
          <CommandFlag>FixMenuController</CommandFlag>
          <!-- The text that appears in the tooltip.-->
          <Strings>
            <ButtonText>Set Startup Project</ButtonText>
          </Strings>
        </Button>
    </Buttons>
    ```

4. Agregue un icono al proyecto (en la carpeta *Resources* ) y, a continuación, agregue la referencia a él en el archivo *. Vsct* . En este tutorial, usamos el icono de flechas que se incluye en la plantilla de proyecto.

5. Agregue una sección VisibilityConstraints fuera de la sección Commands justo antes de la sección Symbols. (Puede recibir una advertencia si la agrega después de símbolos). En esta sección se asegura de que el controlador de menú solo aparece cuando se carga una solución con varios proyectos.

    ```xml
    <VisibilityConstraints>
         <!--Make the MenuController show up only when there is a solution with more than one project loaded-->
        <VisibilityItem guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" context="UICONTEXT_SolutionHasMultipleProjects"/>
    </VisibilityConstraints>
    ```

## <a name="implement-the-dynamic-menu-command"></a>Implementar el comando de menú dinámico
 Cree una clase de comando de menú dinámico que herede de <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> . En esta implementación, el constructor especifica un predicado que se va a usar para los comandos coincidentes. Debe invalidar el <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> método para utilizar este predicado con el fin de establecer la <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> propiedad, que identifica el comando que se va a invocar.

1. Cree un nuevo archivo de clase de C# denominado *DynamicItemMenuCommand. CS* y agregue una clase denominada **DynamicItemMenuCommand** que herede de <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> :

    ```csharp
    class DynamicItemMenuCommand : OleMenuCommand
    {

    }

    ```

2. Agregue lo siguiente mediante directivas:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    using System.ComponentModel.Design;
    ```

3. Agregue un campo privado para almacenar el predicado de coincidencia:

    ```csharp
    private Predicate<int> matches;

    ```

4. Agregue un constructor que herede del <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> constructor y especifique un controlador de comandos y un <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> controlador. Agregue un predicado para que coincida con el comando:

    ```csharp
    public DynamicItemMenuCommand(CommandID rootId, Predicate<int> matches, EventHandler invokeHandler, EventHandler beforeQueryStatusHandler)
        : base(invokeHandler, null /*changeHandler*/, beforeQueryStatusHandler, rootId)
    {
        if (matches == null)
        {
            throw new ArgumentNullException("matches");
        }

        this.matches = matches;
    }
    ```

5. Invalide el <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> método para que llame al predicado matches y establezca la <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> propiedad:

    ```csharp
    public override bool DynamicItemMatch(int cmdId)
    {
        // Call the supplied predicate to test whether the given cmdId is a match.
        // If it is, store the command id in MatchedCommandid
        // for use by any BeforeQueryStatus handlers, and then return that it is a match.
        // Otherwise clear any previously stored matched cmdId and return that it is not a match.
        if (this.matches(cmdId))
        {
            this.MatchedCommandId = cmdId;
            return true;
        }

        this.MatchedCommandId = 0;
        return false;
    }
    ```

## <a name="add-the-command"></a>Agregar el comando
 El constructor DynamicMenu es donde se configuran los comandos de menú, incluidos los menús dinámicos y los elementos de menú.

1. En *DynamicMenuPackage. CS*, agregue el GUID del conjunto de comandos y el identificador de comando:

    ```csharp
    public const string guidDynamicMenuPackageCmdSet = "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file
    public const uint cmdidMyCommand = 0x104;
    ```

2. En el archivo *DynamicMenu. CS* , agregue las siguientes directivas Using:

    ```csharp
    using EnvDTE;
    using EnvDTE80;
    using System.ComponentModel.Design;
    ```

3. En la `DynamicMenu` clase, agregue un campo privado **DTE2**.

    ```csharp
    private DTE2 dte2;
    ```

4. Agregue un campo rootItemId privado:

    ```csharp
    private int rootItemId = 0;
    ```

5. En el constructor DynamicMenu, agregue el comando de menú. En la siguiente sección definiremos el controlador de comandos, el `BeforeQueryStatus` controlador de eventos y el predicado Match.

    ```csharp
    private DynamicMenu(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException(nameof(package));
        }

        this.package = package;

        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        if (commandService != null)
        {
            // Add the DynamicItemMenuCommand for the expansion of the root item into N items at run time.
            CommandID dynamicItemRootId = new CommandID(new Guid(DynamicMenuPackageGuids.guidDynamicMenuPackageCmdSet), (int)DynamicMenuPackageGuids.cmdidMyCommand);
            DynamicItemMenuCommand dynamicMenuCommand = new DynamicItemMenuCommand(dynamicItemRootId,
                IsValidDynamicItem,
                OnInvokedDynamicItem,
                OnBeforeQueryStatusDynamicItem);
                commandService.AddCommand(dynamicMenuCommand);
                }

        dte2 = (DTE2)this.ServiceProvider.GetService(typeof(DTE));
    }
    ```

## <a name="implement-the-handlers"></a>Implementar los controladores
 Para implementar elementos de menú dinámicos en un controlador de menú, debe controlar el comando cuando se hace clic en un elemento dinámico. También debe implementar la lógica que establece el estado del elemento de menú. Agregue los controladores a la `DynamicMenu` clase.

1. Para implementar el comando **establecer proyecto de inicio** , agregue el controlador de eventos **OnInvokedDynamicItem** . Busca el proyecto cuyo nombre es el mismo que el texto del comando que se ha invocado y lo establece como proyecto de inicio estableciendo su ruta de acceso absoluta en la <xref:EnvDTE.SolutionBuild.StartupProjects%2A> propiedad.

    ```csharp
    private void OnInvokedDynamicItem(object sender, EventArgs args)
    {
        DynamicItemMenuCommand invokedCommand = (DynamicItemMenuCommand)sender;
        // If the command is already checked, we don't need to do anything
        if (invokedCommand.Checked)
            return;

        // Find the project that corresponds to the command text and set it as the startup project
        var projects = dte2.Solution.Projects;
        foreach (Project proj in projects)
        {
            if (invokedCommand.Text.Equals(proj.Name))
            {
                dte2.Solution.SolutionBuild.StartupProjects = proj.FullName;
                return;
            }
        }
    }
    ```

2. Agregue el `OnBeforeQueryStatusDynamicItem` controlador de eventos. Este es el controlador al que se llama antes de un `QueryStatus` evento. Determina si el elemento de menú es un elemento "real", es decir, no es el elemento de marcador de posición y si el elemento ya está activado (lo que significa que el proyecto ya está establecido como proyecto de inicio).

    ```csharp
    private void OnBeforeQueryStatusDynamicItem(object sender, EventArgs args)
    {
        DynamicItemMenuCommand matchedCommand = (DynamicItemMenuCommand)sender;
        matchedCommand.Enabled = true;
        matchedCommand.Visible = true;

        // Find out whether the command ID is 0, which is the ID of the root item.
        // If it is the root item, it matches the constructed DynamicItemMenuCommand,
         // and IsValidDynamicItem won't be called.
        bool isRootItem = (matchedCommand.MatchedCommandId == 0);

        // The index is set to 1 rather than 0 because the Solution.Projects collection is 1-based.
        int indexForDisplay = (isRootItem ? 1 : (matchedCommand.MatchedCommandId - (int) DynamicMenuPackageGuids.cmdidMyCommand) + 1);

        matchedCommand.Text = dte2.Solution.Projects.Item(indexForDisplay).Name;

        Array startupProjects = (Array)dte2.Solution.SolutionBuild.StartupProjects;
        string startupProject = System.IO.Path.GetFileNameWithoutExtension((string)startupProjects.GetValue(0));

        // Check the command if it isn't checked already selected
        matchedCommand.Checked = (matchedCommand.Text == startupProject);

        // Clear the ID because we are done with this item.
        matchedCommand.MatchedCommandId = 0;
    }
    ```

## <a name="implement-the-command-id-match-predicate"></a>Implementar el predicado de coincidencia de identificador de comando

Ahora, implemente el predicado Match. Necesitamos determinar dos cosas: en primer lugar, si el identificador de comando es válido (es mayor o igual que el identificador de comando declarado) y el segundo, si especifica un proyecto posible (es menor que el número de proyectos de la solución).

```csharp
private bool IsValidDynamicItem(int commandId)
{
    // The match is valid if the command ID is >= the id of our root dynamic start item
    // and the command ID minus the ID of our root dynamic start item
    // is less than or equal to the number of projects in the solution.
    return (commandId >= (int)DynamicMenuPackageGuids.cmdidMyCommand) && ((commandId - (int)DynamicMenuPackageGuids.cmdidMyCommand) < dte2.Solution.Projects.Count);
}
```

## <a name="set-the-vspackage-to-load-only-when-a-solution-has-multiple-projects"></a>Establecer el VSPackage para cargar solo cuando una solución tiene varios proyectos
 Dado que el comando **establecer proyecto de inicio** no tiene sentido a menos que la solución activa tenga más de un proyecto, puede establecer el VSPackage en carga automática solo en ese caso. Se usa <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> junto con el contexto de la interfaz de usuario <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids.SolutionHasMultipleProjects> . En el archivo *DynamicMenuPackage. CS* , agregue los siguientes atributos a la clase DynamicMenuPackage:

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
[ProvideMenuResource("Menus.ctmenu", 1)]
[ProvideAutoLoad(UIContextGuids.SolutionHasMultipleProjects)]
[Guid(DynamicMenuPackage.PackageGuidString)]
public sealed class DynamicMenuItemsPackage : Package
{}
```

## <a name="test-the-set-startup-project-command"></a>Prueba del comando establecer proyecto de inicio
 Ahora puede probar el código.

1. Compile la solución y comience la depuración. Debería aparecer la instancia experimental.

2. En la instancia experimental, abra una solución que tenga más de un proyecto.

     Debería ver el icono de flecha en la barra de herramientas **Explorador de soluciones** . Al expandirlo, deben aparecer los elementos de menú que representan los distintos proyectos de la solución.

3. Cuando se activa uno de los proyectos, se convierte en el proyecto de inicio.

4. Cuando se cierra la solución o se abre una solución que solo tiene un proyecto, el icono de la barra de herramientas debe desaparecer.

## <a name="see-also"></a>Consulte también
- [Comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md)
- [Cómo agrega VSPackages los elementos de la interfaz de usuario](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
