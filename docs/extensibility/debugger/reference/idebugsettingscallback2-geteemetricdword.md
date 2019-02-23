---
title: IDebugSettingsCallback2::GetEEMetricDword | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::GetEEMetricDword
ms.assetid: c5f8f417-0ef0-4fd0-a779-b0a8ead4effe
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 475a2a22e148c1b2849d469889492f7eb271e7e1
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56697655"
---
# <a name="idebugsettingscallback2geteemetricdword"></a>IDebugSettingsCallback2::GetEEMetricDword
Recupera un valor que corresponde a la métrica especificada del evaluador de expresiones.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetEEMetricDword(
   REFGUID guidLang,
   REFGUID guidVendor,
   LPCWSTR pszMetric,
   DWORD*  pdwValue
);
```

```csharp
private int GetEEMetricDword(
   ref Guid guidLang,
   ref Guid guidVendor,
   string   pszMetric,
   out uint pdwValue
);
```

#### <a name="parameters"></a>Parámetros
 `guidLang`

 [in] Identificador único del lenguaje de programación.

 `guidVendor`

 [in] Identificador único del proveedor.

 `pszMetric`

 [in] Nombre de la métrica.

 `pdwValue`

 [out] Devuelve el valor que corresponde a la cadena de métrica.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)