---
title: 'IDebugGenericParamField:: ConstraintCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- ConstraintCount
- IDebugGenericParamField::ConstraintCount
ms.assetid: 76bef0cb-8a3c-4ce5-87cc-1809de229f33
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5a8f9809df0fa45021aab640bf3ff547efaa1576
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80728080"
---
# <a name="idebuggenericparamfieldconstraintcount"></a>IDebugGenericParamField::ConstraintCount
Devuelve el número de restricciones que están asociadas a este parámetro genérico.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT ConstraintCount(
    ULONG32* pcConst
);
```

```csharp
int ConstraintCount(
    ref uint pcConst
);
```

## <a name="parameters"></a>Parámetros
`pcConst`\
[in, out] Número de restricciones asociadas a este campo.

## <a name="return-value"></a>Valor devuelto
Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra cómo implementar este método para un objeto **CDebugGenericParamFieldType** que expone la interfaz [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md) .

```cpp
HRESULT CDebugGenericParamFieldType::ConstraintCount(ULONG32* pcConst)
{
    HRESULT hr = S_OK;
    CComPtr<IMetaDataImport> pMetadata;
    CComPtr<IMetaDataImport2> pMetadata2;
    HCORENUM hEnum = 0;
    ULONG cConst = 0;

    METHOD_ENTRY( CDebugGenericParamFieldType::ConstraintCount );

    IfFalseGo(pcConst, E_INVALIDARG );
    *pcConst = 0;
    IfFailGo( m_spSH->GetMetadata( m_idModule, &pMetadata ) );
    IfFailGo( pMetadata->QueryInterface(IID_IMetaDataImport2, (void**)&pMetadata2) );
    IfFailGo( pMetadata2->EnumGenericParamConstraints( &hEnum,
              m_tokParam,
              NULL,
              0,
              &cConst) );
    IfFailGo( pMetadata->CountEnum(hEnum, &cConst) );
    pMetadata->CloseEnum(hEnum);
    hEnum = NULL;

    *pcConst = cConst;

Error:

    METHOD_EXIT( CDebugGenericParamFieldType::ConstraintCount, hr );
    return hr;
}
```

## <a name="see-also"></a>Vea también
- [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)
