---
title: SccCloseProject (función) | Microsoft Docs
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
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e4af9d73c19708369bcd4d341b573e421f8bc015
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51807567"
---
# <a name="scccloseproject-function"></a>SccCloseProject (Función)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esta función cierra un proyecto, marca el final de una sesión determinada.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
SCCRTN SccCloseProject (  
   LPVOID pvContext  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
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
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)

