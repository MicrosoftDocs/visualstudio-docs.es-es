---
title: Disposición de comandos | Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- best practices, menu and toolbar commands
- toolbars [Visual Studio], best practices
- menu commands, best practices
ms.assetid: 3ffc4312-c6db-4759-a946-a4bb85f4a17a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a14998b8dca3c14bdae4f00f1940c19b696646ff
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62909583"
---
# <a name="making-commands-available"></a>Disposición de comandos

Cuando se agregan varios VSPackages a Visual Studio, la interfaz de usuario (UI) puede convertirse en demasiado repleto con comandos. Puede programar el paquete para ayudar a reducir este problema, como sigue:

- El paquete de programa para que se cargue solo cuando un usuario lo requiere.

- El paquete del programa para que sus comandos se muestran únicamente cuando que pueden ser necesario en el contexto del estado actual del entorno de desarrollo integrado (IDE).

## <a name="delayed-loading"></a>Carga retrasada

La forma habitual para habilitar la carga retrasada es diseñar el VSPackage para que sus comandos se muestran en la interfaz de usuario, pero el propio paquete no se cargará hasta que un usuario hace clic en uno de los comandos. Para ello, en el archivo .vsct, cree los comandos que no tengan ninguna marca de comando.

El ejemplo siguiente muestra la definición de un comando de menú desde un archivo .vsct. Este es el comando generado por la plantilla de paquete de Visual Studio cuando el **comando de menú** está seleccionada la opción en la plantilla.

```xml
<Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />
  <Icon guid="guidImages" id="bmpPic1" />
  <Strings>
    <CommandName>cmdidTestCommand</CommandName>
    <ButtonText>Test Command</ButtonText>
  </Strings>
</Button>
```

En el ejemplo, si el grupo primario, `MyMenuGroup`, es un elemento secundario de un menú de nivel superior, como el **herramientas** menú, el comando será visible en ese menú, pero no se cargará el paquete que se ejecuta el comando hasta que se hace clic en el comando por el usuario. Sin embargo, mediante programación el comando para implementar el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz, puede habilitar el paquete que se cargarán cuando se expande el menú que contiene el comando por primera vez.

Tenga en cuenta que la carga diferida también puede mejorar el rendimiento de inicio.

## <a name="current-context-and-the-visibility-of-commands"></a>Contexto actual y la visibilidad de comandos

Puede programar comandos VSPackage estén visibles u ocultas, según el estado actual de los datos de VSPackage o las acciones que están actualmente pertinentes. Puede permitir que el VSPackage establecer el estado de sus comandos, normalmente mediante el uso de una implementación de la <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> método desde el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz, pero esto requiere el VSPackage que se cargue antes de poder ejecutar el código. En su lugar, se recomienda que habilite el IDE administrar la visibilidad de los comandos sin necesidad de cargar el paquete. Para ello, en el archivo .vsct, asociar comandos a uno o más contextos de interfaz de usuario especiales. Estos contextos de interfaz de usuario se identifican mediante un GUID que se conoce como un *GUID de contexto de comando*.

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] supervisa los cambios resultantes de las acciones del usuario, como cargar un proyecto o de edición a la compilación. Cuando se producen cambios, automáticamente se modifica la apariencia del IDE. La tabla siguiente muestra cuatro contextos principales del IDE que cambian [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] monitores.

| Tipo de contexto | Descripción |
|-------------------------| - |
| Tipo de proyecto activo | Para la mayoría de los tipos de proyecto, esto `GUID` valor es el mismo que el GUID del VSPackage que implemente el proyecto. Sin embargo, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] proyectos usan el tipo de proyecto `GUID` como valor. |
| Ventana activa | Normalmente, esto es la última ventana de documento activo que establece el contexto actual de la interfaz de usuario para los enlaces de teclado. Sin embargo, también podría ser una ventana de herramientas que tiene una tabla de enlace de teclado que se parece el explorador Web interno. Para ventanas de documento con múltiples fichas, como el editor HTML, cada pestaña tiene un contexto de otro comando `GUID`. |
| Servicio de lenguaje activo | El servicio de lenguaje que está asociado con el archivo que se muestra actualmente en un editor de texto. |
| Ventana de herramientas activa | Una ventana de herramientas que está abierto y tiene el foco. |

