---
title: "C&#243;mo: Deshabilitar la activaci&#243;n de direcciones URL de aplicaciones ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
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
  - "disallowUrlActivation"
  - "activación de direcciones URL, aplicaciones ClickOnce"
ms.assetid: db31a16b-960f-4264-91d7-c7c40f876068
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# C&#243;mo: Deshabilitar la activaci&#243;n de direcciones URL de aplicaciones ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Normalmente, una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] se inicia automáticamente después de que se instale desde un servidor web.  Por motivos de seguridad, puede deshabilitar este comportamiento e indicar a los usuarios que, en su lugar, inicien la aplicación desde el menú **Inicio**.  En el procedimiento siguiente, se describe cómo deshabilitar la activación de URL.  
  
 Esta técnica se puede utilizar solo para las aplicaciones [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] instaladas en el equipo del usuario desde un servidor web.  No se puede utilizar para aplicaciones solo en línea, que se pueden iniciar utilizando su dirección URL.  Para obtener más información acerca de la diferencia entre las aplicaciones solo en línea e instaladas, consulte [Elegir una estrategia de implementación de ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 Este procedimiento utiliza la herramienta [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] MageUI.exe.  Para obtener más información acerca de esta herramienta, consulte [MageUI.exe \(Manifest Generation and Editing Tool, Graphical Client\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md).  También puede realizar este procedimiento mediante [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Procedimiento  
  
#### Deshabilitar la activación de direcciones URL para la aplicación  
  
1.  Abra el manifiesto de implementación en MageUI.exe.  Si aún no ha creado uno, siga los pasos de [Tutorial: Implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
2.  Seleccione la pestaña **Opciones de implementación**.  
  
3.  Desactive la casilla de verificación **Ejecutar automáticamente la aplicación después de instalarla**.  
  
4.  Guarde y firme el manifiesto.  
  
## Vea también  
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)