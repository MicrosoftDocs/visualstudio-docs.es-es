---
title: SccCloseProject (función) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5a5fe721a3b51f4d3f210e7f2d5450e4f4bc6f41
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333930"
---
# <a name="scccloseproject-function"></a>SccCloseProject (función)
Esta función cierra un proyecto, marca el final de una sesión determinada.

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccCloseProject (
   LPVOID pvContext
);
```

### <a name="parameters"></a>Parámetros
 pvContext la estructura de contexto de complemento de control de origen.

## <a name="return-value"></a>Valor devuelto
 La implementación de complemento de control de origen de esta función debe devolver uno de los valores siguientes:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|El proyecto se cerró correctamente.|
|SCC_E_PROJNOTOPEN|No hay ningún proyecto está abierto actualmente.|
|SCC_E_NOTAUTHORIZED|El usuario no puede realizar esta operación.|
|SCC_E_NONSPECIFICERROR|Error no específico.|

## <a name="remarks"></a>Comentarios
 El [SccOpenProject](../extensibility/sccopenproject-function.md) siempre se llama antes de esta función. Una llamada a esta función, a continuación, seguida de una llamada a la `SccOpenProject` función o el [SccUninitialize](../extensibility/sccuninitialize-function.md), que finaliza la conexión con el sistema de control de código fuente completo.

## <a name="see-also"></a>Vea también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)