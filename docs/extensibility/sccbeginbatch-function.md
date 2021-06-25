---
description: Esta función inicia una secuencia por lotes de operaciones de control de código fuente.
title: SccBeginBatch (Función) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 08b9199b98e566a71bfeb95124ebd85781e69950
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904765"
---
# <a name="sccbeginbatch-function"></a>Función SccBeginBatch
Esta función inicia una secuencia por lotes de operaciones de control de código fuente. Se [llamará a SccEndBatch](../extensibility/sccendbatch-function.md) para finalizar el lote. Es posible que estos lotes no se anidan.

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccBeginBatch(void);
```

### <a name="parameters"></a>Parámetros
 Ninguno.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los valores siguientes:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|Lote de operaciones que se iniciaron correctamente.|
|SCC_E_UNKNOWNERROR|Error no específico.|

## <a name="remarks"></a>Observaciones
 Los lotes de control de código fuente se usan para ejecutar las mismas operaciones en varios proyectos o en varios contextos. Los lotes se pueden usar para eliminar los cuadros de diálogo redundantes por proyecto de la experiencia del usuario durante una operación por lotes. La `SccBeginBatch` función y [SccEndBatch](../extensibility/sccendbatch-function.md) se usan como un par de funciones para indicar el principio y el final de una operación. No se pueden anidar. `SccBeginBatch` establece una marca que indica que una operación por lotes está en curso.

 Mientras una operación por lotes está en vigor, el complemento de control de código fuente debe presentar como máximo un cuadro de diálogo para cualquier pregunta al usuario y aplicar la respuesta de ese cuadro de diálogo en todas las operaciones posteriores.

## <a name="see-also"></a>Consulta también
- [Funciones de API del complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [SccEndBatch](../extensibility/sccendbatch-function.md)
