---
title: IDebugProgramNode2::GetProgramName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgramNode2::GetProgramName
helpviewer_keywords:
- IDebugProgramNode2::GetProgramName
ms.assetid: 510c7f5d-48ff-4d9f-ad79-fbad9f15239d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d6f678adc135e85f8808cef36d819733033447e4
ms.sourcegitcommit: 845442e2b515c3ca1e4e47b46cc1cef4df4f08d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/20/2019
ms.locfileid: "56450378"
---
# <a name="idebugprogramnode2getprogramname"></a>IDebugProgramNode2::GetProgramName
Obtiene el nombre del programa.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetProgramName (
    BSTR* pbstrProgramName
);
```

```csharp
int GetProgramName (
    out string pbstrProgramName
);
```

#### <a name="parameters"></a>Parámetros
`pbstrProgramName`  
[out] Devuelve el nombre del programa.

## <a name="return-value"></a>Valor devuelto
Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
El nombre de un programa no es lo mismo que la ruta de acceso al programa, aunque el nombre del programa puede formar parte de una ruta de acceso.

## <a name="example"></a>Ejemplo
El ejemplo siguiente muestra cómo implementar este método para una sencilla `CProgram` objeto que implementa el [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) interfaz. El `MakeBstr` función asigna una copia de la cadena especificada como un BSTR.

```cpp
HRESULT CProgram::GetProgramName(BSTR* pbstrProgramName) {
    if (!pbstrProgramName)
        return E_INVALIDARG;

    // Assign the member program name to the passed program name.
    *pbstrProgramName = MakeBstr(m_pszProgramName);
    return NOERROR;
}
```

## <a name="see-also"></a>Vea también
[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
