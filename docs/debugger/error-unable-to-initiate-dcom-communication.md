---
title: "Error: No se puede iniciar la comunicaci&#243;n con DCOM | Microsoft Docs"
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
  - "vs.debug.error.unmarshal_server_failed"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 2a7b27e6-2526-4f32-bc4d-eaee447f24ec
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Error: No se puede iniciar la comunicaci&#243;n con DCOM
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se ha producido un error de DCOM cuando el equipo local ha intentado comunicarse con el equipo remoto.  Esto se debe a la presencia de un firewall en el servidor remoto o a un incumplimiento de la autenticación de Windows en el equipo remoto.  
  
### Para corregir este error  
  
-   Si el equipo remoto tiene el Firewall de Windows habilitado, vea [Configurar las herramientas remotas en el dispositivo](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md) para obtener instrucciones sobre cómo configurar el firewall para la depuración local.  
  
-   Para restaurar la autenticación de Windows, reinicie ambos equipos.  Examine los registros de eventos en los equipos local y remoto para buscar errores Kerberos y póngase en contacto con los administradores de dominio para averiguar si existen problemas conocidos.  
  
## Vea también  
 [Depuración remota](../debugger/remote-debugging.md)