---
title: IDiaSymbol::get_frontEndBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_frontEndBuild method
ms.assetid: f7dab1c6-112b-4966-baa5-afc976949c76
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a23db75b2e62e3ffbe2d17f14e36806c2dbb9955
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740658"
---
# <a name="idiasymbolget_frontendbuild"></a>IDiaSymbol::get_frontEndBuild
Recupera el número de compilación de front-end.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT get_frontEndBuild ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parámetros
 `pRetVal`

enuncia Devuelve el número de compilación de front-end. Vea la sección Comentarios.

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