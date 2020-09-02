---
title: Función SccEndBatch | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 986056b1f5202c2fb94d27a8792ed3b0fe308944
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200142"
---
# <a name="sccendbatch-function"></a>SccEndBatch (Función)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esta función finaliza un lote de operaciones de control de código fuente. Estos lotes no se pueden anidar.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
SCCRTN SccEndBatch(void);  
```  
  
#### <a name="parameters"></a>Parámetros  
 Ninguno.  
  
## <a name="return-value"></a>Valor devuelto  
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:  
  
|Value|Descripción|  
|-----------|-----------------|  
|SCC_OK|Lote de operaciones concluido correctamente.|  
|SCC_E_UNKNOWNERROR|Error no específico.|  
  
## <a name="remarks"></a>Observaciones  
 Los lotes de control de código fuente se utilizan para ejecutar las mismas operaciones de control de código fuente en varios proyectos o en varios contextos. Los lotes se pueden usar para eliminar cuadros de diálogo redundantes de la experiencia del usuario durante una operación por lotes. [SccBeginBatch](../extensibility/sccbeginbatch-function.md) y la `SccEndBatch` función se usan como un par para indicar el principio y el final de una operación. No se pueden anidar.  
  
## <a name="see-also"></a>Consulte también  
 [Funciones de la API del complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccBeginBatch](../extensibility/sccbeginbatch-function.md)
