---
title: "Lista de comprobaci&#243;n: Crear un servicio de lenguaje heredado | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Servicios de lenguaje"
  - "Servicios de lenguaje, código nativo"
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Lista de comprobaci&#243;n: Crear un servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La lista de comprobación siguiente se resumen los pasos básicos que debe admitir orden de crear un servicio de lenguaje para el publicador de la base de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  Para integrar el servicio de lenguaje en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], debe crear un evaluador de expresiones de depuración.  Para obtener más información, vea [Escribir un evaluador de expresiones de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) en [Extensibilidad del depurador de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md).  
  
## pasos para crear un lenguaje Service  
  
1.  Implemente la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>.  
  
    -   En el paquete VSPackage, implemente la interfaz de <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> para proporcionar el servicio de lenguaje.  
  
    -   Coloque el servicio de lenguaje a disposición del \(IDE\) entorno de desarrollo integrado en la implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> .  
  
2.  Implemente la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> en la clase de servicio principal del lenguaje.  
  
     La interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> es el punto inicial de interacción entre el editor básico y el servicio de lenguaje.  
  
### características opcionales  
 Las siguientes características son opcionales y se pueden implementar en cualquier orden.  Estas características aumentan la funcionalidad del servicio de lenguaje.  
  
-   Colorear la sintaxis  
  
     Implemente la interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>.  La implementación de esta interfaz si la información del analizador devuelve información de color adecuada.  
  
     El método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> devuelve la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> .  Una instancia independiente de colorizer se crea para cada búfer de texto, por lo que debe implementar la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> por separado.  Para obtener más información, vea [Colores en un servicio de lenguaje heredado de sintaxis](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).  
  
-   Ventana de código  
  
     Implemente la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> para habilitar el servicio de lenguaje para recibir notificación de cuando se crea una nueva ventana de código.  
  
     El método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> devuelve la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> .  El servicio de lenguaje puede agregar interfaz de usuario especial a la ventana de código en <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>.  El servicio de lenguaje también puede realizar cualquier procesamiento especial, como agregar un filtro de la vista de texto en <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A>.  
  
-   filtro de la vista de texto  
  
     Para proporcionar la finalización de instrucciones de IntelliSense en un servicio de, debe interceptar algunos de los comandos que la vista de texto deben de otra manera.  para interceptar estos comandos, complete los pasos siguientes:  
  
    -   Implemente <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> para participar en la cadena de comando y comandos de editor de identificador.  
  
    -   Llame al método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> y pase la implementación de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  
  
    -   Llame al método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A> cuando se desasocia de vista para pasar estos comandos no más para usted.  
  
     Los comandos que deben controlar dependen de los servicios que se proporcionan.  Para obtener más información, vea [Comandos importantes para los filtros de servicio de lenguaje](../../extensibility/internals/important-commands-for-language-service-filters.md).  
  
    > [!NOTE]
    >  la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> se debe implementar en el mismo objeto que la interfaz de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  
  
-   Finalización de instrucciones  
  
     Implemente la interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>.  
  
     Admite el comando de finalización de instrucciones \(es decir, <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>\) y llame al método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> en la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> , pasando la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> .  Para obtener más información, vea [Finalización de instrucciones en un servicio de lenguaje heredado](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).  
  
-   Sugerencias de método  
  
     Implemente la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> para proporcionar datos para la ventana de la sugerencia de método.  
  
     Instale el filtro de vista de texto para controlar los comandos correctamente, para saber cuándo mostrar una ventana de sugerencias de datos del método.  Para obtener más información, vea [Información de parámetros en un servicio de lenguaje heredado](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).  
  
-   Marcadores de error  
  
     Implemente la interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>.  
  
     Cree los objetos del marcador de error que implementan la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> y llaman al método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> , pasando la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> de objeto de marcador de error.  
  
     Cada marcador de error normalmente administra un elemento en la ventana lista de tareas.  
  
-   elementos de la lista de tareas  
  
     Implemente una clase de elemento de tarea que proporciona la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem> .  
  
     Implemente una clase de proveedor de la tarea que proporciona la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider> y la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> .  
  
     Implemente una clase de enumerador de la tarea que proporciona la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems> .  
  
     Registrar el proveedor de la tarea con el método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A> de la lista de tareas.  
  
     Obtenga la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> llamando al proveedor de servicios del servicio de lenguaje con el servicio GUID <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>.  
  
     Cree los objetos del elemento de tarea y llame al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A> en la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> cuando hay nuevos o actualizados tareas.  
  
-   Elementos de tarea con comentario  
  
     Utilice la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> y la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> para obtener los tokens de la tarea con comentario.  
  
     Obtiene una interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> de servicio de <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> .  
  
     Obtenga la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> del método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A> .  
  
     Implemente la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents> para escuchar cambios en la lista de símbolos.  
  
-   Esquematización  
  
     hay varias opciones para admitir la esquematización.  Por ejemplo, puede admitir el comando de **Contraer a definiciones** , proporcionar las regiones editor\-controladas del contorno, o para admitir las regiones cliente\-controladas.  Para obtener más información, vea [Cómo: proporcionar soporte ampliado de esquematización en un servicio de lenguaje heredado](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md).  
  
-   Registro del servicio de lenguaje  
  
     Para obtener más información sobre cómo registrar un servicio de, vea [Registrar un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service2.md) y [Administración de VSPackages](../../extensibility/managing-vspackages.md).  
  
-   Ayuda contextual  
  
     Proporcione el contexto al editor de una de las siguientes maneras:  
  
    -   Proporciona el contexto para marcadores de texto implementando la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> .  
  
 Proporcione todo el contexto de usuario implementando la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> .  
  
## Vea también  
 [Desarrollar un servicio de lenguaje](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Escribir un evaluador de expresiones de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)