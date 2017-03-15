---
title: "C&#243;mo: Buscar el nombre de un proceso de ASP.NET | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
helpviewer_keywords: 
  - "depuración ASP.NET, proceso de ASP.NET"
  - "proceso de ASP.NET"
ms.assetid: 931a7597-b0f0-4a28-931d-46e63344435f
caps.latest.revision: 29
caps.handback.revision: 29
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo: Buscar el nombre de un proceso de ASP.NET
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Para establecer una asociación a una aplicación [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] que se está ejecutando, es preciso conocer el nombre del proceso [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
-   Si está ejecutando IIS 6.0 o IIS 7.0, el nombre es w3wp.exe.  
  
-   Si está ejecutando una versión anterior de IIS, el nombre es aspnet\_wp.exe.  
  
 Para las aplicaciones compiladas con [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)] o versiones posteriores, el código [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] puede residir en el sistema de archivos y ejecutarse en el servidor de pruebas WebDev.WebServer.exe.  En ese caso, debe establecer una asociación a WebDev.WebServer.exe en lugar de al proceso [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  Este escenario sólo se aplica a la depuración local.  
  
 Las aplicaciones ASP anteriores se ejecutan dentro del proceso de IIS inetinfo.exe cuando se ejecutan en proceso.  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos.  Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas**.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Para determinar si el código de proyecto reside en el sistema de archivos o en IIS  
  
1.  En Visual Studio, abra el **Explorador de soluciones** si aún no está abierto.  
  
2.  Seleccione el nodo superior que contiene el nombre de la aplicación.  
  
3.  Si el título de la ventana **Propiedades** contiene la ruta de acceso de un archivo, el código de la aplicación reside en el sistema de archivos.  
  
     En caso contrario, el título de la ventana **Propiedades** contendrá el nombre del sitio web.  
  
### Para determinar la versión de IIS en la que se está ejecutando la aplicación  
  
1.  Busque **Herramientas administrativas** y ejecútelo.  Dependiendo del sistema operativo, podría tratarse de un icono incluido en el **Panel de control** o de una entrada de menú que aparezca al hacer clic en **Inicio**.  
  
     En Windows XP, el **Panel de control** puede estar en Vista por categorías o Vista clásica.  En Vista por categorías, debe hacer clic en **Cambiar a Vista clásica** o en **Rendimiento y mantenimiento** para ver el icono **Herramientas administrativas**.  
  
2.  En **Herramientas administrativas**, ejecute Internet Information Services.  Aparecerá un cuadro de diálogo de MMC.  
  
3.  Si hay más de un equipo en el panel izquierdo, seleccione el equipo donde resida el código de la aplicación.  
  
4.  La versión de IIS está en la columna **Versión** situada en el panel derecho.  
  
## Vea también  
 [Requisitos previos para la depuración remota de aplicaciones web](../debugger/prerequistes-for-remote-debugging-web-applications.md)   
 [Requisitos del sistema](../debugger/aspnet-debugging-system-requirements.md)   
 [Preparar la depuración en ASP.NET](../debugger/preparing-to-debug-aspnet.md)   
 [Depurar script y aplicaciones web](../debugger/debugging-web-applications-and-script.md)