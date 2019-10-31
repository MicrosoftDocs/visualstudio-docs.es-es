---
title: Crear comandos disponibles | Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- best practices, menu and toolbar commands
- toolbars [Visual Studio], best practices
- menu commands, best practices
ms.assetid: 3ffc4312-c6db-4759-a946-a4bb85f4a17a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d30d71290c08019acfdc75313516d8b1b1c4be3a
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186361"
---
# <a name="making-commands-available"></a>Crear comandos disponibles

Cuando se agregan varios VSPackages a Visual Studio, la interfaz de usuario (UI) puede estar sobrellenada con comandos. Puede programar el paquete para ayudar a reducir este problema, como se indica a continuación:

- Programe el paquete para que se cargue solo cuando lo requiera un usuario.

- Programe el paquete para que sus comandos se muestren solo cuando puedan ser necesarios en el contexto del estado actual del entorno de desarrollo integrado (IDE).

## <a name="delayed-loading"></a>Carga retrasada

La forma habitual de habilitar la carga retrasada es diseñar el VSPackage para que sus comandos se muestren en la interfaz de usuario, pero el propio paquete no se carga hasta que un usuario hace clic en uno de los comandos. Para ello, en el archivo. Vsct, cree comandos que no tengan ninguna marca de comandos.

En el ejemplo siguiente se muestra la definición de un comando de menú de un archivo. Vsct. Este es el comando generado por la plantilla de paquete de Visual Studio cuando se selecciona la opción de **comando de menú** de la plantilla.

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

En el ejemplo, si el grupo primario, `MyMenuGroup`, es un elemento secundario de un menú de nivel superior, como el menú **herramientas** , el comando estará visible en ese menú, pero el paquete que ejecuta el comando no se cargará hasta que un usuario haga clic en el comando. Sin embargo, al programar el comando para implementar la interfaz <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, puede habilitar el paquete para que se cargue cuando el menú que contiene el comando se expande por primera vez.

Tenga en cuenta que la carga retrasada también puede mejorar el rendimiento de inicio.

## <a name="current-context-and-the-visibility-of-commands"></a>Contexto actual y la visibilidad de los comandos

Puede programar comandos de VSPackage para que estén visibles u ocultos, en función del estado actual de los datos del VSPackage o de las acciones que son relevantes actualmente. Puede habilitar el VSPackage para establecer el estado de sus comandos, normalmente mediante una implementación del método <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> desde la interfaz de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, pero esto requiere que se cargue el VSPackage antes de poder ejecutar el código. En su lugar, se recomienda que habilite el IDE para administrar la visibilidad de los comandos sin cargar el paquete. Para ello, en el archivo. Vsct, asocie comandos con uno o más contextos de la interfaz de usuario especiales. Estos contextos de la interfaz de usuario se identifican mediante un GUID denominado *GUID de contexto de comando*.

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] supervisa los cambios resultantes de las acciones del usuario, como cargar un proyecto o pasar de la edición a la compilación. A medida que se producen cambios, se modifica automáticamente la apariencia del IDE. En la tabla siguiente se muestran cuatro contextos principales del cambio de IDE que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] supervisa.

| Tipo de contexto | Descripción |
|-------------------------| - |
| Tipo de proyecto activo | Para la mayoría de los tipos de proyecto, este valor `GUID` es el mismo que el GUID del VSPackage que implementa el proyecto. Sin embargo, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] proyectos usan el tipo de proyecto `GUID` como valor. |
| Ventana activa | Normalmente, se trata de la última ventana de documento activa que establece el contexto de la interfaz de usuario actual para los enlaces de teclado. Sin embargo, también podría ser una ventana de herramientas que tiene una tabla de enlace de teclado similar al explorador Web interno. En el caso de las ventanas de documentos con varias pestañas, como el editor HTML, cada pestaña tiene un contexto de comando diferente `GUID`. |
| Servicio de lenguaje activo | El servicio de lenguaje que está asociado con el archivo que se muestra actualmente en un editor de texto. |
| Ventana de herramientas activa | Ventana de herramientas que está abierta y tiene el foco. |

Un quinto área de contexto principal es el estado de la interfaz de usuario del IDE. Los contextos de la interfaz de usuario se identifican mediante el contexto de comando activo `GUID`s, como se indica a continuación:

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

Estos GUID se marcan como activo o inactivo, dependiendo del estado actual del IDE. Varios contextos de la interfaz de usuario pueden estar activos al mismo tiempo.

### <a name="hide-and-display-commands-based-on-context"></a>Ocultar y mostrar comandos basados en el contexto

Puede mostrar u ocultar un comando de paquete en el IDE sin cargar el propio paquete. Para ello, defina el comando en el archivo. Vsct del paquete con las marcas de comando `DefaultDisabled`, `DefaultInvisible`y `DynamicVisibility` y agregue uno o varios elementos [VisibilityItem](../../extensibility/visibilityitem-element.md) a la sección [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) . Cuando un contexto de comando especificado `GUID` se activa, se muestra el comando sin cargar el paquete.

### <a name="custom-context-guids"></a>GUID de contexto personalizado

Si aún no se ha definido un GUID de contexto de comando adecuado, puede definir uno en el VSPackage y, a continuación, programarlo para que esté activo o inactivo según sea necesario para controlar la visibilidad de los comandos. Use el servicio <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> para:

- Registre los GUID de contexto (llamando al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A>).

- Obtiene el estado de un `GUID` de contexto (llamando al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>).

- Activar y desactivar el `GUID`de contexto (llamando al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A>).

    > [!CAUTION]
    > Asegúrese de que el VSPackage no afecte al estado de ningún GUID de contexto existente porque otros VSPackages pueden depender de ellos.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente de un comando VSPackage se muestra la visibilidad dinámica de un comando administrado por contextos de comandos sin cargar el VSPackage.

El comando se establece para habilitarse y mostrarse siempre que exista una solución; es decir, siempre que uno de los siguientes GUID de contexto de comando esté activo:

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

En el ejemplo, observe que cada marca de comando es un elemento de [marca de comando](../../extensibility/command-flag-element.md) independiente.

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

Observe también que todos los contextos de la interfaz de usuario deben proporcionarse en un elemento de `VisibilityItem` independiente, como se indica a continuación.

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

- [Agregar un comando a la barra de herramientas Explorador de soluciones](../../extensibility/adding-a-command-to-the-solution-explorer-toolbar.md)
- [Adición de elementos de la interfaz de usuario por VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Enrutamiento de comandos en VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)
- [Adición dinámica de elementos de menú](../../extensibility/dynamically-adding-menu-items.md)
