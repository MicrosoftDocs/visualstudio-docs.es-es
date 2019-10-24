---
title: IDiaSymbol::get_backEndMinor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_backEndMinor method
ms.assetid: 37f38d19-6685-440d-a477-7127c4f8699e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2bfe1e5e3fdd78774142bf2cfe8ce6f097d64ef2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740973"
---
# <a name="idiasymbolget_backendminor"></a>IDiaSymbol::get_backEndMinor
Recupera el número de versión secundaria de back-end del compilador.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT get_backEndMinor ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parámetros
 `pRetVal`

enuncia Devuelve el número de versión secundaria de back-end. Vea la sección Comentarios.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve `S_FALSE` o un código de error.

> [!NOTE]
> Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.

## <a name="remarks"></a>Comentarios
 Un compilador normalmente se compone de dos elementos principales: el front-end (el analizador), que controla el análisis del código fuente en un formato intermedio y un back-end (generador de código), que convierte el formato intermedio en ensamblado. No es raro que el front-end tenga una versión diferente que el back-end.

 Un número de versión de front-end o back-end consta de tres partes: \<major >. \<minor >. \<build >, donde \<major > es el número de versión principal, \<minor > es el número de versión secundaria y \<build > es el número de compilación. Por ejemplo, 13.10.3077.

## <a name="requirements"></a>Requisitos

|Requisito|Descripción|
|-----------------|-----------------|
|Encabezado:|dia2.h|
|Versión:|SDK de DIA v 7.0|

## <a name="see-also"></a>Vea también
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)