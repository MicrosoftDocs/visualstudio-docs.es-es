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
  - "comandos, contexto"
  - "elementos de menú, contextos de visibilidad"
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
caps.latest.revision: 34
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 34
---
# Disponibilidad de los comandos
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

El contexto de Visual Studio determina qué comandos están disponibles. El contexto puede cambiar en función del proyecto actual, el editor actual, los VSPackages que se cargan y otros aspectos del entorno de desarrollo integrado \(IDE\).  
  
## Contextos de comando  
 Los contextos de comando siguientes son las más comunes.  
  
-   **IDE** comandos proporcionados por el IDE están siempre disponibles.  
  
-   **VSPackage** puede definir VSPackages cuando son comandos para mostrar u ocultar.  
  
-   **Proyecto** comandos proyecto sólo aparecen para el proyecto seleccionado actualmente.  
  
-   **Editor** solo editor puede estar activo simultáneamente. Hay comandos desde el editor activo. Un editor trabaja en estrecha colaboración con un servicio de lenguaje. El servicio de lenguaje debe procesar los comandos en el contexto del editor asociado.  
  
-   **Tipo de archivo** un editor puede cargar más de un tipo de archivo. Los comandos disponibles pueden cambiar según el tipo de archivo.  
  
-   **Ventana activa** la última ventana de documento activo, Establece el contexto de la interfaz de usuario para los enlaces de teclado. Sin embargo, una ventana de herramientas que tiene una tabla de enlace de clave que es similar a la del explorador Web interno también puede establecer el contexto de la interfaz de usuario. Para ventanas de documento con múltiples fichas, como el editor HTML, cada pestaña tiene un contexto de otro comando GUID. Una vez registrada una ventana de herramientas, siempre está disponible en la **vista** menú.  
  
-   **El contexto de interfaz de usuario** contextos de interfaz de usuario se identifican mediante los valores de la <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> clase, por ejemplo, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionBuilding> cuando se está generando la solución, o <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_Debugging> cuando el depurador está activo. Varios contextos de interfaz de usuario pueden estar activos al mismo tiempo.  
  
## Definir los GUID de contexto personalizado  
 Si un contexto de comando adecuado que GUID no se ha definido, puede definir uno en el VSPackage y programarlo para estar activas o inactivas según sea necesario para controlar la visibilidad de los comandos.  
  
1.  Registrar los GUID de contexto llamando a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> \(método\).  
  
2.  Obtener el estado de un GUID de contexto llamando a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> \(método\).  
  
3.  Activar y desactivar la GUID de contexto llamando a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> \(método\).  
  
    > [!CAUTION]
    >  Asegúrese de que su VSPackage no afecta a ningún contexto existente GUID porque otros VSPackages puede depender de ellas.  
  
## Vea también  
 [Objetos de contexto de selección](../../extensibility/internals/selection-context-objects.md)   
 [Cómo VSPackages agregar elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)