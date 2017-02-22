---
title: "IDebugEnumField | Microsoft Docs"
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
  - "IDebugEnumField"
helpviewer_keywords: 
  - "Interfaz IDebugEnumField"
ms.assetid: 42f685bf-0f39-47f4-98b0-6022efe2bf97
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEnumField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

esta interfaz representa un tipo de enumeración.  
  
## Sintaxis  
  
```  
IDebugEnumField : IDebugContainerField  
```  
  
## Notas para los implementadores  
 Un proveedor de token implementa esta interfaz para representar una enumeración.  
  
## Notas para los llamadores  
 utilice [QueryInterface](/visual-cpp/atl/queryinterface) para obtener esta interfaz de la interfaz de [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) si [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) devuelve `FIELD_TYPE_ENUM`.  
  
## métodos en el orden de VTable  
 Además de los métodos de las interfaces de `IDebugField` y de `IDebugContainerField` , esta interfaz implementa los siguientes métodos:  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetUnderlyingSymbol](../../../extensibility/debugger/reference/idebugenumfield-getunderlyingsymbol.md)|devuelve [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que describe el nombre para este tipo de enumeración.|  
|[GetStringFromValue](../../../extensibility/debugger/reference/idebugenumfield-getstringfromvalue.md)|Devuelve el nombre del asociado constante de enumeración con el valor especificado.|  
|[GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)|Devuelve el valor asociado a la enumeración con nombre constante|  
|[GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)|Devuelve el valor asociado a la enumeración determinada caso constante de nombre pero el omitir.|  
  
## Comentarios  
 Es el token subyacente que se enlaza realmente en una ubicación con [Enlazar](../../../extensibility/debugger/reference/idebugbinder-bind.md).  
  
## Requisitos  
 encabezado: sh.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [Enlazar](../../../extensibility/debugger/reference/idebugbinder-bind.md)