---
title: "Error: No se puede conectar al equipo &lt;nombre&gt;. No se puede encontrar el equipo en la red. | Microsoft Docs"
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
  - "vs.debug.remote.dcom_disabled"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "DCOM, no se puede realizar la conexión (error)"
ms.assetid: b584b5db-ef52-45ed-8561-1314da3cc5b8
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Error: No se puede conectar al equipo &lt;nombre&gt;. No se puede encontrar el equipo en la red.
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este comportamiento se produce si se da una de las condiciones siguientes:  
  
-   La conexión al equipo remoto se interrumpe.  
  
-   La cuenta de usuario en el equipo remoto está deshabilitada.  
  
-   La contraseña en el equipo remoto ha expirado.  
  
### Para solucionar este comportamiento  
  
-   Asegúrese de que el equipo local y el equipo remoto están en la misma red.  Para ello, utilice el Explorador de Microsoft Windows \(o el Explorador de archivos\) para intentar tener acceso al equipo remoto.  
  
     — y —  
  
-   Asegúrese de que la cuenta de usuario que utiliza para conectarse al equipo remoto esté habilitada.  
  
     — y —  
  
-   Asegúrese de que la contraseña que utiliza para conectarse al equipo remoto sea válida y no haya expirado.  
  
## Vea también  
 [Configurar las herramientas remotas en el dispositivo](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)   
 [Preparación y configuración de la depuración](../debugger/debugger-settings-and-preparation.md)