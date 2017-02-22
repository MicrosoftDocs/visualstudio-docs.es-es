---
title: "CvInitProvider (Funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkers/CvInitProvider"
helpviewer_keywords: 
  - "CvInitProvider (método)"
ms.assetid: ba1863ad-e35f-4d34-a2f2-5e68957d1915
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CvInitProvider (Funci&#243;n)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Inicializa el proveedor de marcadores.  Se tiene que llamar antes que cualquier otra función del visualizador de simultaneidad SDK.  
  
## Sintaxis  
  
```  
HRESULT CvInitProvider(  
   _In_ const GUID* pGuid,  
   _Out_ PCV_PROVIDER* ppProvider  
);  
```  
  
#### Parámetros  
 `pGuid`  
 Guía del proveedor.  No puede ser NULL.  
  
 `ppProvider`  
 Dirección de una variable de salida que almacenará el contexto de proveedor.  No puede ser NULL.  
  
## Valor devuelto  
 S\_OK cuando se inicializa el proveedor correctamente o código de error en caso de que se dé cualquier error.  Utilizar macros SUCCEEDED\/FAILED para comprobar si hay condición de error.  
  
## Requisitos  
 **Encabezado:** cvmarkers.h  
  
## Vea también  
 [Referencia de la biblioteca C\+\+](../profiling/cpp-library-reference.md)