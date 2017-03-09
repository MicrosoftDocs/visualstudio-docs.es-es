---
title: "VsgDbg::VsgDbg (Constructor) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# VsgDbg::VsgDbg (Constructor)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Construye una instancia de la clase `VsgDbg` con o sin preparar el componente de aplicación de diagnóstico de gráficos para capturar y registrar información de gráficos activamente de forma predeterminada, según el parámetro booleano especificado.  
  
## Sintaxis  
  
```cpp  
VsgDbg(  
  bDefaultInit  
);  
```  
  
#### Parámetros  
 `bDefaultInit`  
 Es `true` para especificar que el componente de aplicación de diagnóstico de gráficos debe estar preparado para capturar y grabar activamente información de gráficos; es `false` para especificar que la aplicación no se debe preparar para capturar y grabar activamente información de gráficos en este momento.  
  
## Comentarios  
 Cuando se llama al constructor con `bDefaultInit` establecido en `true`, el nombre del archivo de registro de gráficos está determinado por cómo se definen los símbolos de preprocesador `DONT_SAVE_VSGLOG_TO_TEMP` y `VSG_DEFAULT_RUN_FILENAME` antes de incluir `vsgcapture.h` en la aplicación.  
  
 Cuando se llama al constructor con `bDefaultInit` establecido en `false`, el componente de aplicación de diagnóstico de gráficos se puede preparar para capturar y grabar activamente información de gráficos en otro momento llamando a la función `Init`.  
  
## Vea también  
 [VsgDbg::~VsgDbg \(Destructor\)](../debugger/vsgdbg-tilde-vsgdbg-destructor.md)   
 [Init](../debugger/init.md)   
 [DONT\_SAVE\_VSGLOG\_TO\_TEMP](../debugger/dont-save-vsglog-to-temp.md)   
 [VSG\_DEFAULT\_RUN\_FILENAME](../debugger/vsg-default-run-filename.md)