---
title: "Objeto objeto VSTextBuffer | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VSTextBuffer"
helpviewer_keywords: 
  - "Objeto objeto VSTextBuffer, referencia"
  - "vistas [Visual Studio SDK] objeto objeto VSTextBuffer"
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# Objeto objeto VSTextBuffer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El objeto de búfer de texto representa una secuencia de texto Unicode, que suele estar asociado con un archivo. Un <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objeto puede utilizarse fuera del contexto del editor de núcleo, como en el caso de un asistente.  
  
 En la tabla siguiente se muestra las interfaces de `VSTextBuffer`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IOleCommandTarget](http://msdn.microsoft.com/library/windows/desktop/ms683797)|Interfaz estándar de OLE. Se utiliza principalmente para el control en el búfer de deshacer o rehacer.|  
|[IPersistFile](http://msdn.microsoft.com/library/windows/desktop/ms687223)|Interfaz estándar de OLE.|  
|[IPersistStream](http://msdn.microsoft.com/library/windows/desktop/ms690091)|Interfaz estándar de OLE.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Permite la creación de acciones de compuestos \(es decir, las acciones que se agrupan en una unidad de deshacer y rehacer único\).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Habilita la persistencia de datos administrados por el búfer de texto del documento.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Proporciona servicios básicos; utilizado por muchos clientes.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|Se utiliza para buscar un búfer.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Proporciona lectura y escritura capacidades mediante coordenadas bidimensionales. Se hereda de `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Proporciona lectura y escritura capacidades mediante coordenadas unidimensionales. Se hereda de `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Proporciona un rápido, acceso secuencial orientado a secuencias a texto en el búfer.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Proporciona acceso a una colección genérica de propiedades. La propiedad más importante es el nombre o el moniker del búfer. Puede almacenar sus propios datos aleatorios en el búfer con esta interfaz mediante la creación de un GUID y utilizar como clave.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Admite puntos de conexión de eventos.|  
  
## Comentarios  
 El `VSTextBuffer` se encuentra normalmente por un `QueryInterface` llamar en `IVsTextBuffer`. Para obtener más información, consulte [el búfer de texto](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md).  
  
## Vea también  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Figures Edit](http://msdn.microsoft.com/es-es/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)