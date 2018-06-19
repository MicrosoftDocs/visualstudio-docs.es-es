---
title: Disponibilidad de comandos | Documentos de Microsoft
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 08f6ceb6c57eccf359b4aa23db7d693df3b86453
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128696"
---
# <a name="command-availability"></a>Disponibilidad de los comandos

El contexto de Visual Studio determina qué comandos están disponibles. El contexto puede cambiar en función del proyecto actual, el editor actual, lo paquetes VSPackage que se carga y otros aspectos del entorno de desarrollo integrado (IDE).

## <a name="command-contexts"></a>Contextos de comando

Los siguientes contextos de comando son los más comunes.

-   **IDE** comandos proporcionados por el IDE están siempre disponibles.

-   **VSPackage** VSPackages puede definir cuándo son comandos para mostrar u ocultar.

-   **Proyecto** comandos de proyecto solo aparecen para el proyecto seleccionado actualmente.

-   **Editor de** solo editor puede estar activo simultáneamente. Existen comandos desde el editor activo. Un editor trabaja en estrecha colaboración con un servicio de lenguaje. El servicio de lenguaje debe procesar sus comandos en el contexto del editor asociado.

-   **Tipo de archivo** un editor puede cargar más de un tipo de archivo. Pueden cambiar los comandos disponibles según el tipo de archivo.

-   **Ventana activa** la última ventana de documento activo, Establece el contexto de la interfaz de usuario para los enlaces de teclado. Sin embargo, una ventana de herramientas que tiene una tabla de enlace de teclado similar del explorador Web interno también puede establecer el contexto de la interfaz de usuario. Ventanas de documento con múltiples fichas como el editor HTML, cada pestaña tiene un contexto de otro comando GUID. Cuando se registre una ventana de herramientas, siempre está disponible en la **vista** menú.

-   **Contexto de la interfaz de usuario** contextos de interfaz de usuario se identifican mediante los valores de la <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> de la clase, por ejemplo, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> al que se va a generar la solución, o <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> cuando el depurador está activo. Varios contextos de interfaz de usuario pueden activos al mismo tiempo.

## <a name="defining-custom-context-guids"></a>Definir los GUID de contexto personalizado

Si un contexto de comando adecuado que GUID no se ha definido, puede definir uno en el paquete de VS y, a continuación, programarlo para ser activos o inactivos según sea necesario para controlar la visibilidad de los comandos.

1.  Registrar los GUID de contexto mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> método.

2.  Obtener el estado de un GUID de contexto mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> método.

3.  Active o desactive los GUID de contexto mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> método.

    > [!CAUTION]
    > Asegúrese de que el VSPackage no afecta a ningún contexto existente GUID porque otros VSPackages pueden depender de ellas.

## <a name="see-also"></a>Vea también

- [Objetos de contexto de selección](../../extensibility/internals/selection-context-objects.md)
- [Adición de elementos de la interfaz de usuario por VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)