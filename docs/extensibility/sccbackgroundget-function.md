---
description: Esta función recupera del control de código fuente cada uno de los archivos especificados sin interacción del usuario.
title: SccBackgroundGet Function | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccBackgroundGet
helpviewer_keywords:
- SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 316a02e84b4d51f309aecdd98d0409c85ccbdbef
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901245"
---
# <a name="sccbackgroundget-function"></a>Función SccBackgroundGet
Esta función recupera del control de código fuente cada uno de los archivos especificados sin interacción del usuario.

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccBackgroundGet(
   LPVOID  pContext,
   LONG    nFiles,
   LPCSTR* lpFileNames,
   LONG    dwFlags,
   LONG    dwBackgroundOperationID
);
```

### <a name="parameters"></a>Parámetros
 pContext

[in] Puntero de contexto del complemento de control de código fuente.

 nFiles

[in] Número de archivos especificados en la `lpFileNames` matriz.

 lpFileNames

[in, out] Matriz de nombres de archivos que se recuperarán.

> [!NOTE]
> Los nombres deben ser nombres de archivo locales completos.

 dwFlags

[in] Marcas de comandos ( `SCC_GET_ALL` , `SCC_GET_RECURSIVE` ).

 dwBackgroundOperationID

[in] Valor único asociado a esta operación.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los valores siguientes:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|Operación completada correctamente.|
|SCC_E_BACKGROUNDGETINPROGRESS|Ya hay una recuperación en segundo plano en curso (el complemento de control de código fuente solo debe devolverlo si no admite operaciones por lotes simultáneas).|
|SCC_I_OPERATIONCANCELED|La operación se canceló antes de completarse.|

## <a name="remarks"></a>Observaciones
 Siempre se llama a esta función en un subproceso diferente del que cargó el complemento de control de código fuente. No se espera que esta función vuelva hasta que se haya realizado; Sin embargo, se puede llamar varias veces con varias listas de archivos, todas al mismo tiempo.

 El uso del `dwFlags` argumento es el mismo que el de [SccGet.](../extensibility/sccget-function.md)

## <a name="see-also"></a>Consulta también
- [Funciones de API del complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [SccGet](../extensibility/sccget-function.md)
