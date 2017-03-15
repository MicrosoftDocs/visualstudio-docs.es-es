---
title: "Error: Una comprobaci&#243;n de seguridad produjo un error porque el servicio de administraci&#243;n de IIS no respondi&#243; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.iis_not_responding"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurador, errores de aplicación Web"
ms.assetid: 6060e94e-71dc-49f2-bb59-2584216eadbf
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Error: Una comprobaci&#243;n de seguridad produjo un error porque el servicio de administraci&#243;n de IIS no respondi&#243;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este error se produce cuando el servicio de administración de IIS no responde.  En general, esto indica que hay un problema relacionado con la instalación de IIS.  Lo primero que debe hacer es comprobar que el servicio se está ejecutando mediante la herramienta **Servicios** de **Herramientas administrativas**.  
  
### Para corregir este error  
  
-   Reinstale IIS mediante el subprograma **Agregar o quitar programas** del Panel de control.  
  
-   O bien  
  
-   Quite IIS del equipo mediante el subprograma Agregar o quitar programas del Panel de control.  Si el problema persiste tras quitar IIS, compruebe el Registro y asegúrese de que la siguiente clave ya no existe:  
  
    ```  
    HKEY_CLASSES_ROOT\CLSID\{A9E69610-B80D-11D0-B9B9-00A0C922E750}  
    ```  
  
     O bien  
  
-   Deshabilite el servicio de administración de IIS mediante el subprograma Herramientas administrativas del Panel de control.  Esto deshabilitará IIS en el equipo.  
  
     Tras la conclusión de cualquiera de estos tres pasos, reinicie el equipo.  
  
     Para obtener más información, consulte la documentación de IIS.  
  
## Vea también  
 [Depurar las aplicaciones Web: errores y solución de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)