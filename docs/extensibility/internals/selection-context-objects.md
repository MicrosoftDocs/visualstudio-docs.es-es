---
title: "Objetos de contexto de selección | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d97dd10661beb5acb28b464a8bc0d88ba5946924
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="selection-context-objects"></a>Objetos de contexto de selección
El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el entorno de desarrollo integrado (IDE) utiliza un objeto de contexto de selección global para determinar lo que debe mostrarse en el IDE. Cada ventana en el IDE puede tener su propio objeto de contexto de selección insertado en el contexto de selección global. El IDE actualiza el contexto de selección global con los valores de una ventana cuando esa ventana tiene el foco. Para obtener más información, consulte [comentarios al usuario](../../extensibility/internals/feedback-to-the-user.md).  
  
 Cada marco de ventana o el sitio en el IDE tiene un servicio denominado <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>. El objeto creado por el VSPackage que se ubica en el marco de ventana debe llamar a la `QueryService` método para obtener un puntero a la <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> interfaz.  
  
 Ventanas de marco pueden mantener las partes de su información de contexto de selección se propague en el contexto de selección global cuando se inician. Esta capacidad es útil para las ventanas de herramientas que se tienen que iniciar con una selección vacía.  
  
 Modificación de los eventos de desencadenadores de contexto de selección global que puede supervisar VSPackages. VSPackages puede realizar las siguientes tareas mediante la implementación `IVsTrackSelectionEx` y <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> interfaces:  
  
-   Actualice el archivo activo actualmente en una jerarquía.  
  
-   Supervisar los cambios a ciertos tipos de elementos. Por ejemplo, si el paquete de VS utiliza una clase especial **propiedades** ventana, puede supervisar los cambios en el activo **propiedades** ventana y reinicie suyo cuando sea necesario.  
  
 La secuencia siguiente muestra el curso normal de seguimiento de selección.  
  
1.  El IDE recupera el contexto de selección de la ventana recién abierta y lo coloca en el contexto de selección global. Si el contexto de selección usa HIERARCHY_DONTPROPAGATE o SELCONTAINER_DONTPROPAGATE, esa información no se propaga al contexto global. Para obtener más información, consulte [comentarios al usuario](../../extensibility/internals/feedback-to-the-user.md).  
  
2.  Eventos de notificación se difunden a cualquier VSPackage que solicitaron.  
  
3.  El VSPackage actúa en los eventos que recibe mediante la realización de actividades, como la actualización de una jerarquía, reactivar una herramienta u otras tareas similares.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>   
 [Jerarquías en Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Selección y moneda en el IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Tipos de proyecto](../../extensibility/internals/project-types.md)