---
title: "Error DCOM inesperado al intentar ponerse en contacto con el equipo remoto. Acceso denegado. | Microsoft Docs"
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
  - "vs.debug.remote.dcom_access_denied"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
helpviewer_keywords: 
  - "DCOM, errores de acceso"
  - "error de denegación de acceso remoto a DCOM"
  - "depuración remota, error en DCOM"
ms.assetid: 9d7dfc1b-9fe0-4f54-9c50-9c0e0f8358c5
caps.latest.revision: 27
caps.handback.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Error DCOM inesperado al intentar ponerse en contacto con el equipo remoto. Acceso denegado.
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La depuración remota utiliza DCOM para la comunicación entre el host y los equipos remotos en las siguientes situaciones:  
  
-   El depurador está establecido en el **Modo de compatibilidad nativa** o el **Modo de compatibilidad administrado** está activado en la página **Herramientas \/ Opciones \/ Depuración**  
  
-   Está depurando código C\+\+ \(C\+\+ \/ CLI\) administrado.  
  
-   En Visual Studio 2013, cuando se activa **Habilitar la opción Editar y continuar nativa** en la página **Herramientas \/ Opciones \/ Depuración**  
  
-   Algunos escenarios de depuración de terceros  
  
 Este error se produce cuando el proceso de Visual Studio no puede autenticarse \(o las credenciales proporcionadas se consideran insuficientes\) al proceso del depurador remoto sobre DCOM. Una o varias de las siguientes soluciones podrían resolver el problema:  
  
-   Desactive el **Modo de compatibilidad nativa** y el **Modo de compatibilidad administrado**.  
  
-   En Visual Studio 2013, desactive **Habilitar la opción Editar y continuar nativa**.  
  
-   Reinicie ambos equipos.  
  
-   Si la depuración remota requiere proporcionar las credenciales, active la opción para guardar las credenciales.  
  
## Vea también  
 [Errores de la depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Depuración remota](../debugger/remote-debugging.md)