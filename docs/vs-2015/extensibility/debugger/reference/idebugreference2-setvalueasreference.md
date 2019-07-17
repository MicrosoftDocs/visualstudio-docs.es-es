---
title: IDebugReference2::SetValueAsReference | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::SetValueAsReference
helpviewer_keywords:
- IDebugReference2::SetValueAsReference
ms.assetid: 94a545d2-16b9-45e9-b2e7-4e49ff90aad0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2b14ca1293a709dce35f2e8aa45a7fa22bf29845
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68178189"
---
# <a name="idebugreference2setvalueasreference"></a>IDebugReference2::SetValueAsReference
Establece el valor de una referencia desde otra referencia. Reservado para un uso futuro.

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

#### <a name="parameters"></a>Parámetros
 `rgpArgs`

 [in] Una matriz de [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) los objetos utilizados para determinar cómo establecer el valor de referencia.

 `dwArgCount`

 [in] El número de referencias de la matriz.

 `pValue`

 [in] Un [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) objeto desde el que se va a establecer el valor de propiedad.

 `dwTimeout`

 [in] Tiempo máximo, en milisegundos para esperar antes de volver de este método. Use `INFINITE` para esperar indefinidamente.

## <a name="return-value"></a>Valor devuelto
 Siempre devuelve `E_NOTIMPL`.

## <a name="see-also"></a>Vea también
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)