---
title: SccBeginBatch (función) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c2e0ae1dd4d01018d9637e5722d8079222afbf3c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53869131"
---
# <a name="sccbeginbatch-function"></a>SccBeginBatch (función)
Esta función inicia una secuencia por lotes de operaciones de control de código fuente. El [SccEndBatch](../extensibility/sccendbatch-function.md) se llamará para finalizar el lote. Estos lotes no pueden anidarse.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
SCCRTN SccBeginBatch(void);  
```  
  
### <a name="parameters"></a>Parámetros  
 Ninguno.  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los valores siguientes:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|Lote de operaciones se inició correctamente.|  
|SCC_E_UNKNOWNERROR|Error no específico.|  
  
## <a name="remarks"></a>Comentarios  
 Los lotes de control de código fuente se usan para ejecutar las mismas operaciones en varios proyectos o varios contextos. Los lotes pueden usarse para eliminar cuadros de diálogo por proyecto redundantes de la experiencia del usuario durante una operación por lotes. El `SccBeginBatch` función y el [SccEndBatch](../extensibility/sccendbatch-function.md) se usan como un par de funciones para indicar el principio y al final de una operación. No se pueden anidar. `SccBeginBatch` establece una marca que indica que una operación por lotes está en curso.  
  
 Mientras una operación por lotes está vigente, el complemento de control de origen debe presentar como máximo un cuadro de diálogo para cualquier pregunta al usuario y la respuesta de ese cuadro de diálogo se aplican en todas las operaciones subsiguientes.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccEndBatch](../extensibility/sccendbatch-function.md)