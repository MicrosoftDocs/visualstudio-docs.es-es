---
title: "IActiveScriptProfilerCallback3::SetWebWorkerId (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 47744746-1276-441e-ab60-2a78f550e8e2
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IActiveScriptProfilerCallback3::SetWebWorkerId (M&#233;todo)
Notifica al generador de perfiles sobre el id. de trabajo para esta sesión.  Si la función no se ejecuta en el contexto de página, este método no se invoca.  El valor de los incrementos de `webWorkerId` por 1 para cada trabajo, comenzando en 1.  Los valores de identificador no van a ser estables más allá de una sesión, y corresponden sólo al orden en que se creó en los trabajadores.  
  
## Sintaxis  
  
```  
HRESULT SetWebWorkerId([in] DWORD webWorkerId);  
  
```  
  
#### Parámetros  
 `webWorkerId`  
 La identificación web worker  
  
## Valor devuelto  
 El valor devuelto de este método es omitido por el motor de script.