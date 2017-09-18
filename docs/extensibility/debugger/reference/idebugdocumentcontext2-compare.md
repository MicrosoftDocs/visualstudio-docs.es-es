---
title: "IDebugDocumentContext2::Compare | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentContext2::Compare"
helpviewer_keywords: 
  - "IDebugDocumentContext2::Compare"
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDocumentContext2::Compare
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Compara este contexto de documento a una matriz determinado de contextos de documento.  
  
## Sintaxis  
  
```cpp#  
HRESULT Compare(   
   DOCCONTEXT_COMPARE       compare,  
   IDebugDocumentContext2** rgpDocContextSet,  
   DWORD                    dwDocContextSetLen,  
   DWORD*                   pdwDocContext  
);  
```  
  
```c#  
int Compare(   
   enum_ DOCCONTEXT_COMPARE compare,  
   IDebugDocumentContext2[] rgpDocContextSet,  
   uint                     dwDocContextSetLen,  
   out uint                 pdwDocContext  
);  
```  
  
#### Parámetros  
 `compare`  
 \[in\]  Un valor de enumeración de [DOCCONTEXT\_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) que especifica el tipo de comparación.  
  
 `rgpDocContextSet`  
 \[in\]  Matriz de los objetos de [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) a los que representa los contextos de documento comparados.  
  
 `dwDocContextSetLen`  
 \[in\]  La longitud de la matriz de contextos de documento a comparar.  
  
 `pdwDocContext`  
 \[out\]  Devuelve el índice de la matriz de `rgpDocContextSet` del primer contexto de documento que satisface la comparación.  
  
## Valor devuelto  
 Devuelve `S_OK` si se encontró una coincidencia.  Devuelve `S_FALSE` si no se encuentra ninguna coincidencia.  De lo contrario, devuelve un código de error.  
  
## Comentarios  
 Los objetos de [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) que se pasan a la matriz se deben implementar por el mismo motor de depuración que implementa el objeto de `IDebugDocumentContext2` que es invitado; si no, la comparación no es válida.  
  
## Vea también  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [DOCCONTEXT\_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)