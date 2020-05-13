---
title: Función SccCloseProject ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 71df385bc0cf42c2437abfd117c2f84bda5b5432
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701045"
---
# <a name="scccloseproject-function"></a>Función SccCloseProject
Esta función cierra un proyecto, marcando el final de una sesión determinada.

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccCloseProject (
   LPVOID pvContext
);
```

### <a name="parameters"></a>Parámetros
 pvContext La estructura de contexto del complemento de control de código fuente.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|El proyecto se cerró con éxito.|
|SCC_E_PROJNOTOPEN|Actualmente no hay ningún proyecto abierto.|
|SCC_E_NOTAUTHORIZED|El usuario no puede realizar esta operación.|
|SCC_E_NONSPECIFICERROR|Fallo inespecífico.|

## <a name="remarks"></a>Observaciones
 El [SccOpenProject](../extensibility/sccopenproject-function.md) siempre se llama antes de esta función. A continuación, una llamada a esta función va seguida de una llamada a la `SccOpenProject` función o a [SccUninitialize](../extensibility/sccuninitialize-function.md), que finaliza completamente la conexión al sistema de control de código fuente.

## <a name="see-also"></a>Vea también
- [Funciones de API de plug-in de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
