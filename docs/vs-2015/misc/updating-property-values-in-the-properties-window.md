---
title: Actualizar valores de propiedad en la ventana Propiedades | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Properties window, updating property values
- property values, updating in Properties window
ms.assetid: 9358e8c3-b9d2-4fd4-aaab-cf48d1526db4
caps.latest.revision: 9
manager: douge
ms.openlocfilehash: 0272ba348e29fb1a2a118a0ff4b0989a2aa1683f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47575648"
---
# <a name="updating-property-values-in-the-properties-window"></a>Actualizar valores de propiedad en la ventana Propiedades
Existen dos maneras de mantener la ventana **Propiedades** sincronizada con los cambios de valores de propiedad. La primera consiste en llamar a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfaz, que proporciona acceso a la funcionalidad básica de ventanas, incluidos el acceso y la creación de ventanas de herramientas y de documento proporcionado por el entorno. Los pasos siguientes describen este proceso de sincronización.  
  
## <a name="updating-property-values-using-ivsuishell"></a>Actualización de los valores de propiedad mediante IVsUIShell  
  
#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>Para actualizar los valores de propiedad mediante la interfaz IVsUIShell  
  
1.  Llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> (a través de <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> service) cada vez que paquetes VSPackage, proyectos, o editores necesiten crear o enumerar las ventanas de documento o herramienta.  
  
2.  Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> para mantener la **propiedades** ventana sincronizado con los cambios de propiedad para un proyecto (o cualquier otro objeto seleccionado que examina el **propiedades** ventana) sin necesidad de implementar <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> y desencadenando <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> eventos.  
  
3.  Implementar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> métodos <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> para establecer y deshabilitar, respectivamente, la notificación de cliente de eventos de la jerarquía sin necesidad de la jerarquía para implementar <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.  
  
## <a name="updating-property-values-using-iconnection"></a>Actualización de los valores de propiedad mediante IConnection  
 La segunda manera de mantener la ventana **Propiedades** sincronizada con los cambios de valores de propiedad consiste en implementar `IConnection` en el objeto conectable para indicar la existencia de las interfaces de salida. Si desea localizar el nombre de propiedad, derive su objeto de <xref:System.ComponentModel.ICustomTypeDescriptor>. El <xref:System.ComponentModel.ICustomTypeDescriptor> puede modificar los descriptores de propiedad devuelve y cambiar el nombre de una propiedad de implementación. Para localizar la descripción, cree un atributo que se deriva de <xref:System.ComponentModel.DescriptionAttribute> e invalidar la propiedad Description.  
  
#### <a name="considerations-in-implementing-the-iconnection-interface"></a>Consideraciones de la implementación de la interfaz IConnection  
  
1.  `IConnection` proporciona acceso a un subobjeto enumerador con el <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> interfaz. También proporciona acceso a todas las conexiones punto subobjetos, cada uno de los cuales implementa la <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfaz.  
  
2.  Cualquier objeto de búsqueda es responsable de implementar un <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink> eventos. La ventana **Propiedades** aconsejará sobre el evento establecido a través de `IConnection`.  
  
3.  Un punto de conexión controla cuántas conexiones (uno o más) permite en su implementación de <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>. Puede devolver un punto de conexión que permite solo una interfaz <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> desde el <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A> método.  
  
4.  Un cliente puede llamar a la `IConnection` interfaz para obtener acceso a un subobjeto enumerador con el <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> interfaz. El <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> interfaz, a continuación, se puede llamar para enumerar los puntos de conexión para cada identificador (IID) de la interfaz de salida.  
  
5.  `IConnection` También se puede llamar para obtener acceso a los objetos secundarios de punto de conexión con el <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfaz para cada IID saliente. A través de la <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfaz, un cliente se inicia o finaliza un bucle de asesoría con el objeto conectable y la sincronización del cliente. El cliente también puede llamar a la <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfaz para obtener un objeto enumerador con el <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> interfaz para enumerar las conexiones que conoce.  
  
## <a name="see-also"></a>Vea también  
 [Presentación de seguimiento de selección de ventana de propiedades](../misc/announcing-property-window-selection-tracking.md)   
 [Extensión de propiedades](../extensibility/internals/extending-properties.md)