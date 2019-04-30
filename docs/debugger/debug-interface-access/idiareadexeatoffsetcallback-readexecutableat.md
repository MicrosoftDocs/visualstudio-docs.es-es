---
title: IDiaReadExeAtOffsetCallback::ReadExecutableAt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtOffsetCallback::ReadExecutableAt method
ms.assetid: 30b1cef0-b366-4712-8e89-d21f640964f8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0f199db93fa2ea0b3ee2633f9af8a02fff5a4fdf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62828206"
---
# <a name="idiareadexeatoffsetcallbackreadexecutableat"></a>IDiaReadExeAtOffsetCallback::ReadExecutableAt
Lee el número especificado de bytes a partir del desplazamiento especificado desde un archivo ejecutable.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT ReadExecutableAt ( 
   DWORDLONG fileOffset,
   DWORD     cbData,
   DWORD*    pcbData,
   BYTE      data[]
);
```

#### <a name="parameters"></a>Parámetros
 fileOffset

[in] El desplazamiento en el archivo ejecutable al comenzar la lectura.

 cbData

[in] Número de bytes que se leen.

 pcbData

[out] Devuelve el número de bytes leídos.

 data[]

[in, out] Una matriz que se rellena con los bytes leídos del archivo.

## <a name="remarks"></a>Comentarios
 Este método es invocado por el código de soporte técnico DIA para cargar los bytes de datos de una aplicación ejecutable mediante un desplazamiento de archivo absoluta. Se llama a este método de apoyo del [Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) método.

## <a name="see-also"></a>Vea también
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)