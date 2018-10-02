---
title: IDebugCodeContext3::GetProcess | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugCodeContext3::GetProcess
ms.assetid: e082e494-2255-4d9d-a5a9-6dadd904bea8
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a3a31ee8d9d527f00eab2ace0416ffc04ab8c0b0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47574813"
---
# <a name="idebugcodecontext3getprocess"></a>IDebugCodeContext3::GetProcess
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDebugCodeContext3::GetProcess](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugcodecontext3-getprocess).  
  
Recupera una referencia a la interfaz del proceso de depuración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT GetProcess(   
   IDebugProcess2 **ppProcess  
);  
```  
  
```csharp  
public int GetProcess(   
   out IDebugProcess2 ppProcess  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppProcess`  
 [out] Referencia a la interfaz del proceso de depuración.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra cómo implementar este método para un **CDebugCodeContext** objeto que expone el [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md) interfaz.  
  
```cpp#  
HRESULT CDebugCodeContext::GetProcess(IDebugProcess2** ppProcess)  
{  
    HRESULT hr = S_OK;  
    CComPtr<CDebugEngine> pEngine;  
    CComPtr<IDebugPort2> pPort2;  
  
    IfFalseGo( ppProcess, E_INVALIDARG );  
    *ppProcess = NULL;  
  
    IfFalseGo( m_pProgram, E_FAIL );  
    IfFailGo( ((CDebugProgram *)m_pProgram)->GetEngine(&pEngine) );  
    IfFailGo( pEngine->GetSDMProcess(ppProcess) );  
  
Error:  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)

