---
title: IDiaLoadCallback2::RestrictReferencePathAccess | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictReferencePathAccess method
ms.assetid: e20cb45c-0360-4ff0-a92c-b1b6f76d6e85
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3406052f4d5466b5b7f52a1da3490d35bbb0508f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742989"
---
# <a name="idialoadcallback2restrictreferencepathaccess"></a>IDiaLoadCallback2::RestrictReferencePathAccess
Determina si se permite buscar un archivo. pdb en la ruta de acceso donde se encuentra el archivo. exe.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT RestrictReferencePathAccess();
```

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Cualquier código de retorno distinto de `S_OK` para evitar buscar un archivo. pdb en la ruta de acceso donde se encuentra el archivo. exe.

## <a name="see-also"></a>Vea también
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)