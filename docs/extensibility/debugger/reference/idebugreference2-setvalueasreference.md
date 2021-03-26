---
description: Establece el valor de una referencia desde otra referencia.
title: 'IDebugReference2:: SetValueAsReference | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::SetValueAsReference
helpviewer_keywords:
- IDebugReference2::SetValueAsReference
ms.assetid: 94a545d2-16b9-45e9-b2e7-4e49ff90aad0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c78da74368285c3dcfe06c13fdf8e665da0b7947
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105075788"
---
# <a name="idebugreference2setvalueasreference"></a>IDebugReference2::SetValueAsReference
Establece el valor de una referencia desde otra referencia. Reservado para uso futuro.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT SetValueAsReference ( 
   IDebugReference2** rgpArgs,
   DWORD              dwArgCount,
   IDebugReference2*  pValue,
   DWORD              dwTimeout
);
```

```cpp
int SetValueAsReference ( 
   IDebugReference2[] rgpArgs,
   uint               dwArgCount,
   IDebugReference2   pValue,
   uint               dwTimeout
);
```

## <a name="parameters"></a>Parámetros
`rgpArgs`\
de Matriz de objetos [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) que se usa para determinar cómo establecer el valor de referencia.

`dwArgCount`\
de Número de referencias de la matriz.

`pValue`\
de Objeto [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) a partir del cual se va a establecer el valor de propiedad.

`dwTimeout`\
de Tiempo máximo, en milisegundos, que se va a esperar antes de que se devuelva desde este método. Use `INFINITE` para esperar indefinidamente.

## <a name="return-value"></a>Valor devuelto
 Siempre devuelve `E_NOTIMPL`.

## <a name="see-also"></a>Consulte también
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
