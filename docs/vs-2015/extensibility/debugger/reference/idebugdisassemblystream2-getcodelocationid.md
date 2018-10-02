---
title: IDebugDisassemblyStream2::GetCodeLocationId | Microsoft Docs
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
- IDebugDisassemblyStream2::GetCodeLocationId
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
ms.assetid: 567adfb8-2f54-499a-a027-e4ecb82277ef
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c2e388219d00c2fa3be9d3be61667328c6a189f0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47581477"
---
# <a name="idebugdisassemblystream2getcodelocationid"></a>IDebugDisassemblyStream2::GetCodeLocationId
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDebugDisassemblyStream2::GetCodeLocationId](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid).  
  
Devuelve un identificador de ubicación de código para un contexto de código determinado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT GetCodeLocationId(   
   IDebugCodeContext2* pCodeContext,  
   UINT64*             puCodeLocationId  
);  
```  
  
```csharp  
int GetCodeLocationId(   
   IDebugCodeContext2 pCodeContext,  
   out ulong          puCodeLocationId  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pCodeContext`  
 [in] Un [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) objeto va a convertir en un identificador.  
  
 `puCodeLocationId`  
 [out] Devuelve el identificador de ubicación del código. Vea la sección Comentarios.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error. Devuelve `E_CODE_CONTEXT_OUT_OF_SCOPE` si el contexto de código es válido, pero fuera del ámbito.  
  
## <a name="remarks"></a>Comentarios  
 El identificador de ubicación del código es específico para el motor de depuración (DE) que admiten el desensamblado. Este identificador de ubicación se utiliza internamente por la DE para realizar el seguimiento de las posiciones en el código y suele ser una dirección o el desplazamiento de algún tipo. El único requisito es que si el contexto del código de una ubicación es menor que el contexto del código de otra ubicación, el identificador de ubicación de código correspondiente del primer contexto de código también debe ser menor que el identificador de ubicación del código del segundo contexto de código.  
  
 Para recuperar el contexto del código de un identificador de ubicación del código, llame el [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md) método.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)

