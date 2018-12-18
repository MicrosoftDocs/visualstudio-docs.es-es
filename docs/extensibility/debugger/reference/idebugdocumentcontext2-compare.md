---
title: IDebugDocumentContext2::Compare | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: af349d8568d50e2059ab33ad54b14f499c7b6afd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49913467"
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