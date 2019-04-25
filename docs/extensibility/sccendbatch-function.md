---
title: SccEndBatch (función) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e0662e4c4d1d71e2c9ae0e8f40ff21868d6b9a5d
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56683927"
---
# <a name="sccendbatch-function"></a>SccEndBatch (función)
Esta función finaliza un lote de operaciones de control de código fuente. Estos lotes no pueden anidarse.

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccEndBatch(void);
```

## <a name="parameters"></a>Parámetros
 Ninguno.

## <a name="return-value"></a>Valor devuelto
 La implementación de complemento de control de origen de esta función debe devolver uno de los valores siguientes:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|Lote de operaciones concluido correctamente.|
|SCC_E_UNKNOWNERROR|Error no específico.|

## <a name="remarks"></a>Comentarios
 Los lotes de control de código fuente se usan para ejecutar las mismas operaciones de control de código fuente a través de varios proyectos o varios contextos. Los lotes pueden usarse para eliminar cuadros de diálogo con redundancia de la experiencia del usuario durante una operación por lotes. El [SccBeginBatch](../extensibility/sccbeginbatch-function.md) y `SccEndBatch` función sirven como un par para indicar el principio y al final de una operación. No se pueden anidar.

## <a name="see-also"></a>Vea también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [SccBeginBatch](../extensibility/sccbeginbatch-function.md)