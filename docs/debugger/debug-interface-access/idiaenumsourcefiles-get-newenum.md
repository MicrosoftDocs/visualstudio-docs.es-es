---
title: IDiaEnumSourceFiles::get__NewEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles::get__NewEnum method
ms.assetid: 8405966c-64b4-4743-9a83-0e27ca2047c7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2460194426384d574cf2dbd36d89819d38472f14
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56611521"
---
# <a name="idiaenumsourcefilesgetnewenum"></a>IDiaEnumSourceFiles::get__NewEnum
Recupera el <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> versión de este enumerador.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT get__NewEnum ( 
   IUnknown** pRetVal
);
```

#### <a name="parameters"></a>Parámetros
 pRetVal

[out] Devuelve el `IUnknown` interfaz que representa el <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> versión de este enumerador.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)