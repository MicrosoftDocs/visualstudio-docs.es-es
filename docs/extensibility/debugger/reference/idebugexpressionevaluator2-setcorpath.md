---
title: IDebugExpressionEvaluator2::SetCorPath | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SetCorPath
- IDebugExpressionEvaluator2::SetCorPath
ms.assetid: 27b614ff-7325-4f9b-8da4-61ee020c9410
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f99ed6decc69c4da600d22bc146e4958852e6386
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idebugexpressionevaluator2setcorpath"></a>IDebugExpressionEvaluator2::SetCorPath
Establece la ruta de acceso a common language runtime (CLR) cargado en el depurador.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT SetCorPath(  
   LPCOLESTR pcstrCorPath  
);  
```  
  
```csharp  
int SetCorPath(  
   string pcstrCorPath  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pcstrCorPath`  
 [in] Ruta de acceso a lo CLR cargados en el depurador.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo implementar este método para un **ExpressionEvaluatorPackage** objeto que expone la [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md) interfaz.  
  
```cpp  
STDMETHODIMP ExpressionEvaluatorPackage::SetCorPath(LPCOLESTR pcstrCorPath)  
{  
    VerifyInPtr(pcstrCorPath);  
    HRESULT hr = E_FAIL;  
  
    VBEECompilerSingleton *pVBEECompilerSingleton = VBEECompilerSingleton::Instance();  
  
    if (pVBEECompilerSingleton)  
    {  
        pVBEECompilerSingleton->LockEECompiler();  
  
        try  
        {  
            if (!m_pCompiler->FindEECompilerHost(pcstrCorPath, &m_pCompilerHost))  
            {  
                CComObject<CVBEECompilerHost> *pEECompilerHost;  
  
                if (SUCCEEDED(CComObject<CVBEECompilerHost>::CreateInstance(&pEECompilerHost)))  
                {  
                    pEECompilerHost->AddRef();  
                    pEECompilerHost->Init(pcstrCorPath);  
  
                    CComPtr<IVbCompilerHost> srpVBHost;  
                    HRESULT hr2 = pEECompilerHost->QueryInterface(IID_IVbCompilerHost, (void **)&srpVBHost);  
  
                    pEECompilerHost->Release();  
  
                    if (SUCCEEDED(hr2))  
                    {  
                        m_pCompiler->RegisterEECompilerHost(srpVBHost);  
                    }  
                }  
            }  
            else  
            {  
                hr = S_OK;  
            }  
  
            if (m_pCompiler->FindEECompilerHost(pcstrCorPath, &m_pCompilerHost))  
            {  
                ULONG cErrors = 0;  
                ULONG cWarnings = 0;  
  
                m_pCompiler->CompileToBound(m_pCompilerHost, &cErrors, &cWarnings, NULL);  
  
                // This needs to happen after bound  
                if (m_pCompilerHost->GetVbLibraryType() == TLB_AutoDetect)  
                {  
                    m_pCompilerHost->AutoSetVbLibraryType();  
                }  
  
                VSASSERT(m_pCompiler && m_pCompilerHost && m_pCompilerHost->GetIntrinsicSymbol(t_i4) != NULL, "Invalid state");  
  
                if (cErrors + cWarnings > 0)  
                {  
                    VSFAIL("Errors from mscorlib.dll and vb runtime!");                 
                    __leave;  
                }  
  
                hr = S_OK;  
            }  
            else  
            {  
                VSFAIL("FindCompilerHost shouldn't have failed!");  
            }  
        }  
        catch_hresult;  
  
        VSASSERT(m_pCompilerHost->GetComPlusProject()->GetCompState() >= CS_Bound, "Debugger mscorlib not in bound state");  
  
        pVBEECompilerSingleton->UnlockEECompiler();  
    }  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)