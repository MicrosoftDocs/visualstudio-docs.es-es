---
title: IDebugDocumentContext2::Compare | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3a4475dd8031dd75a35dda8950b8005886ec9b47
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53866704"
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
Compara este contexto de documento a una matriz de contextos de documento determinada.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT Compare(   
   DOCCONTEXT_COMPARE       compare,  
   IDebugDocumentContext2** rgpDocContextSet,  
   DWORD                    dwDocContextSetLen,  
   DWORD*                   pdwDocContext  
);  
```  
  
```csharp  
int Compare(   
   enum_ DOCCONTEXT_COMPARE compare,  
   IDebugDocumentContext2[] rgpDocContextSet,  
   uint                     dwDocContextSetLen,  
   out uint                 pdwDocContext  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `compare`  
 [in] Un valor de la [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) enumeración que especifica el tipo de comparación.  
  
 `rgpDocContextSet`  
 [in] Una matriz de [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) objetos que representan los contextos de documento que se compara con.  
  
 `dwDocContextSetLen`  
 [in] La longitud de la matriz de contextos de documento para comparar.  
  
 `pdwDocContext`  
 [out] Devuelve el índice en el `rgpDocContextSet` matriz del primer contexto de documento que satisface la comparación.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` si se encuentra una coincidencia. Devuelve `S_FALSE` si se encuentra ninguna coincidencia. De lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 El [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) objetos que se pasan en la matriz deben ser implementados por el mismo motor de depuración que implementa el `IDebugDocumentContext2` de objeto que se llama; de lo contrario, la comparación no es válida.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)