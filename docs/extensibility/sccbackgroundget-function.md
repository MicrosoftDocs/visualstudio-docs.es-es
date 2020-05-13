---
title: Función SccBackgroundGet ( SccBackgroundGet) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccBackgroundGet
helpviewer_keywords:
- SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b1c07076b6e257bd5519d19f841797fbc652f0c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701227"
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

[en] El puntero de contexto del complemento de control de código fuente.

 nArchivos

[en] Número de archivos especificados en la `lpFileNames` matriz.

 lpFileNames

[adentro, fuera] Matriz de nombres de archivos que se van a recuperar.

> [!NOTE]
> Los nombres deben ser nombres de archivo locales completos.

 dwFlags

[en] Indicadores`SCC_GET_ALL`de `SCC_GET_RECURSIVE`comando ( , ).

 dwBackgroundOperationID

[en] Un valor único asociado a esta operación.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|Operación completada correctamente.|
|SCC_E_BACKGROUNDGETINPROGRESS|Una recuperación en segundo plano ya está en curso (el complemento de control de código fuente debe devolver esto solo si no admite operaciones por lotes simultáneas).|
|SCC_I_OPERATIONCANCELED|La operación fue cancelada antes de ser completada.|

## <a name="remarks"></a>Observaciones
 Esta función siempre se llama en un subproceso diferente del que cargó el complemento de control de código fuente. No se espera que esta función vuelva hasta que se realiza; sin embargo, se puede llamar varias veces con varias listas de archivos, todo al mismo tiempo.

 El uso `dwFlags` del argumento es el mismo que [SccGet](../extensibility/sccget-function.md).

## <a name="see-also"></a>Vea también
- [Funciones de API de plug-in de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [SccGet](../extensibility/sccget-function.md)
