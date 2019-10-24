---
title: IDiaSymbol::get_numberOfAcceleratorPointerTags | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 1886e3ec-b227-4187-8d93-c5144b4b77ae
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 47c5827348c7b7cb450017a0e6176d71f555c841
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739696"
---
# <a name="idiasymbolget_numberofacceleratorpointertags"></a>IDiaSymbol::get_numberOfAcceleratorPointerTags
Devuelve el número de etiquetas de puntero de acelerador en una C++ función de código auxiliar de amp.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT get_numberOfAcceleratorPointerTags(
   DWORD* count);
```

#### <a name="parameters"></a>Parámetros
 `count`

enuncia Puntero a una `DWORD` que contiene el número de etiquetas de puntero de acelerador C++ en una función de código auxiliar de amp.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve `S_FALSE` o un código de error.

## <a name="remarks"></a>Comentarios
 Se llama a este método en una interfaz de `IDiaSymbol` que corresponde C++ a una función de código auxiliar del acelerador amp.

## <a name="see-also"></a>Vea también
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)