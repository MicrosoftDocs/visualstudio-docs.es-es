---
title: "SccGetEvents (funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccGetEvents"
helpviewer_keywords: 
  - "SccGetEvents (función)"
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# SccGetEvents (funci&#243;n)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta función recupera un evento de estado en cola.  
  
## Sintaxis  
  
```cpp#  
SCCRTN SccGetEvents (  
   LPVOID pvContext,  
   LPSTR  lpFileName,  
   LPLONG lpStatus,  
   LPLONG pnEventsRemaining  
);  
```  
  
#### Parámetros  
 pvContext  
 \[in\] La estructura de contexto complemento de control de código fuente.  
  
 lpFileName  
 \[entrada, salida\] Búfer en el complemento de control de código fuente coloca el nombre de archivo devuelto \(hasta caracteres \_MAX\_PATH\).  
  
 lpStatus  
 \[entrada, salida\] Devuelve el código de estado \(consulte [Código de estado de archivo](../extensibility/file-status-code-enumerator.md) posibles valores\).  
  
 pnEventsRemaining  
 \[entrada, salida\] Devuelve el número de entradas que quedan en la cola después de esta llamada. Si este número es grande, el llamador puede decidir llamar el [SccQueryInfo](../extensibility/sccqueryinfo-function.md) para obtener toda la información a la vez.  
  
## Valor devuelto  
 La implementación de complemento del control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC\_OK|Obtener los eventos se realizó correctamente.|  
|SCC\_E\_OPNOTSUPPORTED|No se admite esta función.|  
|SCC\_E\_NONSPECIFICERROR|Error no específico.|  
  
## Comentarios  
 Esta función se invoca durante el procesamiento de inactividad para ver si se han producido las actualizaciones de estado para los archivos bajo control de código fuente. El complemento de control de código fuente mantiene el estado de todos los archivos que conoce y siempre que un cambio de estado se indica mediante el complemento, el estado y el archivo asociado se almacenan en una cola. Cuando `SccGetEvents` se llama, la parte superior se recuperan y se devuelve el elemento de la cola. Esta función está limitada a devolver únicamente información previamente almacenado en caché y debe tener un procesamiento muy rápido \(es decir, sin leer del disco o pedir el sistema de control de código fuente estado\); de lo contrario, el rendimiento del IDE puede comenzar a degradar.  
  
 Si no hay ninguna actualización de estado al informe, el complemento de control de código fuente almacena una cadena vacía en el búfer señalado por `lpFileName`. De lo contrario, el complemento almacena el nombre de ruta de acceso completa del archivo que ha cambiado la información de estado y devuelve el código de estado apropiado \(uno de los valores que se detallan en [Código de estado de archivo](../extensibility/file-status-code-enumerator.md)\).  
  
## Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [Código de estado de archivo](../extensibility/file-status-code-enumerator.md)