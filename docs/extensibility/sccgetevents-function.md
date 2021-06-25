---
description: Esta función recupera un evento de estado en cola.
title: SccGetEvents Function | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGetEvents
helpviewer_keywords:
- SccGetEvents function
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9438ac10301e2da43b26a88575e44a8ad2c0bf82
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901063"
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

[in] Estructura de contexto del complemento de control de código fuente.

 lpFileName

[in, out] Búfer donde el complemento de control de código fuente coloca el nombre de archivo devuelto (hasta _MAX_PATH caracteres).

 lpStatus

[in, out] Devuelve el código de estado (consulte [Código de estado del archivo](../extensibility/file-status-code-enumerator.md) para ver los valores posibles).

 pnEventsRemaining

[in, out] Devuelve el número de entradas que quedan en la cola después de esta llamada. Si este número es grande, el autor de la llamada puede decidir llamar a [SccQueryInfo](../extensibility/sccqueryinfo-function.md) para obtener toda la información a la vez.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los valores siguientes:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|Obtener eventos correctamente.|
|SCC_E_OPNOTSUPPORTED|Esta función no se admite.|
|SCC_E_NONSPECIFICERROR|Error no específico.|

## <a name="remarks"></a>Observaciones
 Se llama a esta función durante el procesamiento inactivo para ver si ha habido actualizaciones de estado para los archivos bajo control de código fuente. El complemento de control de código fuente mantiene el estado de todos los archivos que conoce y, cada vez que el complemento anota un cambio de estado, el estado y el archivo asociado se almacenan en una cola. Cuando se llama a , se recupera y devuelve el elemento superior `SccGetEvents` de la cola. Esta función está restringida para devolver solo la información almacenada previamente en caché y debe tener un tiempo de respuesta muy rápido (es decir, sin lectura del disco o solicitando al sistema de control de código fuente el estado); de lo contrario, el rendimiento del IDE puede empezar a degradarse.

 Si no hay ninguna actualización de estado para notificar, el complemento de control de código fuente almacena una cadena vacía en el búfer al que apunta `lpFileName` . De lo contrario, el complemento almacena el nombre de ruta de acceso completo del archivo para el que ha cambiado la información de estado y devuelve el código de estado adecuado (uno de los valores detallados en Código de estado de [archivo](../extensibility/file-status-code-enumerator.md)).

## <a name="see-also"></a>Consulta también
- [Funciones de API del complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [Código de estado del archivo](../extensibility/file-status-code-enumerator.md)
