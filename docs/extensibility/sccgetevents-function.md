---
title: Función SccGetEvents | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccGetEvents
helpviewer_keywords:
- SccGetEvents function
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 79e517d87acd61eafcd2eb0a12f5a8978912db81
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="sccgetevents-function"></a>SccGetEvents (función)
Esta función recupera un evento de estado en cola.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
SCCRTN SccGetEvents (  
   LPVOID pvContext,  
   LPSTR  lpFileName,  
   LPLONG lpStatus,  
   LPLONG pnEventsRemaining  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 pvContext  
 [in] La estructura de contexto de complemento de control de código fuente.  
  
 lpFileName  
 [entrada, salida] Búfer en el complemento de control de código fuente coloca el nombre de archivo devuelto (máximo de caracteres _MAX_PATH).  
  
 lpStatus  
 [entrada, salida] Devuelve el código de estado (vea [código de estado de archivo](../extensibility/file-status-code-enumerator.md) para los valores posibles).  
  
 pnEventsRemaining  
 [entrada, salida] Devuelve el número de entradas que se deja en la cola después de esta llamada. Si este número es grande, el llamador puede decidir llamar el [SccQueryInfo](../extensibility/sccqueryinfo-function.md) para obtener toda la información a la vez.  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|Obtenga los eventos se realizó correctamente.|  
|SCC_E_OPNOTSUPPORTED|No se admite esta función.|  
|SCC_E_NONSPECIFICERROR|Error no determinado.|  
  
## <a name="remarks"></a>Comentarios  
 Esta función se invoca durante el procesamiento de inactividad para ver si se han producido las actualizaciones de estado para los archivos bajo control de código fuente. El complemento de control de código fuente mantiene el estado de todos los archivos que conoce y cada vez que un cambio de estado se indica mediante el complemento, el estado y el archivo asociado se almacenan en una cola. Cuando `SccGetEvents` se llama, la parte superior se recuperan y se devuelve el elemento de la cola. Esta función está restringida para devolver únicamente información previamente almacenado en caché y debe tener un procesamiento muy rápido (es decir, sin leer del disco o solicitar el sistema de control de código fuente de estado); en caso contrario, el rendimiento del IDE puede empezar a degradar.  
  
 Si no hay ninguna actualización de estado para el informe, el complemento de control de código fuente almacena una cadena vacía en el búfer señalado por `lpFileName`. En caso contrario, el complemento almacena el nombre de ruta de acceso completa del archivo para que la información de estado ha cambiado y devuelve el código de estado adecuado (uno de los valores que se detallan en [código de estado de archivo](../extensibility/file-status-code-enumerator.md)).  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [Código de estado de archivo](../extensibility/file-status-code-enumerator.md)