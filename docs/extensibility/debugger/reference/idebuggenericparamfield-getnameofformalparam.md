---
title: IDebugGenericParamField::GetNameOfFormalParam | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugGenericParamField::GetNameOfFormalParam
- GetNameOfFormalParam
ms.assetid: 05032a83-49ce-4007-b5d6-7b56945b956c
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ed397b8cf41bd75253b8879308aa29b84490360e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebuggenericparamfieldgetnameofformalparam"></a>IDebugGenericParamField::GetNameOfFormalParam
Recupera el nombre de este parámetro genérico.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetNameOfFormalParam (  
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetNameOfFormalParam (  
   string pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pbstrName`  
 [out] Nombre de este parámetro genérico.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo implementar este método para un **CDebugGenericParamFieldType** objeto que expone la [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md) interfaz.  
  
```cpp  
HRESULT CDebugGenericParamFieldType::GetNameOfFormalParam(BSTR *pbstrName)  
{  
    HRESULT hr = S_OK;  
    CComBSTR bstrName;  
  
    METHOD_ENTRY( CDebugGenericParamFieldType::GetNameOfFormalParam );  
  
    IfFalseGo( pbstrName, E_INVALIDARG );  
    IfFailGo( this->LoadProps() );  
    IfNullGo( *pbstrName = SysAllocString(m_bstrName), E_OUTOFMEMORY );  
  
Error:  
  
    METHOD_EXIT( CDebugGenericParamFieldType::GetNameOfFormalParam, hr );  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)