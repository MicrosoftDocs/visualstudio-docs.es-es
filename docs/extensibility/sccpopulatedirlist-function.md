---
title: "SccPopulateDirList (funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccPopulateDirList"
helpviewer_keywords: 
  - "SccPopulateDirList (función)"
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# SccPopulateDirList (funci&#243;n)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta función determina qué directorios y archivos \(opcionalmente\) se almacenan en el control de código fuente, dada una lista de directorios para examinar.  
  
## Sintaxis  
  
```cpp  
SCCRTN SccPopulateDirList(  
   LPVOID        pContext,  
   LONG          nDirs,  
   LPCSTR*       lpDirPaths,  
   POPDIRLISTFUNCpfnPopulate,  
   LPVOID        pvCallerData,  
   LONG          fOptions  
);  
```  
  
#### Parámetros  
 pContext  
 \[in\] El puntero de contexto de complemento de control de código fuente.  
  
 nDirs  
 \[in\] Número de rutas de acceso del directorio en el `lpDirPaths` matriz.  
  
 lpDirPaths  
 \[in\] Matriz de rutas de directorio para examinar.  
  
 pfnPopulate  
 \[in\] Función de devolución de llamada para llamar para cada nombre de archivo en la ruta de acceso de directorio y \(opcionalmente\) `lpDirPaths` \(consulte [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) para obtener más información\).  
  
 pvCallerData  
 \[in\] Valor que se pasa sin cambios a la función de devolución de llamada.  
  
 Opciones  
 \[in\] Una combinación de valores que controlan cómo se procesan los directorios \(consulte la sección "PopulateDirList marcas" de [Marcadores de bits que se utilizan los comandos específicos](../extensibility/bitflags-used-by-specific-commands.md) posibles valores\).  
  
## Valor devuelto  
 La implementación de complemento del control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC\_OK|La operación se completó correctamente.|  
|SCC\_E\_UNKNOWNERROR|Error.|  
  
## Comentarios  
 Sólo esos directorios y \(opcionalmente\) los nombres de archivo que están realmente en el repositorio de control de código fuente se pasan a la función de devolución de llamada.  
  
## Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [Marcadores de bits que se utilizan los comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)   
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)   
 [Códigos de error](../extensibility/error-codes.md)