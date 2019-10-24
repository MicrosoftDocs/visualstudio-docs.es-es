---
title: IDiaStackFrame::get_rawLVarInstanceValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_rawLVarInstanceValue method
ms.assetid: ce526259-85a6-475b-9274-0b3a21d95db2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0b1118517988f6a790cd4f6732eba3bc8a9fc25a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741632"
---
# <a name="idiastackframeget_rawlvarinstancevalue"></a>IDiaStackFrame::get_rawLVarInstanceValue
Este método recupera el valor de la variable local especificada como bytes sin formato.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT get_rawLVarInstanceValue(
   IDiaLVarInstance* pInstance,
   DWORD             cbDataMax,
   DWORD*            pcbData,
   BYTE*             pbData
);
```

#### <a name="parameters"></a>Parámetros
 `pInstance`

de Objeto `IDiaLVarInstance` que representa una instancia de la variable local para la que obtener el valor.

 `cbDataMax`

de Número máximo de bytes en el búfer al que apunta `pbData`. Puede tener un máximo de 8 bytes (`sizeof(ULONGLONG)`).

 `pcbData`

enuncia Devuelve el número real de bytes almacenados en el búfer.

 `pbData`

enuncia Búfer que se va a rellenar con datos. No puede ser `NULL`.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)