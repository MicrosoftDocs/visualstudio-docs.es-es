---
description: Obtiene el tamaño, en bytes, del valor de propiedad.
title: 'IDebugProperty2:: se obtiene | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetSize
helpviewer_keywords:
- IDebugProperty2::GetSize
ms.assetid: 0deb8ec5-d6fb-4622-bb14-0c46b9459cc6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7db319a420dc63eaec8afcdcbeaa38fe861a4bea
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064792"
---
# <a name="idebugproperty2getsize"></a>IDebugProperty2::GetSize
Obtiene el tamaño, en bytes, del valor de propiedad.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetSize ( 
   DWORD* pdwSize
);
```

```csharp
int GetSize ( 
   out uint pdwSize
);
```

## <a name="parameters"></a>Parámetros
`pdwSize`\
enuncia Devuelve el tamaño, en bytes, del valor de propiedad.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve el código de error. Devuelve `S_GETSIZE_NO_SIZE` si la propiedad no tiene ningún tamaño.

## <a name="see-also"></a>Consulte también
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
