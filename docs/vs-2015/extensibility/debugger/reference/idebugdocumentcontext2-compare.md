---
title: IDebugDocumentContext2::Compare | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2e100fdd8e303bf9a85e9ea8f7f0c77b6b300d8b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47566746"
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDebugDocumentContext2::Compare](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugdocumentcontext2-compare).  
  
Compara este contexto de documento a una matriz de contextos de documento determinada.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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

