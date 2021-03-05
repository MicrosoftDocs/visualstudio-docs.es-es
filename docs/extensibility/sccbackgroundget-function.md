---
description: Esta función recupera del control de código fuente de cada uno de los archivos especificados sin interacción del usuario.
title: Función SccBackgroundGet | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccBackgroundGet
helpviewer_keywords:
- SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4df0866458f04081c82796767808194b292866a1
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102220929"
---
# <a name="sccbackgroundget-function"></a>SccBackgroundGet función)
Esta función recupera del control de código fuente de cada uno de los archivos especificados sin interacción del usuario.

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

de Puntero de contexto del complemento de control de código fuente.

 N archivos

de Número de archivos especificados en la `lpFileNames` matriz.

 lpFileNames

[in, out] Matriz de nombres de los archivos que se van a recuperar.

> [!NOTE]
> Los nombres deben ser nombres de archivo locales completos.

 dwFlags

de Marcas de comandos ( `SCC_GET_ALL` , `SCC_GET_RECURSIVE` ).

 dwBackgroundOperationID

de Un valor único asociado a esta operación.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|Operación completada correctamente.|
|SCC_E_BACKGROUNDGETINPROGRESS|Ya hay una recuperación en segundo plano en curso (el complemento de control de código fuente solo debe devolver este valor si no admite operaciones por lotes simultáneas).|
|SCC_I_OPERATIONCANCELED|La operación se canceló antes de completarse.|

## <a name="remarks"></a>Observaciones
 Siempre se llama a esta función en un subproceso distinto del que cargó el complemento de control de código fuente. No se espera que esta función devuelva hasta que se haya hecho; sin embargo, se puede llamar varias veces con varias listas de archivos al mismo tiempo.

 El uso del `dwFlags` argumento es el mismo que el de [SccGet](../extensibility/sccget-function.md).

## <a name="see-also"></a>Consulte también
- [Funciones de la API del complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [SccGet](../extensibility/sccget-function.md)
