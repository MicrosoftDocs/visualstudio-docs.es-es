---
title: "Preparaci&#243;n de la depuraci&#243;n: aplicaciones de Windows Forms | Microsoft Docs"
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
  - "depurar [C#], aplicaciones Windows"
  - "depurar [J#], aplicaciones Windows"
  - "depurar [Visual Basic], aplicaciones Windows"
  - "depurar [Visual Studio], aplicaciones Windows"
  - "depurar aplicaciones para Windows"
  - "aplicaciones Windows, depurar"
ms.assetid: 7092ee7f-8378-4def-aef8-1695bd97cf14
caps.latest.revision: 28
caps.handback.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Preparaci&#243;n de la depuraci&#243;n: aplicaciones de Windows Forms
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La plantilla de proyecto de Windows Forms crea una aplicación de Windows Forms.  La depuración de este tipo de aplicación en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] es muy sencilla.  Para obtener más información, vea [Creating a Windows Application Project](http://msdn.microsoft.com/es-es/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
 Cuando se crea un proyecto de formularios Windows Forms con la plantilla de proyecto, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] crea automáticamente la configuración requerida para las versiones Debug y Release.  Si fuera necesario, puede cambiar esta configuración.  Esta configuración se puede cambiar en el cuadro de diálogo **Páginas de propiedades de \<nombre de proyecto\>** \(**Mi proyecto** en Visual Basic\).  
  
 Para obtener más información, vea [Valores de propiedad recomendados](../debugger/managed-debugging-recommended-property-settings.md).  
  
 En la tabla siguiente se muestra una configuración de propiedades adicional recomendada.  
  
### Propiedades de configuración de la ficha Depurar  
  
|**Nombre de la propiedad**|**Configuración**|  
|--------------------------------|-----------------------|  
|**Acción de inicio**|-   Establézcala en **Proyecto de inicio** en la mayoría de los casos.  Establézcala en **Programa externo de inicio** si desea iniciar otro ejecutable al comenzar la depuración \(normalmente para la depuración de archivos DLL\).|  
  
 Es posible depurar aplicaciones de Windows Forms dentro de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o mediante la asociación a una aplicación que ya está en ejecución.  Para obtener más información sobre asociación, vea [Crear asociaciones con procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
### Para depurar una aplicación de Windows Forms en C\#, F\# o Visual Basic  
  
1.  Abra el proyecto en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
2.  Cree puntos de interrupción según sea necesario.  
  
     Debido a que las aplicaciones de Windows Forms están orientadas a eventos, los puntos de interrupción entrarán en el código del controlador de eventos o en métodos llamados por el código del controlador de eventos.  Entre los eventos típicos en los cuales colocar puntos de interrupción se encuentran:  
  
    1.  Eventos asociados a un control, como Click, Enter, etc.  
  
    2.  Eventos asociados al inicio y apagado de una aplicación como Load, Activated, etc.  
  
    3.  Eventos de foco y validación.  
  
     Para obtener más información, vea [Creating Event Handlers in Windows Forms](../Topic/Creating%20Event%20Handlers%20in%20Windows%20Forms.md).  
  
3.  En el menú **Depurar**, haga clic en **Iniciar**.  
  
4.  Depure mediante las técnicas que se describen en [Conceptos básicos del depurador](../debugger/debugger-basics.md).  
  
## Vea también  
 [Depurar código administrado](../debugger/debugging-managed-code.md)   
 [Tipos de proyectos de C\#, F\# y Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Cómo: Establecer configuraciones Debug y Release](../debugger/how-to-set-debug-and-release-configurations.md)   
 [Configuración del proyecto para configuraciones de depuración en C\#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Configuración del proyecto para una configuración de depuración de Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Crear asociaciones con procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Windows Forms](../Topic/Windows%20Forms.md)