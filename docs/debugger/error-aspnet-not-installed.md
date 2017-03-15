---
title: "Error: ASP.NET no est&#225; instalado | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.http_not_supported"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ASP.NET, mensajes de error de instalación"
  - "depurador, errores de aplicación Web"
  - "mensajes de error, ASP.NET"
  - "aplicaciones web, errores"
ms.assetid: 6286dd3d-3e2b-4edd-959d-81e0ed45500b
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Error: ASP.NET no est&#225; instalado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este error se produce si [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] no está correctamente instalado en el equipo en el que intenta depurar.  Esto puede significar que nunca se instaló [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] o que se instaló [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] antes que IIS.  
  
### Para reinstalar ASP.NET  
  
1.  Desde una ventana del símbolo del sistema, ejecute el siguiente comando:  
  
    ```  
    \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i  
    ```  
  
     donde *version* representa el número de la versión de .NET Framework instalada en el equipo, por ejemplo, v1.0.370.  Para determinar la versión de .NET Framework, observe el directorio `\WINDOWS\Microsoft.NET\Framework`.  
  
    > [!NOTE]
    >  En Windows Server 2003, puede instalar [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] mediante el subprograma **Agregar o quitar programas** del Panel de control.  
  
## Vea también  
 [Depurar las aplicaciones Web: errores y solución de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)