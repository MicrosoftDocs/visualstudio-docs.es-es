---
title: "CvIsEnabled (Funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkers/CvIsEnabledEx"
  - "cvmarkers/CvIsEnabled"
helpviewer_keywords: 
  - "CvIsEnabled (método)"
  - "CvIsEnabledEx (método)"
ms.assetid: 2e4fea6d-758d-4150-8744-6102a1d58c1c
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# CvIsEnabled (Funci&#243;n)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Determina si alguna sesión ha habilitado el proveedor ETW especificado.  
  
## Sintaxis  
  
```  
HRESULT CvIsEnabled(  
   _In_ PCV_PROVIDER pProvider  
);  
HRESULT CvIsEnabledEx(  
   _In_ PCV_PROVIDER pProvider,  
   _In_ CV_IMPORTANCE level,  
   _In_ int category  
);  
```  
  
#### Parámetros  
 `category`  
 Categoría.  
  
 `level`  
 Nivel de importancia.  
  
 `pProvider`  
 Objeto de proveedor válido.  No puede ser NULL.  
  
## Valor devuelto  
 S\_OK si el proveedor está habilitado actualmente.  S\_FALSE si el proveedor está deshabilitado actualmente.  Código de error en caso de que hubiera cualquier error.  Utilice la macro FAILED para comprobar la condición del error y después comprobar S\_OK\/S\_FALSE.  
  
## Requisitos  
 **Encabezado:** cvmarkers.h  
  
## Vea también  
 [Referencia de la biblioteca C\+\+](../profiling/cpp-library-reference.md)