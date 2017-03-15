---
title: "AddMessage | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# AddMessage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Agrega un mensaje personalizado al *HUD* \(pantalla de visualización frontal\) de diagnóstico de gráficos.  
  
## Sintaxis  
  
```cpp  
void AddMessage(  
  wchar_t const * szMessage  
);  
```  
  
#### Parámetros  
 `szMessage`  
 Mensaje que se va a agregar al HUD.  
  
## Comentarios  
 El HUD de diagnósticos de gráficos se muestra en la esquina superior izquierda de la aplicación que se ejecuta bajo diagnóstico de gráficos.  Muestra información en tiempo de ejecución sobre la aplicación y sobre la captura de información de gráficos, y los mensajes que se agregan al llamar a esta función.  
  
 Para agregar un mensaje al HUD, no tiene que estar capturando activamente información de gráficos; es decir, se puede agregar un mensaje mediante una instancia de la clase `VsgDbg`, pero no se debe llamar primero a la función miembro [Init](../debugger/init.md).  Los mensajes solo se muestran en el HUD, no se registran en el archivo de registro de gráficos.