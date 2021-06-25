---
title: Objetos de contexto de selección | Microsoft Docs
description: Obtenga información sobre los detalles internos de cómo el IDE de Visual Studio usa un objeto de contexto de selección global para determinar lo que se debe mostrar en el IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b0c97108eaba426a4def4c1052d3adc7348eb88b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898492"
---
# <a name="selection-context-objects"></a>Objetos de contexto de selección
El entorno de desarrollo integrado (IDE) usa un objeto de contexto de selección global para determinar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] lo que se debe mostrar en el IDE. Cada ventana del IDE puede tener su propio objeto de contexto de selección pushed en el contexto de selección global. El IDE actualiza el contexto de selección global con valores de una ventana cuando esa ventana tiene el foco. Para obtener más información, vea [Comentarios al usuario.](../../extensibility/internals/feedback-to-the-user.md)

 Cada marco de ventana o sitio del IDE tiene un servicio denominado <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> . El objeto creado por el VSPackage que se encuentra en el marco de ventana debe llamar al método para obtener `QueryService` un puntero a la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> .

 Las ventanas de marco pueden evitar que partes de su información de contexto de selección se propaguen al contexto de selección global cuando se inician. Esta capacidad es útil para las ventanas de herramientas que pueden tener que empezar con una selección vacía.

 Al modificar el contexto de selección global, se desencadenan eventos que los VSPackages pueden supervisar. Los VSPackages pueden realizar las siguientes tareas mediante la implementación de `IVsTrackSelectionEx` <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> interfaces e :

- Actualice el archivo activo actualmente en una jerarquía.

- Supervise los cambios en determinados tipos de elementos. Por ejemplo, si el VSPackage usa una ventana propiedades  especial, puede supervisar los cambios en la ventana Propiedades activas y reiniciar los de cuando sea necesario. 

  En la secuencia siguiente se muestra el curso típico de seguimiento de selección.

1. El IDE recupera el contexto de selección de la ventana recién abierta y lo coloca en el contexto de selección global. Si el contexto de selección usa HIERARCHY_DONTPROPAGATE o SELCONTAINER_DONTPROPAGATE, esa información no se propaga al contexto global. Para obtener más información, vea [Comentarios al usuario.](../../extensibility/internals/feedback-to-the-user.md)

2. Los eventos de notificación se difunden a cualquier VSPackage que los solicite.

3. El VSPackage actúa sobre los eventos que recibe realizando actividades como actualizar una jerarquía, reactivar una herramienta u otras tareas similares.

## <a name="see-also"></a>Consulta también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>
- [Jerarquías en Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [Selección y moneda en el IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Tipos de proyecto](../../extensibility/internals/project-types.md)
