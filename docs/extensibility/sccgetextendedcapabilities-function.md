---
title: "SccGetExtendedCapabilities (funci&#243;n) | Microsoft Docs"
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
  - "SccGetExtendedCapabilities"
helpviewer_keywords: 
  - "SccGetExtendedCapabilities (función)"
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# SccGetExtendedCapabilities (funci&#243;n)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta función devuelve capacidades adicionales compatibles con el complemento de control de código fuente.  
  
## Sintaxis  
  
```cpp  
SCCRTN SccGetExtendedCapabilities(  
   LPVOID pContext,  
   LONG lSccExCaps,   LPBOOL pbSupported  
);  
```  
  
#### Parámetros  
 pContext  
 \[in\] El puntero de contexto de complemento de control de código fuente.  
  
 lSccExCaps  
 \[in\] Un indicador que especifica una funcionalidad extendida para el que se va a probar \(vea la tabla de código de capacidad total de [Marcadores de capacidad](../extensibility/capability-flags.md) para las marcas posibles\).  
  
 pbSupported  
 \[out\] Devuelve un valor no es cero \(`TRUE`\) si se admite la capacidad especificada; en caso contrario, devuelve cero \(`FALSE`\).  
  
## Valor devuelto  
 La implementación de complemento del control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC\_OK|La operación de capacidad get finalizada correctamente.|  
|SCC\_E\_UNKNOWNERROR<br /><br /> SCC\_E\_NONSPECIFICERROR|Error desconocido o no especificado.|  
  
## Comentarios  
 Este método se llama a petición; es decir, cuando se necesita una capacidad ser probado, se llama a este método para determinar si el que se admite la capacidad. Se especifica solo un marcador a la vez.  
  
## Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [Códigos de error](../extensibility/error-codes.md)   
 [Marcadores de capacidad](../extensibility/capability-flags.md)