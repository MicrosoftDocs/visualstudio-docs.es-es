---
title: "C&#243;mo: Habilitar la configuraci&#243;n de seguridad para aplicaciones ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "implementación ClickOnce, configuración de seguridad"
  - "seguridad [Visual Studio], aplicaciones ClickOnce"
  - "configuración de seguridad, implementación ClickOnce"
ms.assetid: 73cd3e9d-cd72-4ad2-8cae-94d6bb6b01e0
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# C&#243;mo: Habilitar la configuraci&#243;n de seguridad para aplicaciones ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se debe habilitar la seguridad de acceso del código para las aplicaciones ClickOnce con el fin de publicar la aplicación.  Esta acción se realiza automáticamente al publicar una aplicación mediante el Asistente para publicación.  
  
 En algunos casos, habilitar la seguridad de acceso del código puede influir en el rendimiento al compilar o depurar la aplicación; en estos casos, quizá desee deshabilitar temporalmente la configuración de seguridad.  
  
 La configuración de seguridad de ClickOnce se puede habilitar o deshabilitar en la página **Seguridad** del **Diseñador de proyectos**.  
  
### Para habilitar la configuración de seguridad de ClickOnce  
  
1.  Con un proyecto seleccionado en el **Explorador de soluciones**, en el menú **Proyecto** haga clic en **Propiedades**.  
  
2.  Haga clic en la ficha **Seguridad**.  
  
3.  Active la casilla **Habilitar configuración de seguridad de ClickOnce**.  
  
     Ahora puede personalizar la configuración de seguridad de la aplicación en la página Seguridad.  
  
    > [!NOTE]
    >  Esta casilla se activa automáticamente cada vez que la aplicación se publique con el **Asistente para publicación**.  
  
### Para deshabilitar la configuración de seguridad de ClickOnce  
  
1.  Con un proyecto seleccionado en el **Explorador de soluciones**, en el menú **Proyecto** haga clic en **Propiedades**.  
  
2.  Haga clic en la ficha **Seguridad**.  
  
3.  Desactive la casilla **Habilitar configuración de seguridad de ClickOnce**.  
  
     La aplicación se ejecutará con la configuración de seguridad Plena confianza; se pasará por alto la configuración de la página **Seguridad**.  
  
    > [!NOTE]
    >  Cada vez que se publique la aplicación en el Asistente para publicación, se activará esta casilla; debe volver a desactivarla después de cada publicación correcta.  
  
## Vea también  
 [Proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Seguridad de acceso del código para aplicaciones ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [Proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)