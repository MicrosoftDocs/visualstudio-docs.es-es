---
title: "Objetos de contexto de selecci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "selección de seguimiento"
  - "selección de objetos de contexto"
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Objetos de contexto de selecci&#243;n
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

El entorno de desarrollo integrado de \(IDE\) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utiliza un objeto global de contexto de selección para determinar qué se debe mostrar en el IDE.  Cada ventana en el IDE puede tener su propio objeto de contexto de selección insertado el contexto global de la selección.  El IDE actualiza el contexto global de selección con valores de una ventana a esa ventana tiene el foco.  Para obtener más información, vea [Comentarios para el usuario](../../extensibility/internals/feedback-to-the-user.md).  
  
 Cada marco de ventana o sitio en el IDE tiene un servicio denominado <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>.  El objeto creado por el Paquete que se encuentra en el marco de ventana debe llamar al método de `QueryService` para obtener un puntero a la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> .  
  
 Las ventanas de capítulos pueden mantener partes de la información de contexto de selección de propagar el contexto global de selección cuando se inician.  Esta capacidad es útil para las ventanas de herramientas que pueden tener que empezar con una selección vacía.  
  
 Modificando el contexto global de selección desencadena eventos que VSPackages puede controlar.  VSPackages puede realizar las siguientes tareas implementando `IVsTrackSelectionEx` y las interfaces de <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> :  
  
-   Actualice actualmente en el archivo activo en una jerarquía.  
  
-   Cambios de Monitor ciertos tipos de elementos.  Por ejemplo, si el Paquete utiliza una ventana especial de **Propiedades** , puede controlar cambios en la ventana activa de **Propiedades** y reiniciar thes cuando sea necesario.  
  
 La secuencia siguiente muestra el curso típico de traza de la selección.  
  
1.  El IDE recupera el contexto de selección de ventana recién abierta y lo pondrá en el contexto global de la selección.  Si el contexto de selección utiliza HIERARCHY\_DONTPROPAGATE o SELCONTAINER\_DONTPROPAGATE, dicha información no se propaga al contexto global.  Para obtener más información, vea [Comentarios para el usuario](../../extensibility/internals/feedback-to-the-user.md).  
  
2.  Eventos de notificación se propagan a cualquier Paquete que los solicitara.  
  
3.  El paquete VSPackage actúa en los eventos que recibe realizando actividades como actualizar una jerarquía, reactivando una herramienta, u otras tareas similares.  
  
## Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>   
 [Jerarquías en Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Selección y moneda en el IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Tipos de proyecto](../../extensibility/internals/project-types.md)