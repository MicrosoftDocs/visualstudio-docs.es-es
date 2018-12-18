---
title: Ampliación y personalización de la herramienta Windows | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- user interfaces, essentials
- tool windows, standard
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7aac774f64d79d2d28cc690550abb7a84b7d3674
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51778753"
---
# <a name="extending-and-customizing-tool-windows"></a>Ampliación y personalización de ventanas de herramientas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio proporciona varios tipos diferentes de windows, por ejemplo las ventanas de herramientas, ventanas de documento y ventanas de diálogo. Otras ventanas como la ventana Propiedades, la ventana de salida y la ventana Lista de tareas, son tipos de ventanas de herramientas.  
  
## <a name="tool-windows"></a>Ventanas de herramientas  
 Ventanas de herramientas de Visual Studio son ventanas normalmente de solo lectura que no están basados en archivos. En esto se diferencian de las ventanas de documento, que muestran archivos en modo de lectura y escritura. Las ventanas **Cuadro de herramientas**, **Explorador de soluciones**, **Propiedades** y el **Explorador web** son ejemplos de ventanas de herramientas.  
  
 Para obtener información sobre cómo crear una ventana de herramientas simple, consulte [adición de una ventana de herramientas](../extensibility/adding-a-tool-window.md).  
  
 Para registrar una ventana de herramientas con Visual Studio, consulte [registrando una ventana de herramientas](../extensibility/registering-a-tool-window.md).  
  
 Las ventanas de herramientas son de instancia única de forma predeterminada, lo que significa que solo una instancia de la ventana de herramientas puede estar abierta a la vez. Cuando se abre una ventana de herramientas de instancia única, permanece abierta hasta que se cierra el IDE. Cuando se cierra una ventana de herramientas de instancia única, se cambia solo su visibilidad. También puede crear ventanas de herramientas de varias instancias, de forma que varias instancias de la ventana puedan abrir simultáneamente. Consulte [creación de una ventana de herramientas de instancias múltiples](../extensibility/creating-a-multi-instance-tool-window.md) para obtener más información.  
  
 Ventanas de herramientas pueden ser *dinámica*, lo que significa que están visibles siempre que se aplica su contexto de interfaz de usuario relacionado. El uso de la visibilidad automática puede reducir la cantidad de ventanas en el IDE. Para obtener más información, consulte [abriendo una ventana de herramientas dinámica](../extensibility/opening-a-dynamic-tool-window.md).  
  
 Las ventanas de herramientas se pueden acoplar, ser flotantes o con pestañas en el marco del documento. El IDE proporciona el marco de ventana de herramientas y se usa para controlar el tamaño, la ubicación, el estado de acoplamiento y otras propiedades persistentes. El panel de la ventana de herramientas muestra el contenido. La ubicación y tamaño predeterminados se aplican solo cuando la ventana de herramientas se abre por primera vez; después se guarda el estado de la ventana de herramientas.  
  
 Los paneles de la ventana de herramientas pueden hospedar controles de usuario WPF y admiten barras de herramientas. Puede invalidar la propiedad <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> para devolver el identificador del control hospedado.  
  
 Puede agregar muchas características distintas a las ventanas de herramientas. Por ejemplo, puede agregar una barra de herramientas: [agregar una barra de herramientas a una ventana de herramientas](../extensibility/adding-a-toolbar-to-a-tool-window.md) o un menú contextual: [adición de un menú contextual en una ventana de herramientas](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md). Puede agregar un control de búsqueda que le permite buscar elementos dentro de la ventana de herramientas: [adición de búsqueda a una ventana de herramientas](../extensibility/adding-search-to-a-tool-window.md).  
  
 Puede suscribirse a eventos de ventana de herramienta: [suscripción a un evento](../extensibility/subscribing-to-an-event.md).  
  
## <a name="extending-existing-tool-windows"></a>Ampliación de Windows existentes de herramienta  
 Puede agregar información acerca de la ventana de herramientas a un nuevo **opciones** página y una nueva configuración en el **propiedades** página, escribir en el **lista de tareas** y **salida**  windows. Para obtener más información, consulte [extender las propiedades, lista de tareas, salida y las opciones de Windows](../extensibility/extending-the-properties-task-list-output-and-options-windows.md) y [extender las propiedades, lista de tareas, salida y las opciones de Windows](../extensibility/extending-the-properties-task-list-output-and-options-windows.md).  
  
## <a name="modal-dialog-boxes"></a>Cuadros de diálogo modales  
 En una extensión de Visual Studio debe crear cuadros de diálogo modales derivando desde <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName>, que le permite controlar ellos y el resto de la interfaz de usuario. Para más información, consulte . [Creación y administración de cuadros de diálogo modales](../extensibility/creating-and-managing-modal-dialog-boxes.md).  
  
## <a name="see-also"></a>Vea también  
 [Creación de una extensión con una ventana de herramientas](../extensibility/creating-an-extension-with-a-tool-window.md)

