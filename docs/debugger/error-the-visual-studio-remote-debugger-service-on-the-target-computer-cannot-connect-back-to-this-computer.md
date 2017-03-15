---
title: "Error: El servicio del depurador remoto de Visual Studio del equipo de destino no se puede volver a conectar a este equipo | Microsoft Docs"
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
  - "vs.debug.error.service_access_denied_oncallback"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 89ecf99d-66bf-4da0-a840-aa95b0be1702
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Error: El servicio del depurador remoto de Visual Studio del equipo de destino no se puede volver a conectar a este equipo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este error significa que el servicio del depurador remoto de Visual Studio se ejecuta con una cuenta de usuario que no se puede autenticar cuando intenta conectarse al equipo desde el que se realiza la depuración.  
  
 En la tabla siguiente se muestran las cuentas que pueden tener acceso al equipo:  
  
|||||  
|-|-|-|-|  
||Cuenta LocalSystem|Cuenta de dominio|Cuentas locales con el mismo nombre de usuario y contraseña en ambos equipos|  
|Ambos equipos en el mismo dominio|Sí|Sí|Sí|  
|Ambos equipos en dominios que tienen confianza bidireccional|No|No|Sí|  
|Uno o ambos equipos en un grupo de trabajo|No|No|Sí|  
|Equipos en dominios diferentes|No|No|Sí|  
  
 Además:  
  
-   La cuenta en la que se ejecuta el servicio del depurador remoto de Visual Studio debe ser una cuenta de administrador en el equipo remoto, de modo que éste pueda depurar cualquier proceso.  
  
-   La cuenta también necesita tener el privilegio `Log on as a service` en el equipo remoto que usa la herramienta administrativa **Directiva de seguridad local**.  
  
-   Si está usando un acceso de cuenta local al equipo, debe ejecutar el servicio del depurador remoto de Visual Studio con una cuenta local.  
  
### Para corregir este error  
  
1.  Asegúrese de que el servicio del depurador remoto de Visual Studio esté correctamente configurado en el equipo remoto.  Para obtener más información, vea [Configurar las herramientas remotas en el dispositivo](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md).  
  
2.  Ejecute el servicio del depurador remoto bajo una cuenta que puede tener acceso al equipo host del depurador, como se muestra en la tabla anterior.  
  
### Para agregar el privilegio "Iniciar sesión como servicio"  
  
1.  En el menú **Inicio**, elija **Panel de control**.  
  
2.  En Panel de control, elija **Vista clásica** si es necesario.  
  
3.  Haga doble clic en **Herramientas administrativas**.  
  
4.  En la ventana Herramientas administrativas, haga doble clic en **Directiva de seguridad local**.  
  
5.  En la ventana **Configuración de seguridad local**, expanda la carpeta **Directivas locales**.  
  
6.  Haga clic en **Asignación de derechos de usuario**.  
  
7.  En la columna **Directiva**, haga doble clic en **Iniciar sesión como servicio** para ver las asignaciones de directiva de grupo local en el cuadro de diálogo **Iniciar sesión como servicio**.  
  
8.  Para agregar nuevos usuarios, haga clic en el botón **Agregar usuario o grupo**.  
  
9. Cuando haya terminado de agregar usuarios, haga clic en **Aceptar**.  
  
### Para solucionar este error  
  
-   Ejecute el Monitor de depuración remota como aplicación en lugar de como servicio.  
  
## Vea también  
 [Errores de la depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Depuración remota](../debugger/remote-debugging.md)