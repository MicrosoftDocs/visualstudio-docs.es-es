---
title: SccGetEvents (función) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccGetEvents
helpviewer_keywords:
- SccGetEvents function
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d975570334aeab7c6709db92f3240a8e8d06b131
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "58988126"
---
# <a name="sccgetevents-function"></a>SccGetEvents (Función)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esta función recupera un evento de estado en cola.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
SCCRTN SccGetEvents (  
   LPVOID pvContext,  
   LPSTR  lpFileName,  
   LPLONG lpStatus,  
   LPLONG pnEventsRemaining  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 pvContext  
 [in] La estructura de contexto de complemento de control de origen.  
  
 lpFileName  
 [in, out] Búfer donde el complemento de control de código fuente coloca el nombre de archivo devuelto (máximo de caracteres _MAX_PATH).  
  
 lpStatus  
 [in, out] Devuelve el código de estado (consulte [código de estado de archivo](../extensibility/file-status-code-enumerator.md) posibles valores).  
  
 pnEventsRemaining  
 [in, out] Devuelve el número de entradas que quedan en la cola después de esta llamada. Si este número es grande, el llamador puede decidir llamar el [SccQueryInfo](../extensibility/sccqueryinfo-function.md) para obtener toda la información a la vez.  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los valores siguientes:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|Obtener eventos correctos.|  
|SCC_E_OPNOTSUPPORTED|No se admite esta función.|  
|SCC_E_NONSPECIFICERROR|Error no específico.|  
  
## <a name="remarks"></a>Comentarios  
 Esta función se invoca durante el procesamiento inactivo para ver si ha habido las actualizaciones de estado para los archivos bajo control de código fuente. El complemento de control de código fuente mantiene el estado de todos los archivos que conoce y cada vez que un cambio de estado se indica mediante el complemento, el estado y el archivo asociado se almacenan en una cola. Cuando `SccGetEvents` se llama, la parte superior se recupera el elemento de la cola y se devuelve. Esta función está restringida para devolver información previamente almacenado en caché única y debe tener un procesamiento muy rápido (es decir, no de lectura del disco o pide al sistema de control de origen para el estado); en caso contrario, el rendimiento del IDE puede comenzar a degradar.  
  
 Si no hay ninguna actualización de estado para el informe, el complemento de control de código fuente almacena una cadena vacía en el búfer señalado por `lpFileName`. En caso contrario, el complemento almacena el nombre de ruta de acceso completa del archivo para que la información de estado ha cambiado y devuelve el código de estado adecuado (uno de los valores que se detallan en [código de estado de archivo](../extensibility/file-status-code-enumerator.md)).  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [Código de estado de archivo](../extensibility/file-status-code-enumerator.md)
