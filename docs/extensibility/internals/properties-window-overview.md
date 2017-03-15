---
title: "Informaci&#243;n general sobre la ventana Propiedades | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Propiedades (ventana)"
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Informaci&#243;n general sobre la ventana Propiedades
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La ventana de **Propiedades** se utiliza para mostrar las propiedades de los objetos seleccionados en los dos tipos principales de ventanas disponibles en el entorno de desarrollo integrado de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \(IDE\).  estos dos tipos de ventanas son:  
  
-   Ventanas de herramientas como el explorador de soluciones, vista de clases, y el examinador de objetos  
  
-   Ventanas de documento que contienen los editores y diseñadores como el diseñador de formularios, el editor XML, y el editor HTML  
  
## Mediante la ventana Propiedades  
 La ventana de **Propiedades** muestra las propiedades de elementos seleccionados sencillos o múltiples.  Si varios elementos son seleccionado, la intersección de todas las propiedades de todos los objetos seleccionados se muestra.  
  
 Los eventos relacionados con un objeto seleccionado dentro de una ventana o un editor HTML de diseño de formularios mediante metadatos de COM\+ se muestran en la ventana de **Propiedades** .  Por ejemplo, puede seleccionar un botón y mostrar sus eventos asociadas, como un evento de `OnClick` , que se puede vincular a ese botón.  
  
 Los eventos mostrados en la ventana de **Propiedades** se utilizan principalmente con objetos enlazados al código.  Si edita un formato de archivo que no tiene nada que ver con código, no va a tener ningún eventos.  Los eventos se muestran solo en la ventana de **Propiedades** cuando hay un enlace entre el código en ejecución y ciertos eventos asociado a los objetos específicos.  Un ejemplo de esto sería código detrás de un objeto seleccionado que se ejecuta cuando se produce ese objeto.  
  
 La tabla siguiente se muestran las interfaces primarias utilizadas por la ventana de **Propiedades** .  
  
|nombre de la interfaz|Descripción|  
|---------------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|proporciona una lista de categorías a la ventana de **Propiedades** y asigna cada propiedad a una categoría.|  
|[Interfaz IDispatch](http://msdn.microsoft.com/es-es/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)|Expone los métodos y las propiedades de un objeto en las herramientas de programación y otras aplicaciones que automatización admiten.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|Proporciona los botones de puntos suspensivos \(...\) denominados *builders* que las ventanas modal abierto de diálogo implementados por el propio objeto.  Se utiliza cuando un valor fácilmente no está escrito por el usuario en un campo de texto.  Por ejemplo, puede ser utilizado para abrir un selector de colores que determina el valor RGB automáticamente.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|Proporciona acceso a los objetos utilizados a información actualizada mostrada en la ventana de **Propiedades** .  <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> se implementa mediante VSPackages para cada ventana que contiene objetos seleccionables con propiedades relacionadas que se mostrarán.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|Proporciona información sobre el tipo de un objeto como métodos de una interfaz y campos de una estructura.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|Permisos VSPackages para recibir notificación de los eventos de selección y recuperar la información sobre la jerarquía de proyecto, el elemento, el valor del elemento, y el contexto actual de la interfaz de usuario de comandos.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|proporciona el entorno con el acceso a las selecciones múltiples.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|Se utiliza para proporcionar adaptadas nombres en algunas propiedades mostradas en la ventana de **Propiedades** .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|Notifies registró VSPackages de cambios en la selección, el valor del elemento, o al contexto de la interfaz de usuario de comandos.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|Notifica al entorno de un cambio en la selección actual y proporciona acceso a la jerarquía y la información sobre el elemento relacionado con la nueva selección.|  
  
 Para obtener más información sobre `IDispatch`, vea la biblioteca de MSDN.  
  
## Vea también  
 [Extender propiedades](../../extensibility/internals/extending-properties.md)   
 [Interfaces y campos de la ventana de propiedades](../../extensibility/internals/properties-window-fields-and-interfaces.md)