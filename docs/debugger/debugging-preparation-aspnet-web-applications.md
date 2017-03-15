---
title: "Preparaci&#243;n de la depuraci&#243;n: aplicaciones Web ASP.NET | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "depurar [Visual Studio], aplicaciones web"
  - "depurar aplicaciones web ASP.NET"
ms.assetid: bcfb1080-98d1-42f9-96af-186fb14f232a
caps.latest.revision: 35
caps.handback.revision: 35
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Preparaci&#243;n de la depuraci&#243;n: aplicaciones Web ASP.NET
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La plantilla de sitio web de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]crea una aplicación de formularios Web Forms.  Cuando se crea un sitio Web usando esta plantilla, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] crea la configuración predeterminada para la depuración.  En el cuadro de diálogo **Propiedades del proyecto**, puede especificar que la página Web sea una página de inicio, si lo desea.  Al comenzar la depuración de un sitio web de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]con esta configuración predeterminada, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] inicia Internet Explorer y asocia el depurador al proceso de trabajo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] \(aspnet\_wp.exe o w3wp.exe\).  Para obtener más información, vea [Requisitos del sistema](../debugger/aspnet-debugging-system-requirements.md).  
  
### Para crear una aplicación de formularios Web Forms  
  
1.  En el menú **Archivo**, elija **Nuevo sitio Web**.  
  
2.  En el cuadro de diálogo **Nuevo sitio web**, seleccione **Sitio web** de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
3.  Haga clic en **Aceptar**.  
  
### Para depurar el formulario Web Forms  
  
1.  Establezca uno o varios puntos de interrupción en los controladores de funciones y eventos.  
  
     Para obtener más información, vea [Breakpoints and Tracepoints](http://msdn.microsoft.com/es-es/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
2.  Cuando se alcance un punto de interrupción, ejecute paso a paso el código en la función.  Fíjese en la ejecución del código hasta que aísle el problema.  
  
     Para obtener más información, vea [Stepping](http://msdn.microsoft.com/es-es/8791dac9-64d1-4bb9-b59e-8d59af1833f9) y [Depurar script y aplicaciones web](../debugger/debugging-web-applications-and-script.md).  
  
## Cambiar las configuraciones predeterminadas  
 Si desea cambiar las configuraciones predeterminadas Debug y Release creadas por [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], puede hacerlo.  Para obtener más información, vea [Cómo: Establecer configuraciones Debug y Release](../debugger/how-to-set-debug-and-release-configurations.md).  
  
#### Para cambiar la configuración Debug predeterminada  
  
1.  En el **Explorador de soluciones**, haga clic con el botón secundario del mouse en el sitio Web y seleccione **Páginas de propiedades** para abrir el cuadro de diálogo **Páginas de propiedades**.  
  
2.  Haga clic en **Opciones de inicio**.  
  
3.  Establezca **Acción de inicio** en la página web que debe mostrarse primero.  
  
4.  En **Depuradores**, asegúrese de que se ha seleccionado **Depuración ASP.NET**.  
  
     Para obtener más información, vea [Configuración de páginas de propiedades para proyectos web](../debugger/property-pages-settings-for-web-projects.md).  
  
## Vea también  
 [Preparación y configuración de la depuración](../debugger/debugger-settings-and-preparation.md)   
 [Conceptos básicos del depurador](../debugger/debugger-basics.md)   
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Depurar código administrado](../debugger/debugging-managed-code.md)