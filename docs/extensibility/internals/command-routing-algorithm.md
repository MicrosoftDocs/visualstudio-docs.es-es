---
title: "Algoritmo de enrutamiento de comandos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "comandos de enrutamiento"
  - "enrutamiento de comandos"
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# Algoritmo de enrutamiento de comandos
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

En Visual Studio los comandos se controlan mediante una serie de componentes diferentes. Comandos se enrutan desde el contexto más interno, que se basa en la selección actual, en el contexto más externo \(también conocido como global\). Para obtener más información, consulta [Disponibilidad](../../extensibility/internals/command-availability.md).  
  
## Orden de resolución de comando  
 Los comandos se pasen a través de los niveles de contexto de los comandos siguientes:  
  
1.  Complementos: El entorno ofrece primero el comando para los complementos que están presentes.  
  
2.  Comandos de prioridad: estos comandos se registran mediante <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget>. Se denominan para todos los comandos de Visual Studio y se llaman en el orden en que se registraron.  
  
3.  Comandos del menú contextual: se ofrece por primera vez un comando de un menú contextual para el destino del comando que se proporciona en el menú contextual y después de que el enrutamiento típicos.  
  
4.  Barra de herramientas del conjunto de destinos de comando: estos destinos de comando se registran cuando se llama a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A>. El `pCmdTarget` del parámetro puede ser `null`. Si no es `null`, a continuación, se utiliza este destino de comando para actualizar los comandos de la barra de herramientas que se va a configurar. Si está instalando el shell de la barra de herramientas, a continuación, pasa el marco de ventana como la `pCmdTarget` para que todas las actualizaciones de los comandos en el flujo de la barra de herramientas a través del marco de ventana, incluso cuando no está en el foco.  
  
5.  Ventana de herramientas: Herramienta de windows, que normalmente se implementan el <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> de la interfaz, también debe implementar la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> de la interfaz para que Visual Studio pueda obtener el destino del comando cuando la ventana de herramientas es la ventana activa. Sin embargo, si la ventana de herramienta que tiene el foco es el **proyecto** ventana y, a continuación, el comando se enruta a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfaz que es el elemento primario común de los elementos seleccionados. Si esta selección abarca varios proyectos, el comando se enruta a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> jerarquía. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfaz contiene la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> métodos que son análogos a los comandos correspondientes de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz.  
  
6.  Ventana de documento: Si el comando tiene el indicador de RouteToDocs establecido en su archivo vsct, Visual Studio busca un destino de comando en el objeto de vista de documento, que es una instancia de un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interfaz o una instancia de un objeto de documento \(normalmente un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> interfaz o un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interfaz\). Si el objeto de vista de documento no admite el comando, Visual Studio enruta el comando para el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz que se devuelve. \(Esto es una interfaz opcional para objetos de datos de documentos\).  
  
7.  Jerarquía actual: la jerarquía actual puede ser el proyecto que posee la ventana de documento activo o la jerarquía seleccionada en **el Explorador de soluciones**. Visual Studio busca la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz que se implementa en la jerarquía actual o el activa. La jerarquía debe admitir comandos que son válidos cuando la jerarquía esté activa, incluso si una ventana de documento de un elemento de proyecto tiene el foco. Sin embargo, los comandos que aplican solo cuando **el Explorador de soluciones** tiene foco debe ser compatibles con el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfaz y su <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>métodos.  
  
     **Cortar**, **copia**, **Pegar**, **Eliminar**, **cambiar el nombre de**, **ENTRAR**, y **DoubleClick** comandos requieren un tratamiento especial. Para obtener información sobre cómo controlar **Eliminar** y **quitar** comandos en las jerarquías, consulte el <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler> interfaz.  
  
8.  Global: Si un comando no se ha controlado por los contextos mencionados anteriormente, Visual Studio intenta enrutar a VSPackage que posee un comando que implementa el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz. Si ya no se ha cargado el VSPackage, no se carga cuando se llama a Visual Studio la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método. El VSPackage se carga solo cuando el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> se llama al método.  
  
## Vea también  
 [Diseño de comando](../../extensibility/internals/command-design.md)