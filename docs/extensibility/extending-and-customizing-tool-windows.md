---
title: "Ampliaci&#243;n y personalizaci&#243;n de ventanas de herramientas | Microsoft Docs"
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
  - "interfaces de usuario, essentials"
  - "herramienta estándar de windows,"
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# Ampliaci&#243;n y personalizaci&#243;n de ventanas de herramientas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio proporciona varios tipos diferentes de windows, por ejemplo, las ventanas de herramientas, ventanas de documento y ventanas de diálogo. Otras ventanas, como la ventana Propiedades, la ventana de salida y la ventana Lista de tareas, son tipos de ventanas de herramientas.  
  
## Ventanas de herramientas  
 Ventanas de herramientas de Visual Studio son windows suelen ser de solo lectura que no están basados en archivos. En este se diferencian de las ventanas de documento, que muestra los archivos en modo de lectura y escritura. El **herramientas**, **el Explorador de soluciones**, **propiedades** ventana, y **explorador Web** son ejemplos de ventanas de herramientas.  
  
 Para obtener información acerca de cómo crear una ventana de herramientas simple, consulte [Agregar una ventana de herramientas](../extensibility/adding-a-tool-window.md).  
  
 Para registrar una ventana de herramientas con Visual Studio, consulte [Registrar una ventana de herramientas](../extensibility/registering-a-tool-window.md).  
  
 Ventanas de herramientas son una instancia predeterminada, lo que significa que solo una instancia de la ventana de herramientas puede estar abierto a la vez. Cuando se abre una ventana de herramientas de instancia única, permanece abierta hasta que se cierra el IDE. Al cerrar una ventana de herramientas de instancia única, se cambia sólo su visibilidad. También puede crear varias instancias en ventanas de herramientas, de forma que varias instancias de la ventana pueden estar abiertos simultáneamente. Vea [Creación de una ventana de herramienta de instancias múltiples](../extensibility/creating-a-multi-instance-tool-window.md) para obtener más información.  
  
 Ventanas de herramientas pueden ser *dinámica*, lo que significa que están visibles siempre que se aplica su contexto relacionado de la interfaz de usuario. El uso de visibilidad automática puede reducir la cantidad de ventanas en el IDE. Para obtener más información, consulta [Abrir una ventana de herramientas dinámica](../extensibility/opening-a-dynamic-tool-window.md).  
  
 Ventanas de herramientas pueden ser acoplado, flotante o con pestañas en el marco del documento. El marco de ventana de herramienta proporcionado por el IDE y se utiliza para controlar el tamaño, ubicación, estado de acoplamiento y otras propiedades persistentes. El panel de la ventana de herramientas muestra el contenido. La ubicación y tamaño predeterminados aplican sólo cuando la ventana de herramientas se abre por primera vez; Después de que se conserva el estado de la ventana de herramienta.  
  
 Paneles de la ventana de herramienta pueden alojar controles de usuario WPF y admite barras de herramientas. Puede invalidar el <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> para devolver el identificador del control hospedado.  
  
 Puede agregar muchas características distintas a las ventanas de herramientas. Por ejemplo, puede agregar una barra de herramientas: [Agregar una barra de herramientas a una ventana de herramientas](../extensibility/adding-a-toolbar-to-a-tool-window.md) o un menú contextual: [Agregar un menú contextual en una ventana de herramientas](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md). Puede agregar un control de búsqueda que permite buscar elementos dentro de la ventana de herramientas: [Agregar búsqueda a una ventana de herramientas](../extensibility/adding-search-to-a-tool-window.md).  
  
 Puede suscribirse a eventos de ventana de herramienta: [Suscribirse a un evento](../extensibility/subscribing-to-an-event.md).  
  
## Ampliación de ventanas de herramientas existentes  
 Puede agregar información acerca de la ventana de herramientas a una nueva **opciones** página y un nuevo valor en el **propiedades** página, escribir en el **lista de tareas** y **salida** windows. Para obtener más información, vea [Extender propiedades, lista de tareas, salida y ventanas de opciones](../extensibility/extending-the-properties-task-list-output-and-options-windows.md) y [Extender propiedades, lista de tareas, salida y ventanas de opciones](../extensibility/extending-the-properties-task-list-output-and-options-windows.md).  
  
## Cuadros de diálogo modales  
 En una extensión de Visual Studio debe crear cuadros de diálogo modales derivando de <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName>, que le permite controlar de ellos y el resto de la interfaz de usuario. Para obtener más información, consulte.[Creación y administración de cuadros de diálogo modales](../extensibility/creating-and-managing-modal-dialog-boxes.md).  
  
## Vea también  
 [Crear una extensión con una ventana de herramientas](../extensibility/creating-an-extension-with-a-tool-window.md)