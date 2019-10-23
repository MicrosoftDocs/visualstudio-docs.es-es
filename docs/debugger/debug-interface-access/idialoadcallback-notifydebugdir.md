---
title: IDiaLoadCallback::NotifyDebugDir | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyDebugDir method
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6618440cab9b9042ec371383f6c809ca1d0d11f7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743084"
---
# <a name="idialoadcallbacknotifydebugdir"></a>IDiaLoadCallback::NotifyDebugDir
Se le llama cuando se ha encontrado un directorio de depuración en el archivo. exe.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT NotifyDebugDir ( 
   BOOL  fExecutable,
   DWORD cbData,
   BYTE  data[]
);
```

#### <a name="parameters"></a>Parámetros
 `fExecutable`

[in] `TRUE` si el directorio de depuración se lee desde un ejecutable (en lugar de un archivo. dbg).

 `cbData`

de Recuento de bytes de datos en el directorio de depuración.

 `data[]`

de Una matriz que se rellena con el directorio de depuración.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error. Normalmente, se omite el código de retorno.

## <a name="remarks"></a>Comentarios
 El método [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) invoca esta devolución de llamada cuando encuentra un directorio de depuración mientras procesa el archivo ejecutable.

 Este método elimina la necesidad de que el cliente aplique ingeniería inversa al archivo ejecutable o de depuración para admitir información de depuración distinta de la que se encuentra en el archivo. pdb. Con estos datos, el cliente puede reconocer el tipo de información de depuración disponible y si reside en el archivo ejecutable o en el archivo. dbg.

 La mayoría de los clientes no necesitará esta devolución de llamada porque el método `IDiaDataSource::loadDataForExe` abre de forma transparente los archivos. PDB y. dbg cuando sea necesario para servir símbolos.

## <a name="see-also"></a>Vea también
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)