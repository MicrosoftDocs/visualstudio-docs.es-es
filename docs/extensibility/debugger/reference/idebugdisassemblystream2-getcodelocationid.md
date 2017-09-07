---
title: IDebugDisassemblyStream2::GetCodeLocationId | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
ms.assetid: 567adfb8-2f54-499a-a027-e4ecb82277ef
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 0614509685436f46a2f48eb8b6a6299321f84901
ms.contentlocale: es-es
ms.lasthandoff: 09/06/2017

---
# <a name="idebugdisassemblystream2getcodelocationid"></a>IDebugDisassemblyStream2::GetCodeLocationId
Devuelve un identificador de ubicación de código para un contexto de código determinado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
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
 [in] Un [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) objeto se convierta en un identificador.  
  
 `puCodeLocationId`  
 [out] Devuelve el identificador de ubicación del código. Vea la sección Comentarios.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error. Devuelve `E_CODE_CONTEXT_OUT_OF_SCOPE` si el contexto del código es válido, pero fuera del ámbito.  
  
## <a name="remarks"></a>Comentarios  
 El identificador de ubicación de código es específico para el motor de depuración (Alemania) admiten el desensamblado. Este identificador de ubicación se utiliza internamente por la DE para realizar el seguimiento de las posiciones en el código y suele ser una dirección o desplazamiento de algún tipo. El único requisito es que si el contexto del código de una ubicación es menor que el contexto del código de otra ubicación, el identificador de ubicación de código correspondiente de la primera contexto del código también debe ser menor que el identificador de ubicación de código de la segundo contexto del código.  
  
 Para recuperar el contexto del código de un identificador de ubicación del código, llame a la [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md) método.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)
