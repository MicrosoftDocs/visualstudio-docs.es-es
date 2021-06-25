---
description: Esta función cierra un proyecto, marcando el final de una sesión determinada.
title: Función SccCloseProject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 859b1ddea99e74cc1c1dec999611e50216c3c98a
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904700"
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
 pvContext Estructura de contexto del complemento de control de código fuente.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los valores siguientes:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|El proyecto se cerró correctamente.|
|SCC_E_PROJNOTOPEN|Actualmente no hay ningún proyecto abierto.|
|SCC_E_NOTAUTHORIZED|El usuario no puede realizar esta operación.|
|SCC_E_NONSPECIFICERROR|Error no específico.|

## <a name="remarks"></a>Observaciones
 Siempre [se llama a SccOpenProject](../extensibility/sccopenproject-function.md) antes de esta función. A continuación, una llamada a esta función va seguida de una llamada a la función o a `SccOpenProject` [SccUninitialize](../extensibility/sccuninitialize-function.md), que finaliza completamente la conexión al sistema de control de código fuente.

## <a name="see-also"></a>Consulta también
- [Funciones de API del complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
