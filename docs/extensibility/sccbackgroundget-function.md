---
title: Función SccBackgroundGet | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccBackgroundGet
helpviewer_keywords:
- SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 77e70720c9a26710c6d659ebac5b842bef3757eb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="sccbackgroundget-function"></a>SccBackgroundGet (función)
Esta función recupera de control de código fuente cada de los archivos especificados sin interacción del usuario.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
SCCRTN SccBackgroundGet(  
   LPVOID  pContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LONG    dwFlags,  
   LONG    dwBackgroundOperationID  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 pContext  
 [in] El puntero de contexto de complemento de control de código fuente.  
  
 nFiles  
 [in] Número de archivos especificado en el `lpFileNames` matriz.  
  
 lpFileNames  
 [entrada, salida] Matriz de nombres de archivos que se va a recuperar.  
  
> [!NOTE]
>  Los nombres deben ser nombres de archivo local completo.  
  
 dwFlags  
 [in] Indicadores de comandos (`SCC_GET_ALL`, `SCC_GET_RECURSIVE`).  
  
 dwBackgroundOperationID  
 [in] Un valor único asociado a esta operación.  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|Operación se completó correctamente.|  
|SCC_E_BACKGROUNDGETINPROGRESS|La recuperación de un segundo plano ya está en curso (el complemento de control de código fuente debe devolver esto únicamente si no admite operaciones por lotes simultáneos).|  
|SCC_I_OPERATIONCANCELED|Se canceló la operación antes de completarse.|  
  
## <a name="remarks"></a>Comentarios  
 Esta función siempre se invoca en un subproceso diferente del que carga el complemento de control de código fuente. No se espera que esta función devuelva hasta que ha terminado; Sin embargo, se puede llamar varias veces con varias listas de archivos, todos al mismo tiempo.  
  
 El uso de la `dwFlags` argumento es el mismo que el [SccGet](../extensibility/sccget-function.md).  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGet](../extensibility/sccget-function.md)