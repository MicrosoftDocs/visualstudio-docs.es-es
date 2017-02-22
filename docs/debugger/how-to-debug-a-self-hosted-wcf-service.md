---
title: "C&#243;mo: Depurar un servicio WCF independiente | Microsoft Docs"
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
helpviewer_keywords: 
  - "depurar, WCF"
  - "WCF, depurar"
  - "WCF, servicio independiente"
ms.assetid: 288922be-ba3f-411e-af50-bba39c9529cc
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo: Depurar un servicio WCF independiente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un *servicio que se hospeda a sí mismo* es un servicio WCF que no se ejecuta dentro de IIS, el host de servicio WCF o el servidor de desarrollo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  La manera más fácil de depurar un WCF que se hospeda a sí mismo es configurar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para que inicie tanto el cliente como el servidor si elige **Iniciar depuración** en el menú **Depurar**.  
  
 Si el servicio WCF se hospeda a sí mismo dentro de un proceso que no se puede iniciar de esta manera, por ejemplo un servicio NT, no podrá utilizar este método.  En su lugar, puede realizar uno de los siguientes procedimientos:  
  
-   Asociar manualmente el depurador al proceso que hospeda.  Para obtener más información, vea [Crear asociaciones con procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
     O bien  
  
-   Empezar a depurar el cliente y, a continuación, entrar en una llamada al servicio.  Esto requiere habilitar la depuración en el archivo app.config.  Para obtener más información, vea [Limitaciones de la depuración de WCF](../debugger/limitations-on-wcf-debugging.md).  
  
### Para iniciar el cliente y el host desde Visual Studio  
  
1.  Cree una solución de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que contenga los proyectos de cliente y servidor.  
  
2.  Configure la solución para iniciar los procesos de cliente y servidor al elegir **Inicio** en el menú **Depurar**.  
  
    1.  En el **Explorador de soluciones**, haga clic con el botón secundario del mouse en el nombre de la solución.  
  
    2.  Haga clic en **Establecer proyectos de inicio**.  
  
    3.  En el cuadro de diálogo **Propiedades de la solución \<nombre\>**, seleccione **Proyectos de inicio múltiples**.  
  
    4.  En la cuadrícula **Proyectos de inicio múltiples**, en la línea que corresponde al proyecto de servidor, haga clic en **Acción** y elija **Inicio**.  
  
    5.  En la línea que corresponde al proyecto de cliente, haga clic en **Acción** y elija **Inicio**.  
  
    6.  Haga clic en **Aceptar**.  
  
## Vea también  
 [Depurar servicios WCF](../debugger/debugging-wcf-services.md)   
 [Limitaciones de la depuración de WCF](../debugger/limitations-on-wcf-debugging.md)   
 [Cómo: Ir a servicios WCF](../debugger/how-to-step-into-wcf-services.md)