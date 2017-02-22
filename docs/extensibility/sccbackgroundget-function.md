---
title: "SccBackgroundGet (funci&#243;n) | Microsoft Docs"
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
  - "SccBackgroundGet"
helpviewer_keywords: 
  - "SccBackgroundGet (función)"
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# SccBackgroundGet (funci&#243;n)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta función recupera de control de código fuente cada de los archivos especificados sin interacción del usuario.  
  
## Sintaxis  
  
```cpp  
SCCRTN SccBackgroundGet(  
   LPVOID  pContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LONG    dwFlags,  
   LONG    dwBackgroundOperationID  
);  
```  
  
#### Parámetros  
 pContext  
 \[in\] El puntero de contexto de complemento de control de código fuente.  
  
 nFiles  
 \[in\] Número de archivos especificado en el `lpFileNames` matriz.  
  
 lpFileNames  
 \[entrada, salida\] Matriz de nombres de archivos que desea recuperar.  
  
> [!NOTE]
>  Los nombres deben ser nombres de archivo local completo.  
  
 dwFlags  
 \[in\] Indicadores de comandos \(`SCC_GET_ALL`, `SCC_GET_RECURSIVE`\).  
  
 dwBackgroundOperationID  
 \[in\] Un valor único asociado a esta operación.  
  
## Valor devuelto  
 La implementación de complemento del control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC\_OK|Operación se completó correctamente.|  
|SCC\_E\_BACKGROUNDGETINPROGRESS|Una recuperación de segundo plano ya está en curso \(el complemento de control de código fuente debe devolver esto únicamente si no admite operaciones por lotes simultáneos\).|  
|SCC\_I\_OPERATIONCANCELED|Se canceló la operación antes de completarse.|  
  
## Comentarios  
 Esta función siempre se invoca en un subproceso diferente del que carga el complemento de control de código fuente. Esta función no se espera que devuelva hasta que ha terminado; Sin embargo, se puede llamar varias veces con varias listas de archivos, todos al mismo tiempo.  
  
 El uso de la `dwFlags` argumento es el mismo que el [SccGet](../extensibility/sccget-function.md).  
  
## Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGet](../extensibility/sccget-function.md)