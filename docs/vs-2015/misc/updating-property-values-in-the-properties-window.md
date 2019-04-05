---
title: Actualizar valores de propiedad en la ventana Propiedades | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- Properties window, updating property values
- property values, updating in Properties window
ms.assetid: 9358e8c3-b9d2-4fd4-aaab-cf48d1526db4
caps.latest.revision: 9
manager: jillfra
ms.openlocfilehash: 2dd12247c7f2af6a7db297defe835e352848b378
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58987776"
---
# <a name="updating-property-values-in-the-properties-window"></a>Actualizar valores de propiedad en la ventana Propiedades
Existen dos maneras de mantener la ventana **Propiedades** sincronizada con los cambios de valores de propiedad. La primera es llamar a la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>, que proporciona acceso a la funcionalidad básica basada en ventanas, incluidos el acceso y la creación de ventanas de documentos y herramientas proporcionadas por el entorno. Los pasos siguientes describen este proceso de sincronización.  
  
## <a name="updating-property-values-using-ivsuishell"></a>Actualización de los valores de propiedad mediante IVsUIShell  
  
#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>Para actualizar los valores de propiedad mediante la interfaz IVsUIShell  
  
1.  Llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> (a través del servicio <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>) cada vez que paquetes VSPackage, proyectos, o editores necesiten crear o enumerar las ventanas de documentos o herramientas.  
  
2.  Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> para mantener la **propiedades** ventana sincronizado con los cambios de propiedad para un proyecto (o cualquier otro objeto seleccionado que examina el **propiedades** ventana) sin necesidad de implementar <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> y desencadenando <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> eventos.  
  
3.  Implemente los métodos de <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> para establecer y deshabilitar, respectivamente, la notificación de cliente de los eventos de jerarquía sin requerir que la jerarquía implemente <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.  
  
## <a name="updating-property-values-using-iconnection"></a>Actualización de los valores de propiedad mediante IConnection  
 La segunda manera de mantener la ventana **Propiedades** sincronizada con los cambios de valores de propiedad consiste en implementar `IConnection` en el objeto conectable para indicar la existencia de las interfaces de salida. Si desea localizar el nombre de propiedad, derive su objeto de <xref:System.ComponentModel.ICustomTypeDescriptor>. La implementación de <xref:System.ComponentModel.ICustomTypeDescriptor> puede modificar los descriptores de propiedad que devuelve y cambiar el nombre de una propiedad. Para localizar la descripción, cree un atributo que se derive de <xref:System.ComponentModel.DescriptionAttribute> e invalide la propiedad Description.  
  
#### <a name="considerations-in-implementing-the-iconnection-interface"></a>Consideraciones de la implementación de la interfaz IConnection  
  
1.  `IConnection` proporciona acceso a un subobjeto enumerador con la interfaz <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>. También proporciona acceso a todos los subobjetos del punto de conexión, cada uno de los cuales implementa la interfaz <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>.  
  
2.  Cualquier objeto de búsqueda es responsable de implementar un evento <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink>. La ventana **Propiedades** aconsejará sobre el evento establecido a través de `IConnection`.  
  
3.  Un punto de conexión controla cuántas conexiones (una o más) permite en su implementación de <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>. Un punto de conexión que permita solo una interfaz puede devolver <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> desde el método <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A>.  
  
4.  Un cliente puede llamar a la interfaz `IConnection` para obtener acceso a un subobjeto enumerador con la interfaz <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>. A continuación, se puede llamar a la interfaz <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> para enumerar los puntos de conexión de cada identificador de interfaz (IID) de salida.  
  
5.  `IConnection` también se puede llamar para obtener acceso a los subobjetos del punto de conexión con la interfaz l <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> para cada IID saliente. A través de la interfaz <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>, un cliente inicia o termina un bucle de asesoría con el objeto conectable y la sincronización del cliente. El cliente también puede llamar a la interfaz <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> para obtener un objeto enumerador con la interfaz <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> para enumerar las conexiones que conoce.  
  
## <a name="see-also"></a>Vea también  
 [Presentación de seguimiento de selección de ventana de propiedades](../misc/announcing-property-window-selection-tracking.md)   
 [Extensión de propiedades](../extensibility/internals/extending-properties.md)