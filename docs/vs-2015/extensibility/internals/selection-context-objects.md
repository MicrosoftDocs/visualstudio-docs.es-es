---
title: Objetos de contexto de selección | Documentos de Microsoft
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
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: beaf1b9c67cdad3237d1ac48b4a8e464b0a203a7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51769396"
---
# <a name="selection-context-objects"></a>Objetos de contexto de selección
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

El [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] el entorno de desarrollo integrado (IDE) utiliza un objeto de contexto de la selección global para determinar lo que debe mostrarse en el IDE. Cada ventana en el IDE puede tener su propio objeto de contexto de selección insertado en el contexto de selección global. El IDE actualiza el contexto de selección global con los valores de una ventana cuando esa ventana tiene el foco. Para obtener más información, consulte [comentarios al usuario](../../extensibility/internals/feedback-to-the-user.md).  
  
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

