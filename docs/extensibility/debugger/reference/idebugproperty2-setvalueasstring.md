---
description: Establece el valor de una propiedad a partir de una cadena determinada.
title: 'IDebugProperty2:: SetValueAsString | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsString
helpviewer_keywords:
- IDebugProperty2::SetValueAsString
ms.assetid: 9e6a5054-41b7-4223-b509-b93689d366a5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1e3a80c6d5c6e9f3b7f5d9b68ed08dd0b39d940e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064746"
---
# <a name="idebugproperty2setvalueasstring"></a>IDebugProperty2::SetValueAsString
Establece el valor de una propiedad a partir de una cadena determinada.

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
de Cadena que contiene el valor que se va a establecer.

`nRadix`\
de Base que se va a utilizar para interpretar cualquier información numérica. Puede ser 0 para intentar determinar la base automáticamente.

`dwTimeout`\
de Especifica el tiempo máximo, en milisegundos, que se va a esperar antes de que se devuelva desde este método. Use `INFINITE` para esperar indefinidamente.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve el código de error. En la tabla siguiente se muestran otros valores posibles.

|Value|Descripción|
|-----------|-----------------|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|La cadena no se pudo convertir en un valor de propiedad o no se pudo establecer el valor de la propiedad.|
|`E_SETVALUE_VALUE_IS_READONLY`|La propiedad es de solo lectura.|

## <a name="see-also"></a>Consulte también
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
