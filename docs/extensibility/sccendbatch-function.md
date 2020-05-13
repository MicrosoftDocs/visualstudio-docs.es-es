---
title: Función SccEndBatch (SccEndBatch) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51fe7e0bc0d417ffa182fbc68fd2779ed0b625d9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700922"
---
# <a name="sccendbatch-function"></a>Función SccEndBatch
Esta función concluye un lote de operaciones de control de código fuente. Es posible que estos lotes no estén anidados.

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccEndBatch(void);
```

## <a name="parameters"></a>Parámetros
 Ninguno.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|Lote de operaciones concluidas con éxito.|
|SCC_E_UNKNOWNERROR|Fallo inespecífico.|

## <a name="remarks"></a>Observaciones
 Los lotes de control de código fuente se usan para ejecutar las mismas operaciones de control de código fuente en varios proyectos o varios contextos. Los lotes se pueden usar para eliminar cuadros de diálogo redundantes de la experiencia del usuario durante una operación por lotes. [El SccBeginBatch](../extensibility/sccbeginbatch-function.md) `SccEndBatch` y la función se utilizan como un par para indicar el principio y el final de una operación. No se pueden anidar.

## <a name="see-also"></a>Vea también
- [Funciones de API de plug-in de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [SccBeginBatch](../extensibility/sccbeginbatch-function.md)
