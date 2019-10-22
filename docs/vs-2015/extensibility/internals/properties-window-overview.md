---
title: Información general sobre la ventana de propiedades | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fd4be229338d1a09c22b4d81384dc90f0544fa39
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65700741"
---
# <a name="properties-window-overview"></a>Información general sobre la ventana Propiedades
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

El **propiedades** ventana se utiliza para mostrar las propiedades de objetos seleccionados en los dos tipos principales de windows disponibles en el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] el entorno de desarrollo integrado (IDE). Estos dos tipos de windows son:  
  
- Ventanas como explorador de objetos, vista de clases y Explorador de soluciones  
  
- Ventanas de documento que contiene dichos editores y diseñadores como el Diseñador de formularios, el editor XML y el editor HTML  
  
## <a name="using-the-properties-window"></a>Mediante la ventana Propiedades  
 El **propiedades** ventana muestra las propiedades de uno o varios elementos seleccionados. Si se seleccionan varios elementos, se muestra la intersección de todas las propiedades para todos los objetos seleccionados.  
  
 Los eventos relacionados con un objeto seleccionado dentro de una ventana de diseño del formulario o el editor de HTML con los metadatos de COM + se muestran en el **propiedades** ventana. Por ejemplo, puede seleccionar un botón y mostrar los eventos asociados, como un `OnClick` evento, que se puede vincular a ese botón.  
  
 Los eventos que se muestra en el **propiedades** ventana se utilizan principalmente con los objetos que están enlazados al código. Si está editando un formato de archivo que no tiene nada que ver con el código, no va a tener todos los eventos. Solo se muestran los eventos en el **propiedades** ventana cuando hay un enlace entre la ejecución de código y determinados eventos relacionados con objetos específicos. Un ejemplo de esto sería el código detrás de un objeto seleccionado que se ejecuta cuando se activa ese objeto.  
  
 En la tabla siguiente se enumera las interfaces principales utilizadas por la **propiedades** ventana.  
  
|Nombre de la interfaz|Descripción|  
|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|Proporciona una lista de categorías a la **propiedades** ventana y cada propiedad se asigna a una categoría.|  
|[Interfaz IDispatch](https://msdn.microsoft.com/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)|Expone métodos y propiedades a la programación de herramientas y otras aplicaciones que admiten la automatización de un objeto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|Proporciona los botones de puntos suspensivos (...) llamados *generadores* que abrir ventanas de cuadro de diálogo modal implementados por el propio objeto. Se usa cuando un valor no es fácilmente escrito por el usuario en un campo de texto. Por ejemplo, podría utilizarse para abrir un selector de color que determina el valor RGB para usted.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|Proporciona acceso a objetos que se usa para actualizar la información mostrada en el **propiedades** ventana. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> se implementa mediante paquetes VSPackage para cada ventana que contiene objetos seleccionables con las propiedades relacionadas que se mostrará.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|Proporciona información sobre el tipo de un objeto como métodos de una interfaz y los campos de una estructura.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|Habilita a VSPackages para recibir una notificación de eventos de selección y recuperar información acerca de la jerarquía del proyecto actual, elemento, el valor de elemento y el contexto de interfaz de usuario de comandos.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|Proporciona el entorno con acceso a las selecciones múltiples.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|Usar para proporcionar nombres localizados en algunas propiedades mostradas en la **propiedades** ventana.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|Notifica a los VSPackages registrados de los cambios en la selección actual, el valor del elemento o el contexto de interfaz de usuario de comandos.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|Notifica al entorno de un cambio en la selección actual y proporciona acceso a la jerarquía y elemento de información relacionada con la nueva selección.|  
  
 Para obtener más información sobre `IDispatch`, vea MSDN library.  
  
## <a name="see-also"></a>Vea también  
 [Propiedades de extensión](../../extensibility/internals/extending-properties.md)   
 [Interfaces y campos de la ventana Propiedades](../../extensibility/internals/properties-window-fields-and-interfaces.md)
