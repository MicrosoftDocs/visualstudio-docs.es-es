---
title: Función SccGetEvents | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80700818"
---
# <a name="sccgetevents-function"></a>SccGetEvents función)
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

de Estructura de contexto del complemento de control de código fuente.

 lpFileName

[in, out] Búfer en el que el complemento de control de código fuente coloca el nombre de archivo devuelto (hasta _MAX_PATH caracteres).

 lpStatus

[in, out] Devuelve el código de estado (vea el [código de estado de archivo](../extensibility/file-status-code-enumerator.md) para ver los posibles valores).

 pnEventsRemaining

[in, out] Devuelve el número de entradas que quedan en la cola después de esta llamada. Si este número es grande, el llamador puede decidir llamar a [SccQueryInfo](../extensibility/sccqueryinfo-function.md) para obtener toda la información de una vez.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|Los eventos se obtienen correctamente.|
|SCC_E_OPNOTSUPPORTED|Esta función no se admite.|
|SCC_E_NONSPECIFICERROR|Error no específico.|

## <a name="remarks"></a>Observaciones
 Se llama a esta función durante el procesamiento inactivo para ver si ha habido actualizaciones de estado para los archivos bajo control de código fuente. El complemento de control de código fuente mantiene el estado de todos los archivos que conoce y, cada vez que el complemento indica un cambio de estado, el estado y el archivo asociado se almacenan en una cola. Cuando `SccGetEvents` se llama a, se recupera y se devuelve el elemento superior de la cola. Esta función está restringida para devolver solo información almacenada previamente en la memoria caché y debe tener un procesamiento muy rápido (es decir, no se lee el disco o se solicita el estado al sistema de control de código fuente); de lo contrario, es posible que el rendimiento del IDE empiece a degradarse.

 Si no hay ninguna actualización de estado para el informe, el complemento de control de código fuente almacena una cadena vacía en el búfer señalado por `lpFileName` . De lo contrario, el complemento almacena el nombre completo de la ruta de acceso del archivo para el que ha cambiado la información de estado y devuelve el código de estado adecuado (uno de los valores detallados en el [código de estado de archivo](../extensibility/file-status-code-enumerator.md)).

## <a name="see-also"></a>Vea también
- [Funciones de la API del complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [Código de estado del archivo](../extensibility/file-status-code-enumerator.md)
