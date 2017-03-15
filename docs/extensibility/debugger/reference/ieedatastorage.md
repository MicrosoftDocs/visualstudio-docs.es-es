---
title: "IEEDataStorage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEEDataStorage"
helpviewer_keywords: 
  - "Interfaz IEEDataStorage"
ms.assetid: 704e932d-2325-410e-89c4-ce88c6ec19da
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IEEDataStorage
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz representa una matriz de bytes.  
  
## Sintaxis  
  
```  
IEEDataStorage : IUnknown  
```  
  
## Notas para los implementadores  
 El evaluador de \(EE\) expresiones implementa esta interfaz para representar una matriz de bytes \(utilizados por los visualizadores escritos para recuperar y modificar datos a través de la interfaz de [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) \).  Aa implementa normalmente esta interfaz para admitir los visualizadores de tipo externo.  
  
## Notas para los llamadores  
 Los métodos de la interfaz de `IPropertyProxyEESide` todos devuelven esta interfaz.  llamada [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) para obtener la interfaz de [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) .  Llame a [QueryInterface](/visual-cpp/atl/queryinterface) en una interfaz de [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) para obtener la interfaz de [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) .  
  
## métodos en el orden de Vtable  
 La interfaz de `IEEDataStorage` implementa los siguientes métodos:  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|recupera el número especificado de bytes de datos a un búfer proporcionado.|  
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|Recupera el número de bytes de datos disponibles.|  
  
## Comentarios  
 Esta interfaz es utilizado por un visualizador de tipo para tener acceso a los datos almacenados por un objeto concreto.  Los datos se trata como una matriz de bytes, permitiendo que el visualizador de tipo lo manipula en se requiere alguna forma de mostrarlos al usuario.  
  
 Un visor personalizado puede utilizar esta interfaz, si se desea, aunque más normalmente, un visor personalizado utiliza una interfaz personalizada, [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) o [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) \(para los datos cadena\-orientados\).  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [Visualizador de tipo y el visor personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)