Un área de contexto principales quinto es el estado de la interfaz de usuario del IDE. Contextos de interfaz de usuario se identifican mediante el contexto de comando activo `GUID`s, tal como se indica a continuación:

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Dragging_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.FullScreenMode_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.DesignMode_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.NoSolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.CodeWindow_guid>

Estos GUID se marcan como activa o inactiva, según el estado actual del IDE. Varios contextos de interfaz de usuario pueden ser activos al mismo tiempo.

### <a name="hide-and-display-commands-based-on-context"></a>Ocultar y mostrar en función del contexto de comandos

Puede mostrar u ocultar un comando de paquete en el IDE sin tener que cargar el paquete en Sí. Para ello, defina el comando en el archivo .vsct del paquete mediante el uso de la `DefaultDisabled`, `DefaultInvisible`, y `DynamicVisibility` comando marcas y agregar uno o más [VisibilityItem](../../extensibility/visibilityitem-element.md) elementos a la [ VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) sección. Cuando un contexto de comando especificado `GUID` se convierte en activa, se muestra el comando sin tener que cargar el paquete.

### <a name="custom-context-guids"></a>GUID de contexto personalizado

Si un contexto de comando adecuado que GUID ya no está definido, puede definir uno en el paquete de VS y, a continuación, programa que esté activo o inactivo según sea necesario para controlar la visibilidad de los comandos. Use el <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> servicio:

- Registrar identificadores GUID de contexto (mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> método).

- Obtener el estado de un contexto `GUID` (mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> método).

- Activar contexto `GUID`s activar y desactivar (mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> método).

    > [!CAUTION]
    > Asegúrese de que el VSPackage no afecta el estado de los GUID de contexto existente de porque otros VSPackages que dependen de ellos.

## <a name="example"></a>Ejemplo

El siguiente ejemplo de comando VSPackage muestra la visibilidad dinámica de un comando que se administra mediante los contextos de comando sin tener que cargar el VSPackage.

Se establece el comando que se habiliten y se muestra cada vez que existe una solución; es decir, siempre que uno del contexto del comando siguiente GUID está activo:

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

En el ejemplo, observe que cada marcador de comando es otro [comando marca](../../extensibility/command-flag-element.md) elemento.

```xml
<Button guid="guidDynamicVisibilityCmdSet" id="cmdidMyCommand"
        priority="0x0100" type="Button">
  <Parent guid="guidDynamicVisibilityCmdSet" id="MyMenuGroup" />
  <Icon guid="guidImages" id="bmpPic1" />
  <CommandFlag>DefaultDisabled</CommandFlag>
  <CommandFlag>DefaultInvisible</CommandFlag>
  <CommandFlag>DynamicVisibility</CommandFlag>
  <Strings>
    <CommandName>cmdidMyCommand</CommandName>
    <ButtonText>My Command name</ButtonText>
  </Strings>
</Button>
```

Observe también que todos los contextos de interfaz de usuario deben proporcionarse en otro `VisibilityItem` elemento, como se indica a continuación.

```xml
<VisibilityConstraints>
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"
                  id="cmdidMyCommand" context="UICONTEXT_EmptySolution" />
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"
                      id="cmdidMyCommand" context="UICONTEXT_SolutionHasSingleProject" />
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"
                  id="cmdidMyCommand" context="UICONTEXT_SolutionHasMultipleProjects" />
</VisibilityConstraints>
```

## <a name="see-also"></a>Vea también

- [Agregar un comando a la barra de herramientas del explorador de soluciones](../../extensibility/adding-a-command-to-the-solution-explorer-toolbar.md)
- [MenuCommands frente a OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)
- [Adición de elementos de la interfaz de usuario por VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Enrutamiento de comandos en VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)
- [Adición dinámica de elementos de menú](../../extensibility/dynamically-adding-menu-items.md)
