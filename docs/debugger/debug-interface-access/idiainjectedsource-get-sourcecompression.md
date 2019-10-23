---
title: 'IDiaInjectedSource:: get_sourceCompression | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_sourceCompression method
ms.assetid: 854b142f-23a9-466c-bf7f-98e581d5abcd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9428b30df82d92a8c74511644aaf97f2166807a2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743318"
---
# <a name="idiainjectedsourceget_sourcecompression"></a>IDiaInjectedSource::get_sourceCompression
Recupera el indicador de la compresión de origen utilizada.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT get_sourceCompression ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parámetros
 `pRetVal`

enuncia Devuelve el indicador de la compresión de origen utilizada. Un valor de cero indica que no se ha usado ninguna compresión de origen.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si no se admite esta propiedad. De lo contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 El valor devuelto por este método es específico del compilador utilizado. Por ejemplo, un compilador puede utilizar codificación de longitud de ejecución o compresión de estilo Huffman.

## <a name="see-also"></a>Vea también
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)