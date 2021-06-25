---
title: POPDIRLISTFUNC | Microsoft Docs
description: Obtenga información sobre la función de devolución de llamada POPDIRLISTFUNC, que se pasa a los directorios de actualización para averiguar cuáles están bajo control de código fuente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- POPLISTFUNC
helpviewer_keywords:
- POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8c98b35d9f915e16072333c72df2e1e045850f5d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900400"
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
Se trata de una función de devolución de llamada dada a la función [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) para actualizar una colección de directorios y (opcionalmente) nombres de archivo para averiguar cuáles están bajo control de código fuente.

 Solo se debe llamar a la devolución de llamada para los directorios y nombres de archivo (en la lista dada a la función) que realmente están `POPDIRLISTFUNC` bajo control de código `SccPopulateDirList` fuente.

## <a name="signature"></a>Firma

```cpp
typedef BOOL (*POPDIRLISTFUNC)(
   LPVOID pvCallerData,
   BOOL bFolder,
   LPCSTR lpDirectoryOrFileName
);
```

## <a name="parameters"></a>Parámetros
 pvCallerData

[in] Valor de usuario dado a [SccPopulateDirList.](../extensibility/sccpopulatedirlist-function.md)

 bFolder

[in] `TRUE` si el nombre de `lpDirectoryOrFileName` es un directorio; de lo contrario, el nombre es un nombre de archivo.

 lpDirectoryOrFileName

[in] Ruta de acceso local completa a un nombre de directorio o archivo que está bajo control de código fuente.

## <a name="return-value"></a>Valor devuelto
 El IDE devuelve un código de error adecuado:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|Continúe el procesamiento.|
|SCC_I_OPERATIONCANCELED|Detiene el procesamiento.|
|SCC_E_xxx|Cualquier error de control de código fuente adecuado debe detener el procesamiento.|

## <a name="remarks"></a>Observaciones
 Si el parámetro de la función contiene la marca , la lista posiblemente contendrá nombres de `fOptions` `SccPopulateDirList` `SCC_PDL_INCLUDEFILES` archivo, así como nombres de directorio.

## <a name="see-also"></a>Consulta también
- [Funciones de devolución de llamada implementadas por el IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)
- [Códigos de error](../extensibility/error-codes.md)
