---
title: Función SccPopulateDirList (SccPopulateDirList) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ac1c51ac694acadd2efb0cd7d1c5a3f1d66ebc1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700551"
---
# <a name="sccpopulatedirlist-function"></a>SccPopulateDirList (Función)
Esta función determina qué directorios y (opcionalmente) archivos se almacenan en el control de código fuente, dada una lista de directorios para examinar.

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccPopulateDirList(
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

[en] El puntero de contexto del complemento de control de código fuente.

 nDirs

[en] Número de rutas `lpDirPaths` de directorio en la matriz.

 lpDirPaths

[en] Matriz de rutas de directorio que se va a examinar.

 pfnPopulate

[en] Función de devolución de llamada para llamar `lpDirPaths` a cada ruta de acceso de directorio y (opcionalmente) nombre de archivo en (consulte [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) para obtener más información).

 pvCallerData

[en] Valor que se va a pasar sin cambios a la función de devolución de llamada.

 fOptions

[en] Combinación de valores que controlan cómo se procesan los directorios (consulte la sección "PopulateDirList flags" de [Bitflags Used by Specific Commands](../extensibility/bitflags-used-by-specific-commands.md) para los valores posibles).

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|La operación se completó correctamente.|
|SCC_E_UNKNOWNERROR|Se produjo un error.|

## <a name="remarks"></a>Observaciones
 Solo los directorios y (opcionalmente) nombres de archivo que están realmente en el repositorio de control de código fuente se pasan a la función de devolución de llamada.

## <a name="see-also"></a>Vea también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [Marcadores de bits utilizados por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)
- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)
- [Códigos de error](../extensibility/error-codes.md)
