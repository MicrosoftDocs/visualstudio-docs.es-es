---
title: IDiaStackWalkHelper::get_registerValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::get_registerValue method
ms.assetid: 46ac5eee-73a3-44a1-8635-6c58ba193cb6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bfb3e219012effe47a2352f7c22c6cf51b4617f9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741416"
---
# <a name="idiastackwalkhelperget_registervalue"></a>IDiaStackWalkHelper::get_registerValue
Recupera el valor de un registro.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT get_registerValue ( 
   DWORD      index,
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Parámetros
 `index`

de Un valor de la enumeración de [enumeración CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md) que especifica en qué registro se obtiene el valor.

 `pRetVal`

enuncia Devuelve el valor actual del registro.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 A pesar del tamaño del parámetro `pRetVal`, una implementación solo debe almacenar lo que normalmente contiene el registro. Por ejemplo, un registro de 8 bits solo contiene los 8 bits más bajos del valor especificado. Este valor de 8 bits se expande a 64 bits cuando se devuelve desde este método.

## <a name="see-also"></a>Vea también
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [Enumeración CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md)