---
title: Extender y personalizar las ventanas de herramientas | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, essentials
- tool windows, standard
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2ef4f656ed7b7ab7facbcfb470fca98327276cce
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129240"
---
# <a name="extending-and-customizing-tool-windows"></a>Extender y personalizar las ventanas de herramientas
Visual Studio proporciona varios tipos distintos de windows, por ejemplo las ventanas de herramientas, ventanas de documento y ventanas de diálogo. Otras ventanas, como la ventana Propiedades y la ventana de salida, la ventana Lista de tareas, son tipos de ventanas de herramientas.  
  
## <a name="tool-windows"></a>Ventanas de herramientas  
 Ventanas de herramientas de Visual Studio son ventanas normalmente de solo lectura que no están basados en archivos. En esto se diferencian de las ventanas de documento, que muestran archivos en modo de lectura y escritura. Las ventanas **Cuadro de herramientas**, **Explorador de soluciones**, **Propiedades** y el **Explorador web** son ejemplos de ventanas de herramientas.  
  
 Para obtener más información sobre cómo crear una ventana de herramientas simple, consulte [agregar una ventana de herramientas](../extensibility/adding-a-tool-window.md).  
  
 Para registrar una ventana de herramientas con Visual Studio, consulte [registrando una ventana de herramientas](../extensibility/registering-a-tool-window.md).  
  
 Las ventanas de herramientas son de instancia única de forma predeterminada, lo que significa que solo una instancia de la ventana de herramientas puede estar abierta a la vez. Cuando se abre una ventana de herramientas de instancia única, permanece abierta hasta que se cierra el IDE. Al cerrar una ventana de herramientas de instancia única, se cambia solo su visibilidad. También puede crear ventanas de herramientas de varias instancias, de forma que varias instancias de la ventana puedan abrir simultáneamente. Vea [crear una ventana de herramientas de varias instancias](../extensibility/creating-a-multi-instance-tool-window.md) para obtener más información.  
  
 Las ventanas de herramientas pueden ser *dinámica*, lo que significa que están visibles siempre que se aplica su contexto relacionado de la interfaz de usuario. El uso de la visibilidad automática puede reducir la cantidad de ventanas en el IDE. Para obtener más información, consulte [abrir una ventana de herramientas dinámicas](../extensibility/opening-a-dynamic-tool-window.md).  
  
 Las ventanas de herramientas se pueden acoplar, ser flotantes o con pestañas en el marco del documento. El IDE proporciona el marco de ventana de herramientas y se usa para controlar el tamaño, la ubicación, el estado de acoplamiento y otras propiedades persistentes. El panel de la ventana de herramientas muestra el contenido. La ubicación y tamaño predeterminados se aplican solo cuando la ventana de herramientas se abre por primera vez; después se guarda el estado de la ventana de herramientas.  
  
 Los paneles de la ventana de herramientas pueden hospedar controles de usuario WPF y admiten barras de herramientas. Puede invalidar el <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> propiedad para devolver el identificador del control hospedado.  
  
 Puede agregar muchas características distintas a las ventanas de herramientas. Por ejemplo, puede agregar una barra de herramientas: [agregar una barra de herramientas a una ventana de herramientas](../extensibility/adding-a-toolbar-to-a-tool-window.md) o un menú contextual: [agregar un menú contextual en una ventana de herramientas](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md). Puede agregar un control de búsqueda que permite buscar elementos dentro de la ventana de herramientas: [Agregar búsqueda en una ventana de herramientas](../extensibility/adding-search-to-a-tool-window.md).  
  
 Puede suscribirse a eventos de ventana de herramientas: [suscripción a un evento](../extensibility/subscribing-to-an-event.md).  
  
## <a name="extending-existing-tool-windows"></a>Extender las ventanas de herramientas existente  
 Puede agregar información acerca de la ventana de herramientas a una nueva **opciones** página y una nueva configuración en el **propiedades** página, escribir en el **lista de tareas** y **salida**  windows. Para obtener más información, consulte [extender propiedades, lista de tareas, salida y opciones de Windows](../extensibility/extending-the-properties-task-list-output-and-options-windows.md) y [extender propiedades, lista de tareas, salida y opciones de Windows](../extensibility/extending-the-properties-task-list-output-and-options-windows.md).  
  
## <a name="modal-dialog-boxes"></a>Cuadros de diálogo modales  
 En una extensión de Visual Studio debe crear cuadros de diálogo modales derivando de <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName>, que le permite controlar ellos y el resto de la interfaz de usuario. Para más información, consulte . [Crear y administrar cuadros de diálogo modales](../extensibility/creating-and-managing-modal-dialog-boxes.md).  
  
## <a name="see-also"></a>Vea también  
 [Creación de una extensión con una ventana de herramientas](../extensibility/creating-an-extension-with-a-tool-window.md)