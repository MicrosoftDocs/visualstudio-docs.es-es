---
title: "SccGetVersion (funci&#243;n) | Microsoft Docs"
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
  - "SccGetVersion"
helpviewer_keywords: 
  - "SccGetVersion (función)"
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# SccGetVersion (funci&#243;n)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta función obtiene el número de versión de la API de complementos de Control de código fuente compatibles con el complemento de control de código fuente.  
  
## Sintaxis  
  
```cpp#  
LONG SccGetVersion(void);  
```  
  
#### Parámetros  
 Ninguno.  
  
## Valor devuelto  
 A `LONG` tipo de datos que contiene el número de versión de la API de complementos de Control de código fuente compatibles:  
  
|WORD|Descripción|  
|----------|-----------------|  
|HIWORD|Versión principal|  
|LOWORD|Versión secundaria|  
  
## Comentarios  
 Por ejemplo, si un complemento de control de código fuente es compatible con la versión 1.3 de la API de complementos de Control de código fuente, esta función devolvería 0 x 0103.  
  
## Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)