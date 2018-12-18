---
title: Ampliación y personalización de la herramienta Windows | Microsoft Docs
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
ms.openlocfilehash: c11485e830d1b7bcef851a50225e15f351e64f3e
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39637489"
---
# <a name="extend-and-customize-tool-windows"></a>Ampliar y personalizar las ventanas de herramientas
Visual Studio proporciona varios tipos diferentes de windows, por ejemplo las ventanas de herramientas, ventanas de documento y ventanas de diálogo. Otras ventanas, como el **propiedades** ventana, el **salida** ventana y el **lista de tareas** ventana, son tipos de ventanas de herramientas.  
  
## <a name="tool-windows"></a>Ventanas de herramientas  
 Ventanas de herramientas de Visual Studio son ventanas normalmente de solo lectura que no están basados en archivos. En esto se diferencian de las ventanas de documento, que muestran archivos en modo de lectura y escritura. Las ventanas **Cuadro de herramientas**, **Explorador de soluciones**, **Propiedades** y el **Explorador web** son ejemplos de ventanas de herramientas.  
  
 Para obtener información sobre cómo crear una ventana de herramientas simple, consulte [agregar una ventana de herramientas](../extensibility/adding-a-tool-window.md).  
  
 Para registrar una ventana de herramientas con Visual Studio, consulte [registrar una ventana de herramientas](../extensibility/registering-a-tool-window.md).  
  
 Las ventanas de herramientas son de instancia única de forma predeterminada, lo que significa que solo una instancia de la ventana de herramientas puede estar abierta a la vez. Cuando se abre una ventana de herramientas de instancia única, permanece abierta hasta que se cierra el IDE. Cuando se cierra una ventana de herramientas de instancia única, se cambia solo su visibilidad. También puede crear ventanas de herramientas de varias instancias, de forma que varias instancias de la ventana puedan abrir simultáneamente. Consulte [crear una ventana de herramientas de instancias múltiples](../extensibility/creating-a-multi-instance-tool-window.md) para obtener más información.  
  
 Ventanas de herramientas pueden ser *dinámica*, lo que significa que están visibles siempre que se aplica su contexto de interfaz de usuario relacionado. El uso de la visibilidad automática puede reducir la cantidad de ventanas en el IDE. Para obtener más información, consulte [abrir una ventana de herramientas dinámica](../extensibility/opening-a-dynamic-tool-window.md).  
  
 Las ventanas de herramientas se pueden acoplar, ser flotantes o con pestañas en el marco del documento. El IDE proporciona el marco de ventana de herramientas y se usa para controlar el tamaño, la ubicación, el estado de acoplamiento y otras propiedades persistentes. El panel de la ventana de herramientas muestra el contenido. La ubicación y tamaño predeterminados se aplican solo cuando la ventana de herramientas se abre por primera vez; después se guarda el estado de la ventana de herramientas.  
  
 Los paneles de la ventana de herramientas pueden hospedar controles de usuario WPF y admiten barras de herramientas. Puede invalidar el <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> propiedad para devolver el identificador del control hospedado.  
  
 Puede agregar muchas características distintas a las ventanas de herramientas. Por ejemplo, puede agregar una barra de herramientas: [agregar una barra de herramientas a una ventana de herramientas](../extensibility/adding-a-toolbar-to-a-tool-window.md) o un menú contextual: [agregar un menú contextual en una ventana de herramientas](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md). Puede agregar un control de búsqueda que le permite buscar elementos dentro de la ventana de herramientas: [Agregar búsqueda a una ventana de herramientas](../extensibility/adding-search-to-a-tool-window.md).  
  
 Puede suscribirse a eventos de ventana de herramienta: [suscribirse a un evento](../extensibility/subscribing-to-an-event.md).  
  
## <a name="extend-existing-tool-windows"></a>Extender ventanas de herramientas existentes  
 Puede agregar información acerca de la ventana de herramientas a un nuevo **opciones** página y una nueva configuración en el **propiedades** página, escribir en el **lista de tareas** y **salida**  windows. Para obtener más información, consulte [extender las ventanas Propiedades, lista de tareas, resultados y opciones](../extensibility/extending-the-properties-task-list-output-and-options-windows.md) y [extender las ventanas Propiedades, lista de tareas, resultados y opciones](../extensibility/extending-the-properties-task-list-output-and-options-windows.md).  
  
## <a name="modal-dialog-boxes"></a>Cuadros de diálogo modales  
 En una extensión de Visual Studio debe crear cuadros de diálogo modales derivando desde <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName>, que le permite controlar ellos y el resto de la interfaz de usuario. Para obtener más información, consulte [crear y administrar cuadros de diálogo modales](../extensibility/creating-and-managing-modal-dialog-boxes.md).  
  
## <a name="see-also"></a>Vea también  
 [Crear una extensión con una ventana de herramientas](../extensibility/creating-an-extension-with-a-tool-window.md)