---
title: IDiaSession::findLines | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLines method
ms.assetid: d6e84916-fd55-457e-b057-57f97b51fe73
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b127cbc5c9ddc5a2aa2d293d1371bab18d191fdb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839295"
---
# <a name="idiasessionfindlines"></a>IDiaSession::findLines
Recupera los números de línea en la operación de compilación especificado y los identificadores de archivo de origen.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT findLines ( 
   IDiaSymbol*           compiland,
   IDiaSourceFile*       file,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parámetros
 `compiland`

[in] Un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objeto que representa la operación de compilación. Utilice esta interfaz como un contexto en el que se va a buscar los números de línea.

 `file`

[in] Un [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) objeto que representa el archivo de origen en el que se va a buscar los números de línea.

 `ppResult`

[out] Devuelve un [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) recupera el objeto que contiene una lista de los números de línea.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)