---
title: "Error: la m&#225;quina remota no aparece en el cuadro de di&#225;logo Conexiones remotas | Microsoft Docs"
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
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 5fd98a5b-2cf3-4438-8b0f-6f1a742a62ce
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Error: la m&#225;quina remota no aparece en el cuadro de di&#225;logo Conexiones remotas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si el equipo remoto no aparece en el cuadro de diálogo Conexiones remotas, compruebe las siguientes causas comunes.  
  
 Si usa el modo de compatibilidad administrada, vea la documentación de Visual Studio 2010: [Solución de problemas de depuración remota \- Visual Studio 2010](https://msdn.microsoft.com/en-us/library/2ys11ead\(v=vs.100\).aspx) .  
  
### Causas comunes de este error  
  
-   El equipo remoto se está ejecutando en una máquina que se encuentra en una subred diferente. Para solucionar este problema, escriba manualmente la dirección IP o el nombre del equipo en el cuadro de diálogo Calificador  
  
-   El depurador remoto no se está ejecutando en la máquina remota. Para solucionar este problema, inicie al depurador remoto.  
  
-   El firewall está bloqueando la comunicación entre Visual Studio y la máquina remota. Para solucionar este problema, configure el firewall para permitir la comunicación entre Visual Studio y el depurador remoto \(msvsmon\).  
  
-   El software antivirus está bloqueando la comunicación entre Visual Studio y la máquina remota. Para solucionar este problema, configure el software antivirus para permitir la comunicación entre Visual Studio y el depurador remoto \(msvsmon\).  
  
## Vea también  
 [Configurar las herramientas remotas en el dispositivo](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)