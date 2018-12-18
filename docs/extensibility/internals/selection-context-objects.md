---
title: Objetos de contexto de selección | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f09bcb260f4edd09045f860ed08d951622e54a5d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49913168"
---
# <a name="selection-context-objects"></a>Objetos de contexto de selección
El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el entorno de desarrollo integrado (IDE) utiliza un objeto de contexto de la selección global para determinar lo que debe mostrarse en el IDE. Cada ventana en el IDE puede tener su propio objeto de contexto de selección insertado en el contexto de selección global. El IDE actualiza el contexto de selección global con los valores de una ventana cuando esa ventana tiene el foco. Para obtener más información, consulte [comentarios al usuario](../../extensibility/internals/feedback-to-the-user.md).  
  
 Cada sitio en el IDE o marco de ventana tiene un servicio denominado <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>. El objeto creado por el VSPackage que está situado en el marco de ventana debe llamar a la `QueryService` método para obtener un puntero a la <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> interfaz.  
  
 Ventanas de marco pueden mantener las partes de su información de contexto de selección se propaguen en el contexto de la selección global cuando se inician. Esta capacidad es útil para ventanas de herramientas que pueden comenzar con una selección vacía.  
  
 Modificar la selección global contexto desencadena eventos que pueden supervisar los paquetes VSPackage. Los paquetes VSPackage pueden realizar las siguientes tareas mediante la implementación `IVsTrackSelectionEx` y <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> interfaces:  
  
- Actualice el archivo activo en una jerarquía.  
  
- Supervisar los cambios en determinados tipos de elementos. Por ejemplo, si el paquete VSPackage usa un especial **propiedades** ventana, puede supervisar los cambios en el activo **propiedades** ventana y reinicie suyo cuando sea necesario.  
  
  La secuencia siguiente muestra el curso normal de seguimiento de selección.  
  
1.  El IDE recupera el contexto de selección de la ventana recién abierta y lo coloca en el contexto de la selección global. Si el contexto de selección usa HIERARCHY_DONTPROPAGATE o SELCONTAINER_DONTPROPAGATE, no se propaga esa información en el contexto global. Para obtener más información, consulte [comentarios al usuario](../../extensibility/internals/feedback-to-the-user.md).  
  
2.  Eventos de notificación se difunden a cualquier VSPackage que solicita a ellos.  
  
3.  El VSPackage que actúe en los eventos que recibe mediante la realización de actividades, como la actualización de una jerarquía, reactivación de una herramienta u otras tareas similares.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>   
 [Jerarquías en Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Selección y moneda en el IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Tipos de proyecto](../../extensibility/internals/project-types.md)