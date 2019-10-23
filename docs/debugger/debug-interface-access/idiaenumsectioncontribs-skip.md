---
title: IDiaEnumSectionContribs::Skip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Skip method
ms.assetid: 7471a178-5134-41b2-80a6-51ff96abe916
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb371d841c10b64895400f66bf73159f27d68ec1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744261"
---
# <a name="idiaenumsectioncontribsskip"></a>IDiaEnumSectionContribs::Skip
Omite un número especificado de contribuciones de la sección en una secuencia de enumeración.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT Skip( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parámetros
 `celt`

de Número de contribuciones de la sección en la secuencia de enumeración que se va a omitir.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve `S_FALSE` si no hay más contribuciones de sección para omitir.

## <a name="see-also"></a>Vea también
- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)