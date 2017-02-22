---
title: "IDebugPointerField | Microsoft Docs"
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
  - "IDebugPointerField"
helpviewer_keywords: 
  - "Interfaz IDebugPointerField"
ms.assetid: d51bd5b2-f18e-4e27-b4fb-e6f652fbf635
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPointerField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

esta interfaz representa un tipo de puntero.  
  
## Sintaxis  
  
```  
IDebugPointerField : IDebugContainerField  
```  
  
## Notas para los implementadores  
 El proveedor del token implementa esta interfaz para representar un puntero.  
  
## Notas para los llamadores  
 utilice [QueryInterface](/visual-cpp/atl/queryinterface) para obtener esta interfaz de la interfaz de [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) si [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) devuelve `FIELD_TYPE_POINTER`.  
  
## métodos en el orden de Vtable  
 Además de los métodos de las interfaces de `IDebugField` y de `IDebugContainerField` , esta interfaz implementa el método siguiente:  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|Devuelve [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que describe el destino del puntero.|  
  
## Comentarios  
 En C\/C\+\+, un puntero puede ser un contenedor si se utiliza con la notación de matrices.  Por ejemplo, dada `char *pString`, `pString` tiene un tipo de puntero a `char`.  `pString[3]` tiene el tipo de un contenedor que sea un puntero a `char` que hace referencia el cuarto elemento de ese contenedor.  
  
## Requisitos  
 encabezado: sh.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)