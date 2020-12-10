---
title: Extender y personalizar ventanas de herramientas | Microsoft Docs
description: Obtenga información sobre cómo extender y personalizar las ventanas de herramientas que proporciona Visual Studio, incluidos los ventana Propiedades, la ventana de salida y la ventana de Lista de tareas.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: ca7f6aa0c029cd3d85ba569aa93d6ae2087afd52
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995868"
---
# <a name="extend-and-customize-tool-windows"></a>Extender y personalizar ventanas de herramientas
Visual Studio proporciona varios tipos diferentes de ventanas, por ejemplo, ventanas de herramientas, ventanas de documentos y ventanas de cuadro de diálogo. Otras ventanas, como la ventana **propiedades** , la ventana **resultados** y la ventana **lista de tareas** , son tipos de ventanas de herramientas.

## <a name="tool-windows"></a>Ventanas de herramientas
 Las ventanas de herramientas de Visual Studio suelen ser ventanas de solo lectura que no están basadas en archivos. En esto se diferencian de las ventanas de documento, que muestran archivos en modo de lectura y escritura. Las ventanas **Cuadro de herramientas**, **Explorador de soluciones**, **Propiedades** y el **Explorador web** son ejemplos de ventanas de herramientas.

 Para obtener información sobre cómo crear una ventana de herramientas simple, vea [Agregar una ventana de herramientas](../extensibility/adding-a-tool-window.md).

 Para registrar una ventana de herramientas con Visual Studio, consulte [registrar una ventana de herramientas](../extensibility/registering-a-tool-window.md).

 Las ventanas de herramientas son de instancia única de forma predeterminada, lo que significa que solo una instancia de la ventana de herramientas puede estar abierta a la vez. Cuando se abre una ventana de herramientas de instancia única, permanece abierta hasta que se cierra el IDE. Al cerrar una ventana de herramientas de una sola instancia, solo cambia la visibilidad. También puede crear ventanas de herramientas de varias instancias, de forma que varias instancias de la ventana puedan abrir simultáneamente. Para obtener más información [, consulte crear una ventana de herramientas de varias instancias](../extensibility/creating-a-multi-instance-tool-window.md) .

 Las ventanas de herramientas pueden ser *dinámicas*, lo que significa que están visibles cada vez que se aplica su contexto de interfaz de usuario relacionado. El uso de la visibilidad automática puede reducir la cantidad de ventanas en el IDE. Para obtener más información, consulte [abrir una ventana de herramientas dinámica](../extensibility/opening-a-dynamic-tool-window.md).

 Las ventanas de herramientas se pueden acoplar, ser flotantes o con pestañas en el marco del documento. El IDE proporciona el marco de ventana de herramientas y se usa para controlar el tamaño, la ubicación, el estado de acoplamiento y otras propiedades persistentes. El panel de la ventana de herramientas muestra el contenido. La ubicación y tamaño predeterminados se aplican solo cuando la ventana de herramientas se abre por primera vez; después se guarda el estado de la ventana de herramientas.

 Los paneles de la ventana de herramientas pueden hospedar controles de usuario WPF y admiten barras de herramientas. Puede invalidar la propiedad <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> para devolver el identificador del control hospedado.

 Puede Agregar muchas características diferentes a las ventanas de herramientas. Por ejemplo, puede Agregar una barra de herramientas: [Agregar una barra de herramientas a una ventana de herramientas](../extensibility/adding-a-toolbar-to-a-tool-window.md) o un menú contextual: [Agregar un menú contextual en una ventana de herramientas](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md). Puede Agregar un control de búsqueda que le permita buscar elementos dentro de la ventana de herramientas: [Agregar búsqueda a una ventana de herramientas](../extensibility/adding-search-to-a-tool-window.md).

 Puede suscribirse a eventos de la ventana de herramientas: [suscribirse a un evento](../extensibility/subscribing-to-an-event.md).

## <a name="extend-existing-tool-windows"></a>Extender las ventanas de herramientas existentes
 Puede agregar información sobre la ventana de herramientas a una nueva página de **Opciones** y un nuevo valor en la página de **propiedades** , escribir en las ventanas de **lista de tareas** y de **salida** . Para obtener más información, consulte extensión de las [propiedades, lista de tareas, salida y ventanas de opciones](../extensibility/extending-the-properties-task-list-output-and-options-windows.md).

## <a name="modal-dialog-boxes"></a>Cuadros de diálogo modales
 En una extensión de Visual Studio, debe crear cuadros de diálogo modales derivándolo de <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName> , lo que le permite controlarlos y el resto de la interfaz de usuario. Para obtener más información, vea [crear y administrar cuadros de diálogo modales](../extensibility/creating-and-managing-modal-dialog-boxes.md).

## <a name="see-also"></a>Consulte también
- [Crear una extensión con una ventana de herramientas](../extensibility/creating-an-extension-with-a-tool-window.md)
- [Ampliar proyectos](../extensibility/extending-projects.md)
- [Extender soluciones](../extensibility/extending-solutions.md)
