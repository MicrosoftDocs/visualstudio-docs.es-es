---
title: "Error: El sitio utiliza una direcci&#243;n IP | Microsoft Docs"
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
  - "vs.debug.error.webdbg_siteusesipaddress"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurador, errores de aplicación Web"
ms.assetid: b2b8ddc8-746d-46e3-87a6-b956b1ee048d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Error: El sitio utiliza una direcci&#243;n IP
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este error se produce cuando el depurador intenta asociarse automáticamente a una aplicación Web que utilice una dirección IP.  Esto ocurre si se cambia **Identificación del sitio Web** a **Usar una dirección IP específica** en IIS.  
  
 Para que funcione la asociación automática, es preciso crear el proyecto con la dirección IP específica en lugar de hacerlo simplemente con el nombre del equipo.  De lo contrario, el depurador cambiará el nombre de equipo a localhost, lo que generará un error al enviar el verbo de depuración a IIS.  
  
### Para corregir este error  
  
1.  Utilice la asociación manual \(en el menú Depurar, elija **Asociar al proceso**\).  
  
     — o bien —  
  
2.  Cambie el valor de configuración de **Identificación del sitio Web de IIS**.  
  
## Vea también  
 [Depurar las aplicaciones Web: errores y solución de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)