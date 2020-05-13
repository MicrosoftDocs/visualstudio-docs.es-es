---
title: Objetos de contexto de selección ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e4f33dd0168a667b8f266ea606cecf0c26d62f1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705510"
---
# <a name="selection-context-objects"></a>Objetos de contexto de selección
El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno de desarrollo integrado (IDE) utiliza un objeto de contexto de selección global para determinar lo que se debe mostrar en el IDE. Cada ventana del IDE puede tener su propio objeto de contexto de selección insertado en el contexto de selección global. El IDE actualiza el contexto de selección global con valores de una ventana cuando esa ventana tiene el foco. Para obtener más información, consulte [Comentarios al usuario](../../extensibility/internals/feedback-to-the-user.md).

 Cada marco de ventana o sitio del <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>IDE tiene un servicio llamado . El objeto creado por el VSPackage que se encuentra `QueryService` en el marco <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> de ventana debe llamar al método para obtener un puntero a la interfaz.

 Las ventanas de marco pueden evitar que partes de su información de contexto de selección se propaguen al contexto de selección global cuando se inician. Esta capacidad es útil para las ventanas de herramientas que pueden tener que comenzar con una selección vacía.

 Modificar el contexto de selección global desencadena eventos que VSPackages pueden supervisar. VSPackages puede realizar las `IVsTrackSelectionEx` siguientes <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> tareas mediante la implementación e interfaces:

- Actualice el archivo activo actualmente en una jerarquía.

- Supervise los cambios en determinados tipos de elementos. Por ejemplo, si el VSPackage usa una ventana **propiedades** especiales, puede supervisar los cambios en la ventana **Propiedades** activa y reiniciar la suya cuando sea necesario.

  La siguiente secuencia muestra el curso típico de seguimiento de selección.

1. El IDE recupera el contexto de selección de la ventana recién abierta y lo coloca en el contexto de selección global. Si el contexto de selección utiliza HIERARCHY_DONTPROPAGATE o SELCONTAINER_DONTPROPAGATE, esa información no se propaga al contexto global. Para obtener más información, consulte [Comentarios al usuario](../../extensibility/internals/feedback-to-the-user.md).

2. Los eventos de notificación se transmiten a cualquier VSPackage que los haya solicitado.

3. El VSPackage actúa en los eventos que recibe mediante la realización de actividades como actualizar una jerarquía, reactivar una herramienta u otras tareas similares.

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>
- [Jerarquías en Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [Selección y moneda en el IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Tipos de proyecto](../../extensibility/internals/project-types.md)
