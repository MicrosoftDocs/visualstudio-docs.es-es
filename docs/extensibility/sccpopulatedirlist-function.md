---
title: Función SccPopulateDirList | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: eac3973bf28a14340b720a51fc291b914822f3d1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836922"
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

de Puntero de contexto del complemento de control de código fuente.

 nDirs

de Número de rutas de acceso de directorio en la `lpDirPaths` matriz.

 lpDirPaths

de Matriz de rutas de acceso del directorio que se va a examinar.

 pfnPopulate

de Función de devolución de llamada a la que se llama para cada ruta de acceso de directorio y (opcionalmente) FILENAME en `lpDirPaths` (vea [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) para obtener más información).

 pvCallerData

de Valor que se va a pasar sin cambiar a la función de devolución de llamada.

 Opciones

de Combinación de valores que controlan cómo se procesan los directorios (consulte la sección "PopulateDirList flags" de [marcadores que usan los comandos específicos](../extensibility/bitflags-used-by-specific-commands.md) para ver los valores posibles).

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|La operación se completó correctamente.|
|SCC_E_UNKNOWNERROR|Se produjo un error.|

## <a name="remarks"></a>Notas
 Solo los directorios y los nombres de archivo (opcionalmente) que se encuentran en el repositorio de control de código fuente se pasan a la función de devolución de llamada.

## <a name="see-also"></a>Vea también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [Marcadores de bits utilizados por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)
- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)
- [Códigos de error](../extensibility/error-codes.md)
