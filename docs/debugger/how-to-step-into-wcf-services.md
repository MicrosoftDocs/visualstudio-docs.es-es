---
title: "C&#243;mo: Ir a servicios WCF | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
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
ms.assetid: 9893ad01-54af-499f-85a6-9d1cfe6eb640
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo: Ir a servicios WCF
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], puede entrar en un servicio WCF.  Si el servicio WCF está en la misma solución de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que el cliente, puede establecer puntos de interrupción dentro del servicio WCF.  
  
 Para que funcione la entrada en un servicio, debe tener la depuración habilitada en el archivo app.config o Web.config.  Para obtener información sobre cómo habilitar la depuración y sobre las limitaciones de la entrada en los servicios WCF, vea [Limitaciones de la depuración de WCF](../debugger/limitations-on-wcf-debugging.md).  
  
### Para entrar en un servicio WCF  
  
1.  Cree una solución de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que contenga el cliente de WCF y los proyectos de servicio WCF.  
  
2.  En el Explorador de soluciones, haga clic con el botón secundario del mouse en el proyecto Cliente WCF y, a continuación, haga clic en **Establecer como proyecto de inicio**.  
  
3.  Habilite la depuración en el archivo app.config o web.config.  Para obtener más información, vea [Limitaciones de la depuración de WCF](../debugger/limitations-on-wcf-debugging.md).  
  
4.  Establezca un punto de interrupción en la ubicación del proyecto de cliente en la que desee iniciar la entrada.  Normalmente, esto suele ser justo antes de la llamada al servicio WCF.  
  
5.  Ejecute hasta el punto de interrupción y, a continuación, inicie la entrada.  El depurador entrará en el servicio automáticamente.  
  
## Vea también  
 [Depurar servicios WCF](../debugger/debugging-wcf-services.md)   
 [Limitaciones de la depuración de WCF](../debugger/limitations-on-wcf-debugging.md)   
 [Cómo: Depurar un servicio WCF independiente](../debugger/how-to-debug-a-self-hosted-wcf-service.md)