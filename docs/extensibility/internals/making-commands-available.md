---
title: "Disponibilidad de los comandos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "menús [Visual Studio SDK], comandos"
  - "mejores prácticas, comandos de menú y barra de herramientas"
  - "barras de herramientas [Visual Studio], prácticas recomendadas"
  - "comandos de menú, prácticas recomendadas"
ms.assetid: 3ffc4312-c6db-4759-a946-a4bb85f4a17a
caps.latest.revision: 35
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 35
---
# Disponibilidad de los comandos
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cuando se agregan varios VSPackages a Visual Studio, la interfaz de usuario \(IU\) puede ser demasiado repleto con comandos. Puede programar el paquete para ayudar a reducir este problema, como sigue:  
  
-   El paquete del programa para que se cargue cuando un usuario lo requiere.  
  
-   El paquete del programa para que sus comandos se muestran únicamente cuando se necesite en el contexto del estado actual del entorno de desarrollo integrado \(IDE\).  
  
## Carga retrasada  
 La forma habitual para habilitar la carga retrasada es diseñar el VSPackage para que sus comandos se muestran en la interfaz de usuario, pero el paquete en sí no se cargará hasta que un usuario hace clic en uno de los comandos. Para ello, en el archivo .vsct, cree los comandos que no tienen ningún indicador de comando.  
  
 En el ejemplo siguiente se muestra la definición de un comando de menú de un archivo de vsct. Este es el comando generado por la plantilla de paquete de Visual Studio cuando el **comando de menú** está seleccionada la opción en la plantilla.  
  
 [!CODE [TopLevelMenu#03](../CodeSnippet/VS_Snippets_VSSDK/toplevelmenu#03)]  
  
 En el ejemplo, si el grupo primario, `MyMenuGroup`, es un elemento secundario de un menú de nivel superior como el **herramientas** menú, el comando será visible en ese menú, pero no se cargará el paquete que se ejecuta el comando hasta que un usuario hace clic en el comando. Sin embargo, mediante programación el comando para implementar la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz, puede habilitar el paquete que se cargarán cuando se expande el menú que contiene el comando por primera vez.  
  
 Observe que la carga diferida puede mejorar también el rendimiento de inicio.  
  
## Contexto actual y la visibilidad de los comandos  
 Puede programar comandos de VSPackage que esté visible u oculto, dependiendo del estado actual de los datos de VSPackage o las acciones que están actualmente relevantes. Puede habilitar el VSPackage establecer el estado de los comandos, normalmente mediante una implementación de la <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> método desde el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz, pero esto requiere el VSPackage cargarse antes de poder ejecutar el código. En su lugar, se recomienda que habilite el IDE administrar la visibilidad de los comandos sin necesidad de cargar el paquete. Para ello, en el archivo .vsct, asociar comandos a uno o varios contextos de interfaz de usuario especiales. Estos contextos de interfaz de usuario se identifican mediante un GUID conocido como un *GUID del contexto de comandos*.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] controla los cambios resultantes de las acciones del usuario, como cargar un proyecto o de edición para la creación. Cuando se producen cambios, automáticamente se modifica el aspecto del IDE. La siguiente tabla muestra cuatro contextos principales del IDE que cambian [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] monitores.  
  
|Tipo de contexto|Descripción|  
|----------------------|-----------------|  
|Tipo de proyecto activo|Para la mayoría de los tipos de proyecto, esto `GUID` valor es el mismo que el GUID del VSPackage que implemente el proyecto. Sin embargo, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] proyectos usan el tipo de proyecto `GUID` como el valor.|  
|Ventana activa|Normalmente, se trata de la última ventana de documento activo que establece el contexto actual de la interfaz de usuario para los enlaces de teclado. Sin embargo, también podría ser una ventana de herramientas que tiene una tabla de enlace de clave que es similar a la del explorador Web interno. Para ventanas de documento con múltiples fichas, como el editor HTML, cada pestaña tiene un contexto de otro comando `GUID`.|  
|Servicio de lenguaje Active|El servicio de lenguaje que está asociado con el archivo que se muestra actualmente en un editor de texto.|  
|Ventana de herramientas activa|Una ventana de herramientas que está abierto y tiene el foco.|  
  
 Un área de contexto principales quinto es el estado de la interfaz de usuario del IDE. Contextos de la interfaz de usuario se identifican mediante el contexto de comandos activo `GUID`s, como sigue:  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionBuilding>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_Debugging>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_Dragging>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_FullScreenMode>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_DesignMode>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_NoSolution>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionExists>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_EmptySolution>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasSingleProject>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasMultipleProjects>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_CodeWindow>  
  
 Estos GUID se marcan como activo o inactivo, dependiendo del estado actual del IDE. Varios contextos de interfaz de usuario pueden estar activos al mismo tiempo.  
  
### Ocultar y mostrar comandos basados en contexto  
 Puede mostrar u ocultar un comando de paquete en el IDE sin necesidad de cargar el paquete en Sí. Para ello, defina el comando en el archivo .vsct del paquete mediante el uso de la `DefaultDisabled`, `DefaultInvisible`, y `DynamicVisibility` comando marcas y agregar uno o más [VisibilityItem](../../extensibility/visibilityitem-element.md) elementos a la [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) sección. Cuando un contexto de comando especificado `GUID` se convierte en activo, el comando se muestra sin necesidad de cargar el paquete.  
  
### GUID de contexto personalizado  
 Si un contexto de comando adecuado que GUID no se ha definido, puede definir uno en el VSPackage y programarlo para estar activas o inactivas según sea necesario para controlar la visibilidad de los comandos. Utilice la <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> servicio:  
  
-   Registrar identificadores GUID de contexto \(mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> método\).  
  
-   Obtener el estado de un contexto de `GUID` \(mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> método\).  
  
-   Activar contexto `GUID`s y desactivar \(mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> método\).  
  
    > [!CAUTION]
    >  Asegúrese de que su VSPackage no afecta el estado de cualquier contexto existente GUID porque otros VSPackages puede depender de ellas.  
  
## Ejemplo  
 El siguiente ejemplo de un comando de VSPackage muestra la visibilidad de un comando que se administra los contextos de comando sin cargar el VSPackage dinámica.  
  
 El comando se establece en habilitado y muestra cada vez que existe una solución; es decir, siempre que uno del contexto del comando siguiente GUID está activado:  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_EmptySolution>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasMultipleProjects>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasSingleProject>  
  
 En el ejemplo, observe que cada marca de comandos es otro [comando marca](../../extensibility/command-flag-element.md) elemento.  
  
 [!CODE [DynamicVisibility#01](DynamicVisibility#01)]  
  
 Observe también que se deben proporcionar todos los contextos de interfaz de usuario en otro `VisibilityItem` elemento como sigue.  
  
 [!CODE [DynamicVisibility#02](DynamicVisibility#02)]  
  
## Vea también  
 [MenuCommands frente a OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md)   
 [Cómo VSPackages agregar elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Enrutamiento de comandos en VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)   
 [Agregar dinámicamente elementos de menú](../../extensibility/dynamically-adding-menu-items.md)