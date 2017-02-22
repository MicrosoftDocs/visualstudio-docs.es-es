---
title: "IDiaSession::put_loadAddress | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSession::put_loadAddress (método)"
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::put_loadAddress
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Establece la dirección de la carga del archivo ejecutable que corresponde a los símbolos en este almacén de símbolos.  
  
## Sintaxis  
  
```cpp#  
HRESULT put_loadAddress (   
   ULONGLONG NewVal  
);  
```  
  
#### Parámetros  
 `NewVal`  
 \[in\]  Dirección de la carga del archivo ejecutable.  
  
## Comentarios  
 Las propiedades de la dirección virtual \(VA\) de símbolo se calculan con el valor de este método.  No calculan las direcciones virtuales a menos que esta propiedad está establecida en cero.  
  
> [!NOTE]
>  Debe llamar a este método cuando se obtiene el objeto de [IDiaSession](../../debugger/debug-interface-access/idiasession.md) y antes de que comience con el objeto si necesita utilizar las propiedades virtuales de símbolos.  
  
## Vea también  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)