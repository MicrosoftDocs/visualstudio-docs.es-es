---
title: IDebugSettingsCallback2::GetEEMetricString ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::GetEEMetricString
ms.assetid: 85e3c093-6a91-4101-ab32-d8ac6eed4918
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ec2d8d321045900ac208297f7b007ce5266953f4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720026"
---
# <a name="idebugsettingscallback2geteemetricstring"></a>IDebugSettingsCallback2::GetEEMetricString
Recupera la cadena de valor de una métrica de evaluador de expresiones dado su nombre.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetEEMetricString(
   REFGUID guidLang,
   REFGUID guidVendor,
   LPCWSTR pszMetric,
   BSTR*   pbstrValue
);
```

```csharp
private int GetEEMetricString(
   ref Guid   guidLang,
   ref Guid   guidVendor,
   string     pszMetric,
   out string pbstrValue
);
```

## <a name="parameters"></a>Parámetros
`guidLang`\
[en] Identificador único del lenguaje de programación.

`guidVendor`\
[en] Identificador único del proveedor.

`pszMetric`\
[en] Nombre de la métrica.

`pbstrValue`\
[fuera] Devuelve la cadena de valor de métrica.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)
