---
title: Función SccEndBatch | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ec549b5bb0a6c48946edf59f0ab1423cea0ac704
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="sccendbatch-function"></a>SccEndBatch (función)
Esta función finaliza un lote de las operaciones de control de código fuente. Estos lotes no pueden anidarse.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
SCCRTN SccEndBatch(void);  
```  
  
#### <a name="parameters"></a>Parámetros  
 Ninguno.  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|Lote de operaciones concluido correctamente.|  
|SCC_E_UNKNOWNERROR|Error no determinado.|  
  
## <a name="remarks"></a>Comentarios  
 Lotes de control de código fuente se usan para ejecutar las mismas operaciones de control de código fuente en varios proyectos o varios contextos. Lotes pueden usarse para eliminar cuadros de diálogo de redundancia de la experiencia del usuario durante una operación por lotes. El [SccBeginBatch](../extensibility/sccbeginbatch-function.md) y `SccEndBatch` función sirven como un par para indicar el principio y al final de una operación. No se pueden anidar.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccBeginBatch](../extensibility/sccbeginbatch-function.md)