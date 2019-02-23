---
title: IDebugSettingsCallback2::GetEELocalObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::GetEELocalObject
ms.assetid: e69a3469-a049-420c-b918-c48a1e7b9baf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 22d95914ea3366578cb401c304ac52aa5db5e5a1
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56703687"
---
# <a name="idebugsettingscallback2geteelocalobject"></a>IDebugSettingsCallback2::GetEELocalObject
Recupera un objeto local de expresión del evaluador de expresiones según el nombre de métrica.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetEELocalObject(
   REFGUID     guidLang,
   REFGUID     guidVendor,
   LPCWSTR     pszMetric,
   IUnknown ** ppUnk
);
```

```csharp
private int GetEELocalObject(
   ref Guid          guidLang,
   ref Guid          guidVendor,
   string            pszMetric,
   out System.Object ppUnk
);
```

#### <a name="parameters"></a>Parámetros
 `guidLang`

 [in] Identificador único del lenguaje de programación.

 `guidVendor`

 [in] Identificador único del proveedor.

 `pszMetric`

 [in] Nombre de la métrica.

 `ppUnk`

 [out] Devuelve la expresión de objeto local del evaluador de expresiones.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)