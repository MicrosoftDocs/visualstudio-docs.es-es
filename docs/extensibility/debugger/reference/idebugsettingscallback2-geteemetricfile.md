---
title: IDebugSettingsCallback2::GetEEMetricFile ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::GetEEMetricFile
ms.assetid: 3a0bf9e5-bbd2-4d15-840d-8244732787fc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2aafda1563d2f948ea0871f920faa8bbbef766f7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720048"
---
# <a name="idebugsettingscallback2geteemetricfile"></a>IDebugSettingsCallback2::GetEEMetricFile
Recupera el archivo de métrica del evaluador de expresiones dado el nombre o la métrica.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetEEMetricFile(
   REFGUID guidLang,
   REFGUID guidVendor,
   LPCWSTR pszMetric,
   BSTR*   pbstrValue
);
```

```csharp
private int GetEEMetricFile(
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
[fuera] Devuelve el contenido del archivo de métricas como una cadena.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)
