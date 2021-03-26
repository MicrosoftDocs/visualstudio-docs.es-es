---
title: Objetos de contexto de selección | Microsoft Docs
description: Obtenga información sobre cómo el IDE de Visual Studio usa un objeto de contexto de selección global para determinar lo que se debe mostrar en el IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ca6239264ca1fa42edb0b73e8a96f523cb450857
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080845"
---
# <a name="selection-context-objects"></a>Objetos de contexto de selección
El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno de desarrollo integrado (IDE) utiliza un objeto de contexto de selección global para determinar lo que se debe mostrar en el IDE. Cada ventana del IDE puede tener su propio objeto de contexto de selección insertado en el contexto de selección global. El IDE actualiza el contexto de selección global con los valores de una ventana cuando esa ventana tiene el foco. Para obtener más información, vea [comentarios para el usuario](../../extensibility/internals/feedback-to-the-user.md).

 Cada marco de ventana o sitio del IDE tiene un servicio denominado <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> . El objeto creado por el VSPackage que se encuentra en el marco de la ventana debe llamar al `QueryService` método para obtener un puntero a la <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> interfaz.

 Las ventanas de marco pueden impedir que partes de la información de contexto de selección se propaguen al contexto de selección global cuando se inician. Esta capacidad es útil para las ventanas de herramientas que pueden tener que empezar con una selección vacía.

 La modificación del contexto de selección global desencadena eventos que los VSPackages pueden supervisar. Los VSPackages pueden realizar las siguientes tareas mediante la implementación `IVsTrackSelectionEx` de las <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> interfaces e:

- Actualice el archivo activo actualmente en una jerarquía.

- Supervise los cambios en determinados tipos de elementos. Por ejemplo, si el VSPackage usa una ventana **propiedades** especiales, puede supervisar los cambios en la ventana **propiedades** activas y reiniciar el suyo cuando sea necesario.

  La secuencia siguiente muestra el curso típico del seguimiento de la selección.

1. El IDE recupera el contexto de selección de la ventana recién abierta y lo coloca en el contexto de selección global. Si el contexto de selección usa HIERARCHY_DONTPROPAGATE o SELCONTAINER_DONTPROPAGATE, esa información no se propaga al contexto global. Para obtener más información, vea [comentarios para el usuario](../../extensibility/internals/feedback-to-the-user.md).

2. Los eventos de notificación se difunden a cualquier VSPackage que los solicitó.

3. El VSPackage actúa sobre los eventos que recibe realizando actividades como la actualización de una jerarquía, la reactivación de una herramienta u otras tareas similares.

## <a name="see-also"></a>Consulte también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>
- [Jerarquías en Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [Selección y moneda en el IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Tipos de proyecto](../../extensibility/internals/project-types.md)
