---
title: "DEBUG_CUSTOM_VIEWER | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DEBUG_CUSTOM_VIEWER"
helpviewer_keywords: 
  - "Estructura DEBUG_CUSTOM_VIEWER"
ms.assetid: 8e0ef3f0-0107-48e8-a037-6e52b4c4ed9d
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# DEBUG_CUSTOM_VIEWER
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Una estructura que identifica un visualizador personalizado de visor o tipo.  
  
## Sintaxis  
  
```cpp  
typedef struct tagDEBUG_CUSTOM_VIEWER {  
   DWORD dwID;  
   BSTR  bstrMenuName;  
   BSTR  bstrDescription;  
   GUID  guidLang;  
   GUID  guidVendor;  
   BSTR  bstrMetric;  
} DEBUG_CUSTOM_VIEWER;  
```  
  
```c#  
public struct DEBUG_CUSTOM_VIEWER {  
   public uint   dwID;  
   public string bstrMenuName;  
   public string bstrDescription;  
   public Guid   guidLang;  
   public Guid   guidVendor;  
   public string bstrMetric;  
};  
```  
  
## Members  
 dwID  
 Un identificador para distinguir los visores o los visualizadores varias implementados por un `GUID`.  
  
 bstrMenuName  
 el texto que aparecerá en el menú desplegable.  
  
 bstrDescription  
 Una descripción del visor personalizado o del visualizador tipo \(debe ser un valor NULL si no usa\).  
  
 guidLang  
 Lenguaje del evaluador de expresiones que proporciona.  
  
 guidVendor  
 Proveedor del evaluador de expresiones que proporciona.  
  
 bstrMetric  
 Inferior métrica que el visor personalizado o el visualizador tipo `CLSID` se almacena.  
  
## Comentarios  
 Una lista de esta estructura es devuelta por una llamada al método de [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) \(y, por extensión, el método de [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) \).  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)