---
title: Campos de la ventana de propiedades e Interfaces | Microsoft Docs
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
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8b9e7705af131bdc8c81b6cbeeac3ed4dda80aa4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51721037"
---
# <a name="properties-window-fields-and-interfaces"></a>Interfaces y campos de la ventana Propiedades
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

El modelo de selección determinar qué información se muestra en el **propiedades** ventana se basa en la ventana que tiene el foco en el IDE. Cada ventana y el objeto dentro de la ventana seleccionada, pueden tener su objeto de contexto de selección insertado en el contexto de selección global. El entorno actualiza el contexto de selección global con los valores de un marco de ventana cuando esa ventana tiene el foco. Cuando el foco cambia, también lo hace el contexto de selección.  
  
## <a name="tracking-selection-in-the-ide"></a>Selección de seguimiento en el IDE  
 El marco de ventana o el sitio, el IDE de la propiedad tiene un servicio denominado <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>. Los pasos siguientes muestran cómo un cambio en una selección, causada por el usuario cambia el foco a otra ventana abierta o seleccionar un elemento de proyecto diferente en **el Explorador de soluciones**, se implementa para cambiar el contenido mostrado en el  **Propiedades** ventana.  
  
1. El objeto creado por el VSPackage que está situado en las llamadas de la ventana seleccionada <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> tener <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> invocar <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.  
  
2. El contenedor de selección, proporcionado por la ventana seleccionada, se crea su propio <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> objeto. Cuando la selección cambia, el VSPackage llama <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> para notificar a los agentes de escucha en el entorno, incluida la **propiedades** ventana del cambio. También proporciona acceso a la jerarquía y elemento de información relacionada con la nueva selección.  
  
3. Una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> y pasándole los elementos de la jerarquía seleccionada en el `VSHPROPID_BrowseObject` parámetro rellena el <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> objeto.  
  
4. Un objeto derivado de la [interfaz IDispatch](http://msdn.microsoft.com/en-us/ebbff4bc-36b2-4861-9efa-ffa45e013eb5) se devuelve para <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> para el elemento solicitado y el entorno lo encapsula en un <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (consulte el paso siguiente). Si se produce un error en la llamada, el entorno hace que una segunda llamada a `IVsHierarchy::GetProperty`, pasándole el contenedor de selección <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> que proporcionen el elemento de la jerarquía o elementos.  
  
    El proyecto de VSPackage no crea <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> porque la ventana proporcionada por el entorno de VSPackage que implemente (por ejemplo, **el Explorador de soluciones**) construye <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> en su nombre.  
  
5. El entorno invoca los métodos de <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> para obtener los objetos según el `IDispatch` interfaz para rellenar el **propiedades** ventana.  
  
   Cuando un valor de la **propiedades** ventana se cambia, los paquetes VSPackage implementar `IVsTrackSelectionEx::OnElementValueChangeEx` y `IVsTrackSelectionEx::OnSelectionChangeEx` para notificar el cambio en el valor del elemento. A continuación, invoca el entorno <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> o <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> para mantener la información mostrada en el **propiedades** ventana sincronizada con los valores de propiedad. Para obtener más información, consulte [actualizar valores de propiedad en la ventana propiedades](../../misc/updating-property-values-in-the-properties-window.md).  
  
   Además de seleccionar otro elemento de proyecto en **el Explorador de soluciones** para mostrar las propiedades relacionadas con ese elemento, también puede elegir un objeto diferente desde dentro de una ventana de documento o de formulario mediante la lista desplegable disponible en el **Propiedades** ventana. Para obtener más información, consulte [lista de objetos de ventana de propiedades](../../extensibility/internals/properties-window-object-list.md).  
  
   Puede cambiar la manera en que se muestra información en el **propiedades** cuadrícula de la ventana de alfabético en categorías, y, si está disponible, también puede abrir una página de propiedades de un objeto seleccionado, haga clic en los botones apropiados en el  **Propiedades** ventana. Para obtener más información, consulte [botones de la ventana propiedades](../../extensibility/internals/properties-window-buttons.md) y [páginas de propiedades](../../extensibility/internals/property-pages.md).  
  
   Por último, la parte inferior de la **propiedades** ventana también contiene una descripción del campo seleccionado en el **propiedades** cuadrícula de la ventana. Para obtener más información, consulte [obtener descripciones de los campos desde la ventana propiedades](../../misc/getting-field-descriptions-from-the-properties-window.md).  
  
## <a name="see-also"></a>Vea también  
 [Extensión de propiedades](../../extensibility/internals/extending-properties.md)

