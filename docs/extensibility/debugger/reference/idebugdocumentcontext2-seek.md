---
title: IDebugDocumentContext2::Seek | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDocumentContext2::Seek
helpviewer_keywords:
- IDebugDocumentContext2::Seek
ms.assetid: 71501356-8a82-4d36-b354-6625bdd2baa0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: db5c44d79882d887e8a852f3add491317dbf96fa
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53895531"
---
# <a name="idebugdocumentcontext2seek"></a>IDebugDocumentContext2::Seek
Mueva el contexto del documento mediante un número determinado de las instrucciones o líneas.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT Seek(   
   int                      nCount,  
   IDebugDocumentContext2** ppDocContext  
);  
```  
  
```cpp  
int Seek(   
   int                        nCount,  
   out IDebugDocumentContext2 ppDocContext  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `nCount`  
 [in] El número de instrucciones o líneas para avanzar, según el contexto del documento.  
  
 `ppDocContext`  
 [out] Devuelve un nuevo [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) objeto con la nueva posición.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)