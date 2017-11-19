---
title: "Función SccBeginBatch | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccBeginBatch
helpviewer_keywords: SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0e18eedcab133329f10064ef3dd6486beb2e1596
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="sccbeginbatch-function"></a>SccBeginBatch (función)
Esta función inicia una secuencia por lotes de las operaciones de control de código fuente. El [SccEndBatch](../extensibility/sccendbatch-function.md) se llamará para finalizar el lote. Estos lotes no pueden anidarse.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
SCCRTN SccBeginBatch(void);  
```  
  
#### <a name="parameters"></a>Parámetros  
 Ninguno.  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|Lote de operaciones se inició correctamente.|  
|SCC_E_UNKNOWNERROR|Error no determinado.|  
  
## <a name="remarks"></a>Comentarios  
 Lotes de control de código fuente se usan para ejecutar las mismas operaciones en varios proyectos o varios contextos. Lotes pueden usarse para eliminar cuadros de diálogo de proyecto por redundancia de la experiencia del usuario durante una operación por lotes. El `SccBeginBatch` función y la [SccEndBatch](../extensibility/sccendbatch-function.md) se usan como un par de funciones para indicar el principio y al final de una operación. No se pueden anidar. `SccBeginBatch`establece una marca que indica que una operación por lotes está en curso.  
  
 Mientras una operación por lotes está en vigor, el complemento de control de código fuente debe presentar a lo sumo un cuadro de diálogo para cualquier pregunta al usuario y la respuesta en ese cuadro de diálogo se aplican en todas las operaciones subsiguientes.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccEndBatch](../extensibility/sccendbatch-function.md)