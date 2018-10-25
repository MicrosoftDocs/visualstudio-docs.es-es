---
title: SccCloseProject (función) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: abb0cd825b6b09b5fdb7ad37f8066151ee42d3fc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49938102"
---
# <a name="scccloseproject-function"></a>SccCloseProject (función)
Esta función cierra un proyecto, marca el final de una sesión determinada.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
SCCRTN SccCloseProject (  
   LPVOID pvContext  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 pvContext  
 La estructura de contexto de complemento de control de origen.  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los valores siguientes:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|El proyecto se cerró correctamente.|  
|SCC_E_PROJNOTOPEN|No hay ningún proyecto está abierto actualmente.|  
|SCC_E_NOTAUTHORIZED|El usuario no puede realizar esta operación.|  
|SCC_E_NONSPECIFICERROR|Error no específico.|  
  
## <a name="remarks"></a>Comentarios  
 El [SccOpenProject](../extensibility/sccopenproject-function.md) siempre se llama antes de esta función. Una llamada a esta función, a continuación, seguida de una llamada a la `SccOpenProject` función o el [SccUninitialize](../extensibility/sccuninitialize-function.md), que finaliza la conexión con el sistema de control de código fuente completo.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)