---
title: Función SccCloseProject | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701045"
---
# <a name="scccloseproject-function"></a>SccCloseProject función)
Esta función cierra un proyecto y marca el final de una sesión determinada.

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccCloseProject (
   LPVOID pvContext
);
```

### <a name="parameters"></a>Parámetros
 pvContext la estructura de contexto del complemento de control de código fuente.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|El proyecto se ha cerrado correctamente.|
|SCC_E_PROJNOTOPEN|No hay ningún proyecto abierto actualmente.|
|SCC_E_NOTAUTHORIZED|El usuario no tiene permiso para realizar esta operación.|
|SCC_E_NONSPECIFICERROR|Error no específico.|

## <a name="remarks"></a>Observaciones
 Siempre se llama a [SccOpenProject](../extensibility/sccopenproject-function.md) antes de esta función. Una llamada a esta función va seguida de una llamada a la `SccOpenProject` función o a [SccUninitialize](../extensibility/sccuninitialize-function.md), que finaliza la conexión al sistema de control de código fuente por completo.

## <a name="see-also"></a>Vea también
- [Funciones de la API del complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
