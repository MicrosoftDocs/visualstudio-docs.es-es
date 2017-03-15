---
title: "C&#243;mo: Deshabilitar la activaci&#243;n de direcciones URL de aplicaciones ClickOnce mediante el dise&#241;ador | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "implementación ClickOnce, activación de direcciones URL"
  - "disallowURLActivation"
  - "activación de direcciones URL, aplicaciones ClickOnce"
ms.assetid: a337a582-e67c-409a-b52e-607cd1a8fc57
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# C&#243;mo: Deshabilitar la activaci&#243;n de direcciones URL de aplicaciones ClickOnce mediante el dise&#241;ador
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Normalmente, una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] se iniciará automáticamente nada más instalarse desde un servidor web.  Por razones de seguridad, puede deshabilitar este comportamiento e indicar a los usuarios que, en lugar de ello, inicien la aplicación desde el menú **Inicio**.  En el siguiente procedimiento, se describe cómo deshabilitar la activación de direcciones URL.  
  
 Esta técnica sólo puede utilizarse con aplicaciones [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] que se hayan instalado en el equipo del usuario desde un servidor web.  No puede utilizarse con aplicaciones que sólo están disponibles en línea, ya que únicamente pueden iniciarse a través de su dirección URL.  Para obtener más información sobre la diferencia que existe entre las aplicaciones instaladas y las aplicaciones que sólo están disponibles en línea, vea [Elegir una estrategia de implementación de ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 Este procedimiento utiliza [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  También puede llevar a cabo esta tarea utilizando [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)].  Para obtener más información, vea [Cómo: Deshabilitar la activación de direcciones URL de aplicaciones ClickOnce](../deployment/how-to-disable-url-activation-of-clickonce-applications.md).  
  
## Procedimiento  
  
#### Para deshabilitar la activación de direcciones URL para la aplicación  
  
1.  En el **Explorador de soluciones**, haga clic con el botón secundario del mouse en el nombre del proyecto y, a continuación, haga clic en **Propiedades**.  
  
2.  En la página **Propiedades**, haga clic en la ficha **Publicar**.  
  
3.  Haga clic en **Opciones**.  
  
4.  Haga clic en **Manifiestos**.  
  
5.  Active la casilla denominada **Bloquear la aplicación para que no se active mediante una dirección URL**.  
  
6.  Implemente la aplicación.  
  
## Vea también  
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)