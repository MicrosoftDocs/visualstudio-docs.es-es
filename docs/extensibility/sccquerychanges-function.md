---
title: "SccQueryChanges (funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccQueryChanges"
helpviewer_keywords: 
  - "SccQueryChanges (función)"
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# SccQueryChanges (funci&#243;n)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta función enumera una lista de archivos, que proporciona información sobre los cambios de nombre para cada archivo a través de una función de devolución de llamada especificada.  
  
## Sintaxis  
  
```cpp  
SCCRTN SccQueryChanges(  
   LPVOID           pContext,  
   LONG             nFiles,  
   LPCSTR*          lpFileNames,  
   QUERYCHANGESFUNC pfnCallback,  
   LPVOID           pvCallerData  
);  
```  
  
#### Parámetros  
 pContext  
 \[in\] El puntero de contexto de complemento de control de código fuente.  
  
 nFiles  
 \[in\] Número de archivos de `lpFileNames` matriz.  
  
 lpFileNames  
 \[in\] Matriz de nombres de archivo para obtener información acerca de.  
  
 pfnCallback  
 \[in\] Función de devolución de llamada para llamar para cada nombre de archivo en la lista \(consulte [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) para obtener más información\).  
  
 pvCallerData  
 \[in\] Valor que se pasa sin cambios a la función de devolución de llamada.  
  
## Valor devuelto  
 La implementación de complemento del control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC\_OK|El proceso de consulta que se completó correctamente.|  
|SCC\_E\_PROJNOTOPEN|No se ha abierto el proyecto en control de código fuente.|  
|SCC\_E\_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de origen, probablemente debido a problemas de red o de contención.|  
|SCC\_E\_NONSPECIFICERROR|Ocurrió un error no especificado o general.|  
  
## Comentarios  
 Son los cambios que se consulta para el espacio de nombres: en concreto, el cambio de nombre, agregar y quitar un archivo.  
  
## Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)   
 [Códigos de error](../extensibility/error-codes.md)