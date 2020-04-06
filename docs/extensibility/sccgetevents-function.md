---
title: Función SccGetEvents ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetEvents
helpviewer_keywords:
- SccGetEvents function
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 91b3debf0e686ceece3048cf3d92b629e3359edd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700818"
---
# <a name="sccgetevents-function"></a>Función SccGetEvents
Esta función recupera un evento de estado en cola.

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccGetEvents (
   LPVOID pvContext,
   LPSTR  lpFileName,
   LPLONG lpStatus,
   LPLONG pnEventsRemaining
);
```

### <a name="parameters"></a>Parámetros
 pvContext

[en] La estructura de contexto del complemento de control de código fuente.

 lpFileName

[adentro, fuera] Zona de influencia donde el complemento de control de código fuente coloca el nombre de archivo devuelto (hasta _MAX_PATH caracteres).

 lpStatus

[adentro, fuera] Devuelve el código de estado (consulte Código de [estado de](../extensibility/file-status-code-enumerator.md) archivo para los valores posibles).

 pnEventsRemaining

[adentro, fuera] Devuelve el número de entradas que quedan en la cola después de esta llamada. Si este número es grande, el autor de la llamada puede decidir llamar a [SccQueryInfo](../extensibility/sccqueryinfo-function.md) para obtener toda la información a la vez.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|Obtener eventos realizados correctamente.|
|SCC_E_OPNOTSUPPORTED|Esta función no se admite.|
|SCC_E_NONSPECIFICERROR|Fallo inespecífico.|

## <a name="remarks"></a>Observaciones
 Esta función se llama durante el procesamiento inactivo para ver si ha habido actualizaciones de estado para los archivos bajo control de código fuente. El complemento de control de código fuente mantiene el estado de todos los archivos que conoce y, siempre que el complemento anota un cambio de estado, el estado y el archivo asociado se almacenan en una cola. Cuando `SccGetEvents` se llama, se recupera y devuelve el elemento superior de la cola. Esta función está restringida a devolver solo información almacenada previamente en caché y debe tener un cambio de velocidad muy rápido (es decir, sin leer el disco o pedir el estado del sistema de control de código fuente); de lo contrario, el rendimiento del IDE puede comenzar a degradarse.

 Si no hay ninguna actualización de estado para informar, el complemento de `lpFileName`control de código fuente almacena una cadena vacía en el búfer al que apunta . De lo contrario, el complemento almacena el nombre completo de la ruta de acceso del archivo para el que ha cambiado la información de estado y devuelve el código de estado adecuado (uno de los valores detallados en Código de [estado de](../extensibility/file-status-code-enumerator.md)archivo).

## <a name="see-also"></a>Vea también
- [Funciones de API de plug-in de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [Código de estado del archivo](../extensibility/file-status-code-enumerator.md)
