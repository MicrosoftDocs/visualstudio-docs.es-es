---
title: "Error: IIS ha interrumpido el proceso de trabajo del sitio web | Microsoft Docs"
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
  - "vs.debug.error.web_server_process_terminated"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 5707b972-71a6-4cc6-ab99-c7c00ca8628c
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Error: IIS ha interrumpido el proceso de trabajo del sitio web
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El depurador detuvo la ejecución del código en el sitio web.  Esto hizo que Internet Information Services \(IIS\) creyera que el proceso de trabajo había dejado de responder.  Por consiguiente, IIS finalizaron el proceso de trabajo.  
  
 Para seguir depurando, debe configurar IIS para permitir que continúe el proceso de trabajo.  Este mensaje de error no aparece con las versiones de IIS anteriores a IIS 7.  
  
### Para configurar IIS 7 de manera que el proceso de trabajo pueda continuar  
  
1.  Abra la ventana **Herramientas administrativas**.  
  
    1.  Haga clic en **Inicio** y, a continuación, elija **Panel de control**.  
  
    2.  En el **Panel de control**, elija **Cambiar a Vista clásica** si es necesario y, a continuación, haga doble clic en **Herramientas administrativas**.  
  
2.  En la ventana **Herramientas administrativas**, haga doble clic en **Administrador de Internet Information Services \(IIS\)**.  
  
     Se abrirá el Administrador de IIS.  
  
3.  En el panel **Conexiones**, expanda el nodo \<nombre del equipo\> si es necesario.  
  
4.  En el nodo \<nombre del equipo\>, haga clic en **Grupos de aplicaciones**.  
  
5.  En la lista **Grupos de aplicaciones**, haga clic con el botón secundario en el nombre del grupo en el que se ejecuta la aplicación y, a continuación, haga clic en **Configuración avanzada**.  
  
6.  En el cuadro de diálogo **Configuración avanzada**, busque la sección **Modelo de proceso** y realice una de las acciones siguientes:  
  
    -   Establezca **Ping habilitado** en **False**.  
  
    -   Establezca **Tiempo máximo de respuesta de ping** en un valor mayor de 90 segundos.  
  
     Si establece **Ping habilitado** en **False**, IIS dejará de comprobar si el proceso de trabajo todavía se está ejecutando y lo mantendrá activo hasta que detenga el proceso depurado.  Establecer **Tiempo máximo de respuesta de ping** en un valor grande permite a IIS seguir supervisando el proceso de trabajo.  
  
7.  Haga clic en **Aceptar** para cerrar el cuadro de diálogo **Configuración avanzada**.  
  
8.  Cierre el Administrador de IIS y la ventana **Herramientas administrativas**.  
  
## Vea también  
 [Errores de la depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)