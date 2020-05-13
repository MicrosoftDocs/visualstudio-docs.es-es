---
title: IDebugProperty2::SetValueAsString ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsString
helpviewer_keywords:
- IDebugProperty2::SetValueAsString
ms.assetid: 9e6a5054-41b7-4223-b509-b93689d366a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 112ded163f38b93e9918387d8ca6beafb8282647
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721241"
---
# <a name="idebugproperty2setvalueasstring"></a>IDebugProperty2::SetValueAsString
Establece el valor de una propiedad de una cadena determinada.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT SetValueAsString ( 
   LPCOLESTR pszValue,
   UINT      nRadix,
   DWORD     dwTimeout
);
```

```csharp
int SetValueAsString ( 
   string pszValue,
   uint   nRadix,
   uint   dwTimeout
);
```

## <a name="parameters"></a>Parámetros
`pszValue`\
[en] Cadena que contiene el valor que se va a establecer.

`nRadix`\
[en] Un radio que se utilizará para interpretar cualquier información numérica. Esto puede ser 0 para intentar determinar el radio automáticamente.

`dwTimeout`\
[en] Especifica el tiempo máximo, en milisegundos, que se debe esperar antes de volver de este método. Se `INFINITE` usa para esperar indefinidamente.

## <a name="return-value"></a>Valor devuelto
 Si se `S_OK`realiza correctamente, devuelve ; de lo contrario devuelve código de error. En la tabla siguiente se muestran otros valores posibles.

|Value|Descripción|
|-----------|-----------------|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|La cadena no se pudo convertir en un valor de propiedad o no se pudo establecer el valor de propiedad.|
|`E_SETVALUE_VALUE_IS_READONLY`|La propiedad es de solo lectura.|

## <a name="see-also"></a>Vea también
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
