---
title: Información general sobre la ventana de propiedades | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e255795a52064723477eda4e1aca532adedb6be1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131625"
---
# <a name="properties-window-overview"></a>Información general sobre la ventana Propiedades
El **propiedades** ventana se usa para mostrar las propiedades de objetos seleccionados en los dos tipos principales de windows disponibles en la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el entorno de desarrollo integrado (IDE). Estos dos tipos de windows son:  
  
-   Ventanas de herramientas como el Explorador de soluciones, vista de clases y objetos de explorador  
  
-   Ventanas de documento que contiene estos editores y diseñadores, como el Diseñador de formularios, el editor XML y el editor de HTML  
  
## <a name="using-the-properties-window"></a>Mediante la ventana Propiedades  
 El **propiedades** ventana muestra las propiedades de uno o varios elementos seleccionados. Si se seleccionan varios elementos, se muestra la intersección de todas las propiedades para todos los objetos seleccionados.  
  
 Eventos relacionados con un objeto seleccionado dentro de una ventana de diseño del formulario o el editor de HTML con los metadatos de COM + se muestran en la **propiedades** ventana. Por ejemplo, puede seleccionar un botón y mostrar sus eventos asociados, como un `OnClick` eventos, que pueden vincularse a ese botón.  
  
 Eventos mostrados en la **propiedades** ventana se utilizan principalmente con objetos que están enlazados al código. Si está editando un formato de archivo que no tiene nada que ver con el código, no va a tener todos los eventos. Solo se muestran los eventos en el **propiedades** ventana cuando hay un enlace entre ejecutar código y determinados eventos asociados a objetos específicos. Un ejemplo de esto sería el código detrás de un objeto seleccionado que se ejecuta cuando ese objeto se activa.  
  
 En la tabla siguiente se enumera las interfaces principales utilizadas por la **propiedades** ventana.  
  
|Nombre de la interfaz|Descripción|  
|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|Proporciona una lista de categorías para la **propiedades** ventana y cada propiedad se asigna a una categoría.|  
|[Interfaz IDispatch](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx)|Expone métodos y propiedades para la programación de herramientas y otras aplicaciones que admiten la automatización de un objeto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|Proporciona botones de puntos suspensivos (...) que se llama *generadores* que abrir ventanas de cuadro de diálogo modal implementadas por el propio objeto. Se utiliza si no tiene el tipo fácilmente un valor por el usuario en un campo de texto. Por ejemplo, podría utilizarse para abrir un selector de color que determina el valor RGB para usted.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|Proporciona acceso a objetos que se utiliza para actualizar la información que se muestra en el **propiedades** ventana. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> se implementa mediante paquetes VSPackage para cada ventana que contiene objetos que pueden seleccionarse con propiedades relacionadas que se mostrarán.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|Proporciona información sobre el tipo de un objeto como métodos de una interfaz y los campos de una estructura.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|Permite VSPackages para recibir la notificación de eventos de selección y recuperar información acerca de la jerarquía del proyecto actual, el elemento, el valor del elemento y el contexto de la interfaz de usuario de comandos.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|Proporciona el entorno que brinda acceso a las selecciones múltiples.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|Usa para proporcionar los nombres traducidos en algunas propiedades que se muestran en la **propiedades** ventana.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|Notifica a VSPackages registrados de los cambios en la selección actual, el valor del elemento o el contexto de la interfaz de usuario de comandos.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|Notifica el entorno de un cambio en la selección actual y proporciona acceso a la información de jerarquía y elementos relacionados con la nueva selección.|  
  
 Para obtener más información sobre `IDispatch`, vea MSDN library.  
  
## <a name="see-also"></a>Vea también  
 [Extender propiedades](../../extensibility/internals/extending-properties.md)   
 [Interfaces y campos de la ventana Propiedades](../../extensibility/internals/properties-window-fields-and-interfaces.md)