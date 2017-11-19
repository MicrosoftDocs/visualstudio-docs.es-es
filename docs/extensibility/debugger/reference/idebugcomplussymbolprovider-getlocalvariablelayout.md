---
title: IDebugComPlusSymbolProvider::GetLocalVariablelayout | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GetLocalVariablelayout
- IDebugComPlusSymbolProvider::GetLocalVariablelayout
ms.assetid: b7328d85-e5e9-4d9f-bcd1-e7711fd33878
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: aa002841358f4aa464a9120b9100088915e9dfa9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcomplussymbolprovidergetlocalvariablelayout"></a>IDebugComPlusSymbolProvider::GetLocalVariablelayout
Recupera el diseño de las variables locales para un conjunto de métodos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetLocalVariablelayout(  
   ULONG32   ulAppDomainID,  
   GUID      guidModule,  
   ULONG32   cMethods,  
   _mdToken  rgMethodTokens[],  
   IStream** pStreamLayout  
);  
```  
  
```csharp  
int GetLocalVariablelayout(  
   uint        ulAppDomainID,  
   Guid        guidModule,  
   uint        cMethods,  
   int[]       rgMethodTokens,  
   out IStream pStreamLayout  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ulAppDomainID`  
 [in] Identificador del dominio de aplicación.  
  
 `guidModule`  
 [in] Identificador único del módulo.  
  
 `cMethods`  
 [in] Número del método de tokens en el `rgMethodTokens` matriz.  
  
 `rgMethodTokens`  
 [in] Matriz de símbolos (token) de método.  
  
 `pStreamLayout`  
 [out] Una secuencia de texto que contiene el diseño de la variable.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo implementar este método para un **CDebugSymbolProvider** objeto que expone la [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) interfaz.  
  
```cpp  
HRESULT CDebugSymbolProvider::GetLocalVariablelayout(  
    ULONG32 ulAppDomainID,   
    GUID guidModule,   
    ULONG32 cMethods,   
    _mdToken rgMethodTokens[],   
    IStream** ppStreamLayout)  
{  
    HRESULT hr = S_OK;  
  
    METHOD_ENTRY(CDebugSymbolProvider::GetLocalVariablelayout);  
  
    CComPtr<ISymUnmanagedReader> symReader;  
    IfFailRet(GetSymUnmanagedReader(ulAppDomainID, guidModule, (IUnknown **) &symReader));  
    CComPtr<IStream> stream;  
    IfFailRet(CreateStreamOnHGlobal(NULL, true, &stream));  
  
    for (ULONG32 iMethod = 0; iMethod < cMethods; iMethod += 1)  
    {  
        CComPtr<ISymUnmanagedMethod> method;  
        IfFailRet(symReader->GetMethod(rgMethodTokens[iMethod], &method));  
        CComPtr<ISymUnmanagedScope> rootScope;  
        IfFailRet(method->GetRootScope(&rootScope));  
  
        //  
        // Add the method's variables to the stream  
        //  
        IfFailRet(AddScopeToStream(rootScope, 0, stream));  
  
        // do end of method marker  
        ULONG32 depth = 0xFFFFFFFF;  
        ULONG cb = 0;  
        IfFailRet(stream->Write(&depth, sizeof(depth), &cb));  
    }  
  
    LARGE_INTEGER pos;  
    pos.QuadPart = 0;  
    IfFailRet(stream->Seek(pos, STREAM_SEEK_SET, 0));  
    *ppStreamLayout = stream.Detach();  
  
    METHOD_EXIT(CDebugSymbolProvider::GetLocalVariablelayout, hr);  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)