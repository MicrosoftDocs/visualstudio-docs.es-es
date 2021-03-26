---
description: Esta función cierra un proyecto y marca el final de una sesión determinada.
title: Función SccCloseProject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 05dbf0552242bdc1a21ec6dd81a592711f50f391
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085642"
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

## <a name="see-also"></a>Consulte también
- [Funciones de la API del complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
