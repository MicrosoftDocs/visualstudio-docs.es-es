---
title: "Interfaces y campos de la ventana de propiedades | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interfaces, campos y ventana Propiedades"
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Interfaces y campos de la ventana de propiedades
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

El modelo para que la selección determina qué información se muestra en la ventana de **Propiedades** se basa en la ventana que tiene el foco en el IDE.  Cada ventana, y el objeto dentro de la ventana seleccionada, puede tener su objeto de contexto de selección insertado el contexto global de la selección.  El entorno actualiza el contexto global de selección con valores de un marco de la ventana cuando esa ventana tiene el foco.  Cuando el foco, hacerlo el contexto de la selección.  
  
## Selección de seguimiento en el IDE  
 El marco de la ventana o en el sitio, propiedad del IDE, tiene un servicio denominado <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>.  Los pasos siguientes muestran cómo un cambio en una selección, producida por el usuario que cambia el foco a otra ventana abierta o activa otro elemento de **Explorador de soluciones**, se implementa para cambiar el contenido mostrado en la ventana de **Propiedades** .  
  
1.  El objeto creado por el Paquete que se encuentra en la ventana seleccionada llama <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> para que <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> invoca <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.  
  
2.  El contenedor de selección, proporcionadas por la ventana seleccionada, crear su propio objeto de <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> .  Cuando cambia la selección, el Paquete llama <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> para notificar a cualquier agente de escucha del entorno, incluidos la ventana de **Propiedades** , de cambio.  También proporciona acceso a la jerarquía y el elemento información relacionada con la nueva selección.  
  
3.  El <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> de llamada y pasarle los elementos seleccionados de la jerarquía en el parámetro de `VSHPROPID_BrowseObject` rellena el objeto de <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> .  
  
4.  Un objeto derivado de [IDispatch Interface](http://msdn.microsoft.com/es-es/ebbff4bc-36b2-4861-9efa-ffa45e013eb5) se devuelve para <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> para el elemento solicitado, y el entorno se ajusta en <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> \(vea el paso siguiente\).  Si se produce un error en la llamada, el entorno realiza una segunda llamada a `IVsHierarchy::GetProperty`, pasándole el contenedor <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> de selección que el elemento o elementos de la jerarquía proporciona.  
  
     El proyecto VSPackage no crea <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> porque la ventana entorno\-proporcionada VSPackage que lo implementa \(por ejemplo, **Explorador de soluciones**\) crea <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> en su nombre.  
  
5.  El entorno invoca los métodos de <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> para obtener objetos basados en la interfaz de `IDispatch` para completar la ventana de **Propiedades** .  
  
 Cuando un valor en la ventana de **Propiedades** cambia, implemente `IVsTrackSelectionEx::OnElementValueChangeEx` y `IVsTrackSelectionEx::OnSelectionChangeEx` de VSPackages para informar del cambio del valor del elemento.  El entorno a continuación invoca <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> o <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> para mantener la información mostrada en la ventana de **Propiedades** sincronizada con los valores de propiedad.  Para obtener más información, vea [Actualizar valores de propiedad en la ventana Propiedades](../../misc/updating-property-values-in-the-properties-window.md).  
  
 Además de seleccionar un elemento diferente de proyecto en **Explorador de soluciones** para mostrar las propiedades relacionadas con el elemento, puede elegir un objeto diferente dentro de un formulario o ventana de documento utilizando la lista desplegable disponible en la ventana de **Propiedades** .  Para obtener más información, vea [Lista de objetos de ventana de propiedades](../../extensibility/internals/properties-window-object-list.md).  
  
 Puede cambiar la manera en que se muestran en la cuadrícula de la ventana de **Propiedades** de alfabético a de categorías, y, si está disponible, también puede abrir una página de propiedades del objeto seleccionado haciendo clic en los botones adecuados en la ventana de **Propiedades** .  Para obtener más información, vea [Botones de la ventana de propiedades](../../extensibility/internals/properties-window-buttons.md) y [Páginas de propiedades](../../extensibility/internals/property-pages.md).  
  
 Finalmente, la parte inferior de la ventana de **Propiedades** también contiene una descripción del campo seleccionado en la cuadrícula de la ventana de **Propiedades** .  Para obtener más información, vea [Obtener descripciones de los campos de la ventana Propiedades](../../misc/getting-field-descriptions-from-the-properties-window.md).  
  
## Vea también  
 [Extender propiedades](../../extensibility/internals/extending-properties.md)