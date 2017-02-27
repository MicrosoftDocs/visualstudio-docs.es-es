---
title: "CONTEXT_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CONTEXT_INFO"
helpviewer_keywords: 
  - "Estructura CONTEXT_INFO"
ms.assetid: 6b513f4e-e7b0-4969-adf0-2205ccc1e09b
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# CONTEXT_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta estructura describe un contexto de memoria o contexto de código.  
  
## Sintaxis  
  
```cpp#  
typedef struct _tagCONTEXT_INFO {   
   CONTEXT_INFO_FIELDS dwFields;  
   BSTR                bstrModuleUrl;  
   BSTR                bstrFunction;  
   TEXT_POSITION       posFunctionOffset;  
   BSTR                bstrAddress;  
   BSTR                bstrAddressOffset;  
   BSTR                bstrAddressAbsolute;  
} CONTEXT_INFO;  
```  
  
```c#  
public struct CONTEXT_INFO {  
   public uint          dwFields;  
   public string        bstrModuleUrl;  
   public string        bstrFunction;  
   public TEXT_POSITION posFunctionOffset;  
   public string        bstrAddress;  
   public string        bstrAddressOffset;  
   public string        bstrAddressAbsolute;  
};  
```  
  
## Members  
 dwFields  
 Una combinación de marcas de la enumeración de [CONTEXT\_INFO\_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) que especifica qué campos son completo**.**  
  
 bstrModuleUrl  
 El nombre del módulo donde se encuentra el contexto.  
  
 bstrFunction  
 El nombre de función donde se encuentra el contexto.  
  
 posFunctionOffset  
 Una estructura de [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) que identifica la línea y el desplazamiento de la columna de la función asociado al contexto del código.  
  
 bstrAddress  
 La dirección del código donde se encuentra el contexto determinado.  
  
 bstrAddressOffset  
 El desplazamiento de la dirección del código donde se encuentra el contexto determinado.  
  
 bstrAddressAbsolute  
 La dirección absoluta en memoria donde se encuentra el contexto especificado.  
  
## Comentarios  
 Esta estructura se devuelve de una llamada al método de [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) .  
  
 Un uso típico de esta estructura tiene compatibilidad integrada con una ventana de depuración de **Memoria** .  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)   
 [CONTEXT\_INFO\_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)   
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)