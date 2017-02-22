---
title: "SccGetUserOption (funci&#243;n) | Microsoft Docs"
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
  - "SccGetUserOption"
helpviewer_keywords: 
  - "SccGetUserOption (función)"
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# SccGetUserOption (funci&#243;n)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta función recupera una variedad de opciones específicas del usuario.  
  
## Sintaxis  
  
```cpp  
SCCRTN SccGetUserOption(  
   LPVOID pContext,  
   LONG nOption,  
   LPLONG lpVal  
);  
```  
  
#### Parámetros  
 pContext  
 \[in\] El puntero de contexto de complemento de control de código fuente.  
  
 nOption  
 \[in\] Opción para recuperar \(vea la sección Comentarios para las opciones posibles\).  
  
 lpVal  
 \[out\] Valor asociado a la opción.  
  
## Valor devuelto  
 La implementación de complemento del control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC\_OK|Opción se recuperó correctamente.|  
|SCC\_E\_OPNOTSUPPORTED|No se admite la opción.|  
|SCC\_E\_NONSPECIFICERROR|Se produjo un error no especificado.|  
  
## Comentarios  
 Este comando admite las siguientes opciones:  
  
|Opción de usuario|Descripción|  
|-----------------------|-----------------|  
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Determina si el usuario desea desproteger la versión local de archivos.`lpVal` se asigna `SCC_USEROPT_COLV_YES` \(usuario desea desproteger archivos locales\) o `SCC_USEROPT_COLV_NO`.|  
  
## Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [Códigos de error](../extensibility/error-codes.md)