---
title: "SccUninitialize (funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccUninitialize"
helpviewer_keywords: 
  - "SccUninitialize (función)"
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# SccUninitialize (funci&#243;n)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta función limpia las asignaciones o conexiones abiertas creadas por una llamada anterior a la [SccInitialize](../extensibility/sccinitialize-function.md) en preparación para cerrar el complemento de control de código fuente.  
  
## Sintaxis  
  
```cpp#  
SCCRTN SccUninitialize (  
   LPVOID pvContext  
);  
```  
  
#### Parámetros  
 pvContext  
 \[in\] El puntero a la estructura de contexto complemento de control de código fuente creado en el [SccInitialize](../extensibility/sccinitialize-function.md).  
  
## Valor devuelto  
 La implementación de complemento del control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC\_OK|La limpieza finalizada correctamente.|  
  
## Comentarios  
 El complemento de control de código fuente es responsable de preparación para cerrar y para liberar memoria que ha asignado el complemento de la estructura de contexto. La función se llama una vez para cada instancia concreta de un complemento. Una llamada a la [SccInitialize](../extensibility/sccinitialize-function.md) precede a esta llamada. No hay proyectos todavía pueden estar abiertos en el momento de la llamada a `SccUninitialize`.  
  
## Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)