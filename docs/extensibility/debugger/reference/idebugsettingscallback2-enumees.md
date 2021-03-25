---
description: Enumera los evaluadores de expresiones disponibles a partir de los identificadores de idioma y proveedor.
title: 'IDebugSettingsCallback2:: Enums | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::EnumEEs
ms.assetid: 9f884c49-426f-461b-b547-9d909486e73f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7606bd46587c7141bddea0c822f08459f2d262d9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105075671"
---
# <a name="idebugsettingscallback2enumees"></a>IDebugSettingsCallback2::EnumEEs
Enumera los evaluadores de expresiones disponibles a partir de los identificadores de idioma y proveedor.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT EnumEEs(
   DWORD  celtBuffer,
   GUID*  rgguidLang,
   GUID*  rgguidVendor,
   DWORD* pceltEEs
);
```

```csharp
public int EnumEEs(
   uint       celtBuffer,
   ref Guid   rgguidLang,
   ref Guid   rgguidVendor,
   ref uint[] pceltEEs
);
```

## <a name="parameters"></a>Parámetros
`celtBuffer`\
de Número de elementos del `pceltEEs` búfer.

`rgguidLang`\
[in, out] Identificador único para el lenguaje de programación.

`rgguidVendor`\
[in, out] Identificador único para el proveedor.

`pceltEEs`\
[in, out] Matriz de evaluadores de expresiones.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Consulte también
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)
