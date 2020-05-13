---
title: Función SccBeginBatch ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6c7982d8c8c0d71f8c79e9b808be5453d384882d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701198"
---
# <a name="sccbeginbatch-function"></a>Función SccBeginBatch
Esta función inicia una secuencia por lotes de operaciones de control de código fuente. El [SccEndBatch](../extensibility/sccendbatch-function.md) se llamará para finalizar el lote. Es posible que estos lotes no estén anidados.

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
|SCC_OK|Lote de operaciones comenzó con éxito.|
|SCC_E_UNKNOWNERROR|Fallo inespecífico.|

## <a name="remarks"></a>Observaciones
 Los lotes de control de código fuente se usan para ejecutar las mismas operaciones en varios proyectos o varios contextos. Los lotes se pueden usar para eliminar cuadros de diálogo redundantes por proyecto de la experiencia del usuario durante una operación por lotes. La `SccBeginBatch` función y [SccEndBatch](../extensibility/sccendbatch-function.md) se utilizan como un par de funciones para indicar el principio y el final de una operación. No se pueden anidar. `SccBeginBatch`establece una marca que indica que una operación por lotes está en curso.

 Mientras una operación por lotes está en vigor, el complemento de control de código fuente debe presentar como máximo un cuadro de diálogo para cualquier pregunta al usuario y aplicar la respuesta de ese cuadro de diálogo en todas las operaciones posteriores.

## <a name="see-also"></a>Vea también
- [Funciones de API de plug-in de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [SccEndBatch](../extensibility/sccendbatch-function.md)
