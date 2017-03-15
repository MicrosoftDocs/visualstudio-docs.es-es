---
title: "ToggleHUD | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# ToggleHUD
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Alterna la activación o desactivación de la superposición del *HUD* \(pantalla de visualización frontal\) de diagnóstico de gráficos.  
  
## Sintaxis  
  
```cpp  
void ToggleHUD();  
```  
  
## Comentarios  
 El HUD de diagnósticos de gráficos se muestra en la esquina superior izquierda de la aplicación que se ejecuta bajo diagnóstico de gráficos.  Muestra información en tiempo de ejecución sobre la aplicación y sobre la captura de información de gráficos, y los mensajes que se agregan al llamar a la función miembro [AddMessage](../debugger/addmessage.md).  
  
 Para alternar el HUD, no tiene que estar capturando activamente información de gráficos; es decir, se puede alternar mediante una instancia de la clase `VsgDbg`, pero no se debe llamar primero a la función miembro [Init](../debugger/init.md).