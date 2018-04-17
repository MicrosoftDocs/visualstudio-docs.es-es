---
title: IDebugComPlusSymbolProvider::GetSymAttribute | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugComPlusSymbolProvider::GetSymAttribute
- GetSymAttribute
ms.assetid: 6cbaac92-a60b-4165-a7f5-c34407770f3c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 283333c8d505952e36dc8524d1377fd828142aca
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugcomplussymbolprovidergetsymattribute"></a>IDebugComPlusSymbolProvider::GetSymAttribute
Recupera los símbolos de depuración con el atributo primario indicado para el módulo especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetSymAttribute (  
   ULONG32  ulAppDomainID,  
   GUID     guidModule,  
   _mdToken tokParent,  
   LPOLESTR pstrName,  
   ULONG32  cBuffer,  
   ULONG32* pcBuffer,  
   BYTE*    buffer  
);  
```  
  
```csharp  
int GetSymAttribute (  
   uint      ulAppDomainID,  
   Guid      guidModule,  
   int       tokParent,  
   string    pstrName,  
   uint      cBuffer,  
   out uint  pcBuffer,  
   out int[] buffer  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ulAppDomainID`  
 [in] Identificador del dominio de aplicación.  
  
 `guidModule`  
 [in] Identificador único del módulo.  
  
 `tokParent`  
 [in] Símbolo (token) para el atributo primario.  
  
 `pstrName`  
 [in] Nombre del módulo.  
  
 `cBuffer`  
 [in] Número de bytes necesarios para la salida `buffer`.  
  
 `pcBuffer`  
 [out] Longitud de la salida `buffer`.  
  
 `buffer`  
 [out] Matriz que contiene los símbolos.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo implementar este método para un **CDebugSymbolProvider** objeto que expone la [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) interfaz.  
  
```cpp  
HRESULT CDebugSymbolProvider::GetSymAttribute(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    _mdToken tokParent,  
    __in_z LPOLESTR pstrName,  
    ULONG32 cBuffer,  
    ULONG32 *pcBuffer,  
    BYTE buffer[])  
{  
    HRESULT hr = S_OK;  
    CComPtr<CModule> pModule;  
    Module_ID idModule(ulAppDomainID, guidModule);  
  
    METHOD_ENTRY( CDebugSymbolProvider::GetSymAttribute );  
  
    IfFailGo( GetModule( idModule, &pModule) );  
  
    IfFailGo( pModule->GetSymAttribute( tokParent, pstrName, cBuffer, pcBuffer, buffer ) );  
  
Error:  
  
    METHOD_EXIT(CDebugSymbolProvider::GetSymAttribute, hr);  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)