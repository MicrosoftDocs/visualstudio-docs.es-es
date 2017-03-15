---
title: "UnInit | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# UnInit
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Finaliza el archivo de registro de gráficos, lo cierra y libera los recursos utilizados mientras la aplicación estaba grabando activamente información de gráficos.  
  
## Sintaxis  
  
```cpp  
void UnInit();  
```  
  
## Comentarios  
 Se llama automáticamente a `UnInit` cuando se destruye una instancia de la clase `VsgDbg`.  Si la instancia de `VsgDbg` no estaba grabando activamente información de gráficos, no tiene ningún efecto.  
  
 Después de que se haya llamado a `UnInit` en una instancia de la clase `VsgDbg`, se puede crear un nuevo archivo de registro de gráficos llamando a `Init` y finalizarlo llamando a `UnInit`.  Se puede repetir tantas veces como se desee utilizar la misma instancia de `VsgDbg` para crear varios archivos de registro de gráficos independientes.  
  
## Vea también  
 [Init](../debugger/init.md)