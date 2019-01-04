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
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6b7fc5afbc5b1a084f0c5d84f5daf1cb7f257364
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53869432"
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
 [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccBeginBatch](../extensibility/sccbeginbatch-function.md)