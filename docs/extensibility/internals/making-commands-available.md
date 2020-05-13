---
title: Hacer que los comandos estén disponibles en el sistema de comando Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- best practices, menu and toolbar commands
- toolbars [Visual Studio], best practices
- menu commands, best practices
ms.assetid: 3ffc4312-c6db-4759-a946-a4bb85f4a17a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d64df85516e0a1ac326f8d40558755718c4644c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707334"
---
# <a name="making-commands-available"></a>Puesta a disposición de los comandos

Cuando se agregan varios VSPackages a Visual Studio, la interfaz de usuario (UI) puede estar superpoblada con comandos. Puede programar su paquete para ayudar a reducir este problema, de la siguiente manera:

- Programe el paquete para que se cargue solo cuando un usuario lo requiera.

- Programe el paquete para que sus comandos se muestren solo cuando puedan ser necesarios en el contexto del estado actual del entorno de desarrollo integrado (IDE).

## <a name="delayed-loading"></a>Carga retrasada

La forma típica de habilitar la carga retrasada es diseñar el VSPackage para que sus comandos se muestran en la interfaz de usuario, pero el paquete en sí no se carga hasta que un usuario hace clic en uno de los comandos. Para ello, en el archivo .vsct, cree comandos que no tengan marcas de comando.

En el ejemplo siguiente se muestra la definición de un comando de menú de un archivo .vsct. Este es el comando generado por la plantilla de paquete de Visual Studio cuando se selecciona la opción **Comando** de menú de la plantilla.

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

En el ejemplo, si `MyMenuGroup`el grupo primario, , es un elemento secundario de un menú de nivel superior como el menú **Herramientas,** el comando estará visible en ese menú, pero el paquete que ejecuta el comando no se cargará hasta que un usuario haga clic en el comando. Sin embargo, al programar <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> el comando para implementar la interfaz, puede habilitar el paquete para que se cargue cuando se expanda por primera vez el menú que contiene el comando.

Tenga en cuenta que la carga retrasada también puede mejorar el rendimiento de inicio.

## <a name="current-context-and-the-visibility-of-commands"></a>Contexto actual y visibilidad de los comandos

Puede programar comandos de VSPackage para que sean visibles u ocultos, dependiendo del estado actual de los datos de VSPackage o las acciones que son relevantes actualmente. Puede habilitar el VSPackage para establecer el estado de sus comandos, normalmente mediante una implementación del <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> método desde la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz, pero esto requiere que el VSPackage se cargue antes de que pueda ejecutar el código. En su lugar, se recomienda habilitar el IDE para administrar la visibilidad de los comandos sin cargar el paquete. Para ello, en el archivo .vsct, asocie comandos a uno o varios contextos de interfaz de usuario especiales. Estos contextos de interfaz de usuario se identifican mediante un GUID conocido como GUID de contexto de *comando*.

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]supervisa los cambios resultantes de las acciones del usuario, como cargar un proyecto o pasar de la edición a la creación. A medida que se producen cambios, la apariencia del IDE se modifica automáticamente. En la tabla siguiente se muestran [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] cuatro contextos principales de cambio IDE que supervisa.

| Tipo de contexto | Descripción |
|-------------------------| - |
| Tipo de proyecto activo | Para la mayoría `GUID` de los tipos de proyecto, este valor es el mismo que el GUID del VSPackage que implementa el proyecto. Sin [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] embargo, los `GUID` proyectos usan el tipo de proyecto como valor. |
| Ventana activa | Normalmente, esta es la última ventana de documento activa que establece el contexto de interfaz de usuario actual para los enlaces de clave. Sin embargo, también podría ser una ventana de herramientas que tiene una tabla de enlace de claves que se asemeja al explorador web interno. Para ventanas de documentos con varias pestañas, como `GUID`el editor HTML, cada pestaña tiene un contexto de comando diferente. |
| Servicio de idiomas activos | El servicio de lenguaje asociado al archivo que se muestra actualmente en un editor de texto. |
| Ventana de herramientas activas | Una ventana de herramientas que está abierta y tiene el foco. |

Una quinta área de contexto principal es el estado de la interfaz de usuario del IDE. Los contextos de interfaz `GUID`de usuario se identifican mediante contextos de comando activos, como se indica a continuación:

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

Estos GUID se marcan como activos o inactivos, dependiendo del estado actual del IDE. Varios contextos de interfaz de usuario pueden estar activos al mismo tiempo.

### <a name="hide-and-display-commands-based-on-context"></a>Ocultar y mostrar comandos basados en el contexto

Puede mostrar u ocultar un comando de paquete en el IDE sin cargar el propio paquete. Para ello, defina el comando en el archivo .vsct del paquete mediante `DefaultDisabled`los indicadores de comando , `DefaultInvisible`, y `DynamicVisibility` agregando uno o varios elementos [VisibilityItem](../../extensibility/visibilityitem-element.md) a la sección [VisibilityConstraints.](../../extensibility/visibilityconstraints-element.md) Cuando un contexto `GUID` de comando especificado se activa, el comando se muestra sin cargar el paquete.

### <a name="custom-context-guids"></a>GUID de contexto personalizado

Si aún no se ha definido un GUID de contexto de comando adecuado, puede definir uno en el VSPackage y, a continuación, programarlo para que esté activo o inactivo según sea necesario para controlar la visibilidad de los comandos. Utilice <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> el servicio para:

- Registrar GUID de contexto (mediante una llamada al <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> método).

- Obtener el estado `GUID` de un <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> contexto (mediante una llamada al método).

- Active `GUID`y desactive context s <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> (llamando al método).

    > [!CAUTION]
    > Asegúrese de que el VSPackage no afecta al estado de cualquier GUID de contexto existente porque otros VSPackages pueden depender de ellos.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente de un comando VSPackage se muestra la visibilidad dinámica de un comando administrado por contextos de comando sin cargar el VSPackage.

El comando se establece para habilitarse y mostrarse siempre que exista una solución; es decir, siempre que uno de los siguientes GUID de contexto de comando esté activo:

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

En el ejemplo, observe que cada indicador de comando es un elemento [de indicador](../../extensibility/command-flag-element.md) de comando independiente.

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

Observe también que cada contexto de `VisibilityItem` interfaz de usuario debe darse en un elemento independiente, como se indica a continuación.

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

- [Agregue un comando a la barra de herramientas del Explorador de soluciones](../../extensibility/adding-a-command-to-the-solution-explorer-toolbar.md)
- [Cómo VSPackages agrega elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Enrutamiento de comandos en VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)
- [Adición dinámica de elementos de menú](../../extensibility/dynamically-adding-menu-items.md)
