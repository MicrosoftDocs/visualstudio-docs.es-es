---
title: Campos e interfaces de la ventana Propiedades | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b58314d64536ecf33cc5589609ee5524a9352629
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65700823"
---
# <a name="properties-window-fields-and-interfaces"></a>Interfaces y campos de la ventana Propiedades
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

El modelo de selección para determinar qué información se muestra en la ventana **propiedades** se basa en la ventana que tiene el foco en el IDE. Todas las ventanas y objetos de la ventana seleccionada pueden hacer que su objeto de contexto de selección se inserte en el contexto de selección global. El entorno actualiza el contexto de selección global con los valores de un marco de ventana cuando la ventana tiene el foco. Cuando el foco cambia, también lo hace el contexto de selección.  
  
## <a name="tracking-selection-in-the-ide"></a>Seguimiento de la selección en el IDE  
 El marco de ventana o el sitio, propiedad del IDE, tiene un servicio denominado <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> . En los pasos siguientes se muestra cómo un cambio en una selección, causado por el usuario, ya sea cambiando el foco a otra ventana abierta o seleccionando un elemento de proyecto diferente en **Explorador de soluciones**, se implementa para cambiar el contenido que se muestra en la ventana **propiedades** .  
  
1. El objeto creado por el VSPackage que se encuentra en la ventana seleccionada llama <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> a para que se <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> invoque <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> .  
  
2. El contenedor de selección, proporcionado por la ventana seleccionada, crea su propio <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> objeto. Cuando la selección cambia, el VSPackage llama <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> a para notificar a cualquier agente de escucha en el entorno, incluida la ventana **propiedades** , del cambio. También proporciona acceso a la información de la jerarquía y los elementos relacionados con la nueva selección.  
  
3. Al llamar a <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> y pasarle los elementos de la jerarquía seleccionada en el parámetro, se `VSHPROPID_BrowseObject` rellena el <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> objeto.  
  
4. Un objeto derivado de la [interfaz IDispatch](https://msdn.microsoft.com/ebbff4bc-36b2-4861-9efa-ffa45e013eb5) se devuelve para <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> para el elemento solicitado y el entorno lo ajusta en un <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (vea el paso siguiente). Si se produce un error en la llamada, el entorno realiza una segunda llamada a `IVsHierarchy::GetProperty` , pasándole el contenedor de selección <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> proporcionado por el elemento o elementos de la jerarquía.  
  
    El VSPackage del proyecto no crea <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> porque el VSPackage de ventana proporcionado por el entorno que lo implementa (por ejemplo, **Explorador de soluciones**) se construye <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> en su nombre.  
  
5. El entorno invoca los métodos de <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> para obtener los objetos en función de la `IDispatch` interfaz que se va a rellenar en la ventana **propiedades** .  
  
   Cuando se cambia un valor en la ventana **propiedades** , los VSPackages implementan `IVsTrackSelectionEx::OnElementValueChangeEx` y `IVsTrackSelectionEx::OnSelectionChangeEx` para notificar el cambio en el valor del elemento. A continuación, el entorno invoca <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> o <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> para mantener la información mostrada en la ventana **propiedades** sincronizada con los valores de propiedad. Para obtener más información, vea [actualizar valores de propiedad en la ventana Propiedades](../../misc/updating-property-values-in-the-properties-window.md).  
  
   Además de seleccionar un elemento de proyecto diferente en **Explorador de soluciones** para mostrar las propiedades relacionadas con ese elemento, también puede elegir un objeto diferente en un formulario o una ventana de documento mediante la lista desplegable disponible en la ventana **propiedades** . Para obtener más información, vea [propiedades ventana Lista de objetos](../../extensibility/internals/properties-window-object-list.md).  
  
   Puede cambiar la forma en que se muestra la información en la cuadrícula de la ventana **propiedades** de alfabético a categorías y, si está disponible, también puede abrir una página de propiedades para un objeto seleccionado haciendo clic en los botones adecuados en la ventana **propiedades** . Para obtener más información, consulte botones de la [ventana Propiedades](../../extensibility/internals/properties-window-buttons.md) y [páginas de propiedades](../../extensibility/internals/property-pages.md).  
  
   Por último, la parte inferior de la ventana **propiedades** también contiene una descripción del campo seleccionado en la cuadrícula de la ventana **propiedades** . Para obtener más información, vea [obtener descripciones de campo en la ventana Propiedades](../../misc/getting-field-descriptions-from-the-properties-window.md).  
  
## <a name="see-also"></a>Consulte también  
 [Extensión de propiedades](../../extensibility/internals/extending-properties.md)
