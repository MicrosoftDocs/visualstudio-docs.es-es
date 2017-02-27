---
title: "Introducci&#243;n a la extensibilidad del depurador | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Introducción, SDK de depuración"
  - "depuración [depuración SDK], introducción"
  - "SDK de depuración, introducción"
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Introducci&#243;n a la extensibilidad del depurador
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] proporciona información que debe tener que crear y personalizar los componentes del depurador utilizados a los programas de depuración en el entorno de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 la depuración de[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ha agregado mejoras derivadas de prueba de utilidad completa realizada en los depuradores anteriores de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  Puede utilizar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de depuración para recorrer una aplicación múltiples, o puede implementar la edición simultánea de variables mientras depura aplicaciones y soluciones multilenguaje.  
  
 la depuración de[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] está fuera del proceso ejecutado con el programa que se depura y por consiguiente menos intruso en el espacio del proceso de la aplicación.  Por tanto, es más fácil escribir componentes que interactúan con el depurador sin afectar al programa de depuración.  
  
 El mejor uso [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], debe estar familiarizado con el siguiente:  
  
-   el entorno de desarrollo integrado de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \(IDE\)  
  
-   el lenguaje de programación de C\+\+  
  
-   ATL COM  
  
## En esta sección  
 [Guía básica para ampliar el depurador](../../extensibility/debugger/roadmap-for-extending-the-debugger.md)  
 Describe el proceso de implementar la depuración en el producto, dependiendo del compilador y de su resultado.  
  
 [Componentes del depurador](../../extensibility/debugger/debugger-components.md)  
 Proporciona información general sobre [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de depuración componentes, que incluyen el motor de depuración \(DE\), el evaluador de \(EE\) expresiones, y el controlador de símbolos \(SH\).  
  
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)  
 Describe los conceptos arquitectónicos de depuración principal.  
  
 [Contextos de depurador](../../extensibility/debugger/debugger-contexts.md)  
 Explica cómo el motor de depuración \(DE\) funciona simultáneamente en el código, de la documentación, y de contextos de la evaluación de la expresión.  Describe, para cada uno de los tres contextos, location, de posición o de evaluación pertinentes al.  
  
 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)  
 Contiene vínculos a las diferentes tareas de depuración, como iniciar un programa y evaluación de expresiones.