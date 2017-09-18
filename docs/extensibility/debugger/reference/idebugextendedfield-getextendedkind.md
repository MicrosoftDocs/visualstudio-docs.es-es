---
title: "IDebugExtendedField::GetExtendedKind | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugExtendedField::GetExtendedKind"
  - "GetExtendedKind"
ms.assetid: 20dc1c13-3cc0-4bb4-9c99-fa85587c86c3
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugExtendedField::GetExtendedKind
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera la clase extendida de campo especificada.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetExtendedKind(  
   FIELD_KIND_EX* pdwKind  
);  
```  
  
```c#  
int GetExtendedKind(  
   ref enum_FIELD_KIND_EX pdwKind  
);  
```  
  
#### Parámetros  
 `pdwKind`  
 \[in, out\]  Valor de enumeración de [FIELD\_KIND\_EX](../../../extensibility/debugger/reference/field-kind-ex.md) que define la clase de campo.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)