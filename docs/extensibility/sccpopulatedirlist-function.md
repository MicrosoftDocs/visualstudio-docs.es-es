---
description: Esta función determina qué directorios y archivos (opcionalmente) se almacenan en el control de código fuente, dada una lista de directorios que se van a examinar.
title: SccPopulateDirList (Función) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bf2620ff42106be7c858c5104dbf9cb2521252ab
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902363"
---
# <a name="sccpopulatedirlist-function"></a>SccPopulateDirList (Función)
Esta función determina qué directorios y archivos (opcionalmente) se almacenan en el control de código fuente, dada una lista de directorios que se van a examinar.

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccPopulateDirList(
   LPVOID        pContext,
   LONG          nDirs,
   LPCSTR*       lpDirPaths,
   POPDIRLISTFUNCpfnPopulate,
   LPVOID        pvCallerData,
   LONG          fOptions
);
```

#### <a name="parameters"></a>Parámetros
 pContext

[in] Puntero de contexto del complemento de control de código fuente.

 nDirs

[in] Número de rutas de acceso de directorio de la `lpDirPaths` matriz.

 lpDirPaths

[in] Matriz de rutas de acceso de directorio que se examinarán.

 pfnPopulate

[in] Función de devolución de llamada para llamar a para cada ruta de acceso de directorio y (opcionalmente) nombre de archivo en `lpDirPaths` [(vea POPDIRLISTFUNC para](../extensibility/popdirlistfunc.md) obtener más información).

 pvCallerData

[in] Valor que se va a pasar sin cambios a la función de devolución de llamada.

 fOptions

[in] Combinación de valores que controlan cómo se procesan los directorios (consulte la sección "Marcas PopulateDirList" de Marcas de bits usadas por comandos [específicos](../extensibility/bitflags-used-by-specific-commands.md) para ver los valores posibles).

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los valores siguientes:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|La operación se completó correctamente.|
|SCC_E_UNKNOWNERROR|Se produjo un error.|

## <a name="remarks"></a>Observaciones
 Solo los directorios y (opcionalmente) los nombres de archivo que están realmente en el repositorio de control de código fuente se pasan a la función de devolución de llamada.

## <a name="see-also"></a>Consulta también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [Marcadores de bits utilizados por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)
- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)
- [Códigos de error](../extensibility/error-codes.md)
