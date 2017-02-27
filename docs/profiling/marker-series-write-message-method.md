---
title: "marker_series::write_message (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkersobj/Concurrency::diagnostic::marker_series::write_message"
helpviewer_keywords: 
  - "Concurrency::diagnostic::marker_series::write_message (método)"
ms.assetid: 546121bc-67e0-4a5a-a456-12bd78fd6de2
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# marker_series::write_message (M&#233;todo)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Escribe un mensaje en el archivo de seguimiento del Visualizador de simultaneidad.  
  
## Sintaxis  
  
```  
void write_message(  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_message(  
   marker_importance _Importance,  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_message(  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_message(  
   marker_importance _Importance,  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
```  
  
#### Parámetros  
 `_Format`  
 Una cadena de formato compuesto que contiene el texto mezclado con cero o más elementos de formato, que se corresponden con los objetos de la lista de argumentos.  
  
 `_Importance`  
 Nivel de importancia.  
  
 `_Category`  
 Nivel Category.Importance.  
  
## Requisitos  
 **Encabezado:** cvmarkersobj.h  
  
 **Espacio de nombres:** Concurrency::diagnostico  
  
## Vea también  
 [marker\_series \(Clase\)](../profiling/marker-series-class.md)