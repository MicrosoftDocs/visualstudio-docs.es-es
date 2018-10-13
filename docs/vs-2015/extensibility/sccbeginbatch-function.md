---
title: SccBeginBatch (función) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 50fa6d14507a9af98d9ca303bc7bf9dbbf93ab6a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49283457"
---
# <a name="sccbeginbatch-function"></a>SccBeginBatch (Función)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esta función inicia una secuencia por lotes de operaciones de control de código fuente. El [SccEndBatch](../extensibility/sccendbatch-function.md) se llamará para finalizar el lote. Estos lotes no pueden anidarse.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
SCCRTN SccBeginBatch(void);  
```  
  
#### <a name="parameters"></a>Parámetros  
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
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccEndBatch](../extensibility/sccendbatch-function.md)

