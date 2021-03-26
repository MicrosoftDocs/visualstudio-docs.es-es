---
description: Esta función inicia una secuencia por lotes de operaciones de control de código fuente.
title: Función SccBeginBatch | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5af4d8fb1d8524f16493603bb5d46ee4bdbd03ba
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060450"
---
# <a name="sccbeginbatch-function"></a>SccBeginBatch función)
Esta función inicia una secuencia por lotes de operaciones de control de código fuente. Se llamará a [SccEndBatch](../extensibility/sccendbatch-function.md) para finalizar el lote. Estos lotes no se pueden anidar.

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccBeginBatch(void);
```

### <a name="parameters"></a>Parámetros
 Ninguno.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|Se inició correctamente el lote de operaciones.|
|SCC_E_UNKNOWNERROR|Error no específico.|

## <a name="remarks"></a>Observaciones
 Los lotes de control de código fuente se utilizan para ejecutar las mismas operaciones en varios proyectos o en varios contextos. Los lotes se pueden usar para eliminar los cuadros de diálogo por proyecto redundantes de la experiencia del usuario durante una operación por lotes. La `SccBeginBatch` función y [SccEndBatch](../extensibility/sccendbatch-function.md) se utilizan como un par de funciones para indicar el principio y el final de una operación. No se pueden anidar. `SccBeginBatch` establece una marca que indica que una operación por lotes está en curso.

 Mientras una operación por lotes está en vigor, el complemento de control de código fuente debe presentar como máximo un cuadro de diálogo para cualquier pregunta al usuario y aplicar la respuesta desde ese cuadro de diálogo en todas las operaciones posteriores.

## <a name="see-also"></a>Consulte también
- [Funciones de la API del complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [SccEndBatch](../extensibility/sccendbatch-function.md)
