---
title: Función SccCloseProject | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7d2364215f528f16d05ecf0c53b152f7334f4b4a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156140"
---
# <a name="scccloseproject-function"></a>SccCloseProject (Función)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esta función cierra un proyecto y marca el final de una sesión determinada.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
SCCRTN SccCloseProject (  
   LPVOID pvContext  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 pvContext  
 Estructura de contexto del complemento de control de código fuente.  
  
## <a name="return-value"></a>Valor devuelto  
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:  
  
|Value|Descripción|  
|-----------|-----------------|  
|SCC_OK|El proyecto se ha cerrado correctamente.|  
|SCC_E_PROJNOTOPEN|No hay ningún proyecto abierto actualmente.|  
|SCC_E_NOTAUTHORIZED|El usuario no tiene permiso para realizar esta operación.|  
|SCC_E_NONSPECIFICERROR|Error no específico.|  
  
## <a name="remarks"></a>Observaciones  
 Siempre se llama a [SccOpenProject](../extensibility/sccopenproject-function.md) antes de esta función. Una llamada a esta función va seguida de una llamada a la `SccOpenProject` función o a [SccUninitialize](../extensibility/sccuninitialize-function.md), que finaliza la conexión al sistema de control de código fuente por completo.  
  
## <a name="see-also"></a>Consulte también  
 [Funciones de la API del complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)
