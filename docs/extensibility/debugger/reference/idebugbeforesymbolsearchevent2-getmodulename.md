---
title: "IDebugBeforeSymbolSearchEvent2::GetModuleName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetModuleName"
  - "IDebugBeforeSymbolSearchEvent2::GetModuleName"
ms.assetid: 0b4abeac-2eaf-4b2e-a2d5-c9ec303bc869
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugBeforeSymbolSearchEvent2::GetModuleName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera el nombre del módulo que se está depurando actualmente.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetModuleName(   
   BSTR *pbstrModuleName  
);  
```  
  
```c#  
public int GetModuleName (  
   string pbstrModuleName  
);  
```  
  
#### Parámetros  
 `pbstrModuleName`  
 \[out\]  Nombre del módulo.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo implementar este método para un objeto **de CDebugBeforeSymbolSearchEventBase** que expone la interfaz de [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md) .  
  
```cpp#  
STDMETHODIMP CDebugBeforeSymbolSearchEventBase::GetModuleName(BSTR *pbstrModuleName)  
{  
    HRESULT hRes = E_FAIL;  
  
    if (m_bstrModuleName)  
    {  
  
        *pbstrModuleName = SysAllocString( m_bstrModuleName);  
  
        if (*pbstrModuleName)  
        {  
            hRes = S_OK;  
        }  
    }  
  
    return ( hRes );  
}  
```  
  
## Vea también  
 [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md)