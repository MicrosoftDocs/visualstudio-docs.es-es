---
title: IDiaSourceFile::get_checksumType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksumType method
ms.assetid: 4c363e61-a6a9-409a-9cc0-d06eb2bee645
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c85c6ce8f03534c3ed810e530dbd12d8c6d115be
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741827"
---
# <a name="idiasourcefileget_checksumtype"></a>IDiaSourceFile::get_checksumType
Recupera el tipo de suma de comprobación.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT get_checksumType ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parámetros
 `pRetVal`

enuncia Devuelve el tipo de suma de comprobación.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 El tipo de suma de comprobación es un valor que se puede asignar a un algoritmo de suma de comprobación. Por ejemplo, el formato de archivo PDB estándar normalmente puede tener uno de los valores siguientes:

|Tipo de suma de comprobación|Etiqueta CryptoAPI|Descripción|
|-------------------|---------------------|-----------------|
|0|\<none>|No hay ninguna suma de comprobación presente.|
|1|`CALG_MD5`|suma de comprobación generada con el algoritmo hash MD5.|
|2|`CALG_SHA1`|suma de comprobación generada con el algoritmo hash SHA1.|

 Las etiquetas de `CryptoAPI` proceden de la enumeración `ALG_ID`. Para obtener más información sobre los algoritmos hash, consulte la sección `CryptoAPI` del [!INCLUDE[winsdkshort](../../debugger/debug-interface-access/includes/winsdkshort_md.md)] de Microsoft.

 Para obtener los bytes de suma de comprobación reales del archivo de código fuente, llame al método [IDiaSourceFile:: get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md) .

## <a name="see-also"></a>Vea también
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)