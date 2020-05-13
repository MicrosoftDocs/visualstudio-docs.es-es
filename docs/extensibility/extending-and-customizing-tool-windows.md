---
title: Ampliación y personalización de las ventanas de herramientas de la herramienta de la herramienta de la herramienta Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, essentials
- tool windows, standard
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 76c094ec73a69baa46a5e8313dd26febd57e5887
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711814"
---
# <a name="extend-and-customize-tool-windows"></a>Ampliar y personalizar las ventanas de herramientas
Visual Studio proporciona varios tipos diferentes de ventanas, por ejemplo, ventanas de herramientas, ventanas de documento y ventanas de cuadro de diálogo. Otras ventanas, como la ventana **Propiedades,** la ventana **Salida** y la ventana **Lista** de tareas, son tipos de ventanas de herramientas.

## <a name="tool-windows"></a>Ventanas de herramientas
 Las ventanas de herramientas de Visual Studio suelen ser ventanas de solo lectura que no están basadas en archivos. En esto se diferencian de las ventanas de documento, que muestran archivos en modo de lectura y escritura. Las ventanas **Cuadro de herramientas**, **Explorador de soluciones**, **Propiedades** y el **Explorador web** son ejemplos de ventanas de herramientas.

 Para saber cómo crear una ventana de herramientas sencilla, consulte [Agregar una ventana](../extensibility/adding-a-tool-window.md)de herramientas .

 Para registrar una ventana de herramientas con Visual Studio, vea [Registrar una ventana](../extensibility/registering-a-tool-window.md)de herramientas .

 Las ventanas de herramientas son de instancia única de forma predeterminada, lo que significa que solo una instancia de la ventana de herramientas puede estar abierta a la vez. Cuando se abre una ventana de herramientas de instancia única, permanece abierta hasta que se cierra el IDE. Al cerrar una ventana de herramientas de instancia única, solo cambia su visibilidad. También puede crear ventanas de herramientas de varias instancias, de forma que varias instancias de la ventana puedan abrir simultáneamente. Consulte [Crear una ventana de herramientas de varias instancias](../extensibility/creating-a-multi-instance-tool-window.md) para obtener más información.

 Las ventanas de herramientas pueden ser *dinámicas,* lo que significa que son visibles siempre que se aplica su contexto de interfaz de usuario relacionado. El uso de la visibilidad automática puede reducir la cantidad de ventanas en el IDE. Para obtener más información, consulte Abrir una ventana de [herramientas dinámicas](../extensibility/opening-a-dynamic-tool-window.md).

 Las ventanas de herramientas se pueden acoplar, ser flotantes o con pestañas en el marco del documento. El IDE proporciona el marco de ventana de herramientas y se usa para controlar el tamaño, la ubicación, el estado de acoplamiento y otras propiedades persistentes. El panel de la ventana de herramientas muestra el contenido. La ubicación y tamaño predeterminados se aplican solo cuando la ventana de herramientas se abre por primera vez; después se guarda el estado de la ventana de herramientas.

 Los paneles de la ventana de herramientas pueden hospedar controles de usuario WPF y admiten barras de herramientas. Puede invalidar la propiedad <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> para devolver el identificador del control hospedado.

 Puede agregar muchas características diferentes a las ventanas de herramientas. Por ejemplo, puede agregar una barra de herramientas: Agregar una barra de [herramientas a una ventana](../extensibility/adding-a-toolbar-to-a-tool-window.md) de herramientas o un menú contextual: Agregar un menú contextual en una ventana de [herramientas](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md). Puede agregar un control de búsqueda que le permite buscar elementos dentro de la ventana de herramientas: [Agregar búsqueda a una ventana](../extensibility/adding-search-to-a-tool-window.md)de herramientas .

 Puede suscribirse a eventos de ventana de herramientas: [Suscríbase a un evento](../extensibility/subscribing-to-an-event.md).

## <a name="extend-existing-tool-windows"></a>Ampliar las ventanas de herramientas existentes
 Puede agregar información sobre la ventana de herramientas a una nueva página **Opciones** y una nueva configuración en la página **Propiedades,** escribir en las ventanas Lista de **tareas** y **Salida.** Para obtener más información, vea [Extender las ventanas Propiedades, Lista de tareas, Salida y Opciones](../extensibility/extending-the-properties-task-list-output-and-options-windows.md).

## <a name="modal-dialog-boxes"></a>Cuadros de diálogo modales
 En una extensión de Visual Studio debe crear <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName>cuadros de diálogo modales derivando de , lo que le permite controlarlos y el resto de la interfaz de usuario. Para obtener más información, consulte [Crear y administrar cuadros](../extensibility/creating-and-managing-modal-dialog-boxes.md)de diálogo modales .

## <a name="see-also"></a>Vea también
- [Crear una extensión con una ventana de herramientas](../extensibility/creating-an-extension-with-a-tool-window.md)
- [Ampliar proyectos](../extensibility/extending-projects.md)
- [Ampliar las soluciones](../extensibility/extending-solutions.md)
