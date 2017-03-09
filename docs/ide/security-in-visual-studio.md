---
title: "Seguridad en Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "seguridad de acceso del código, errores de programación"
  - "seguridad [.NET Framework], acerca de la seguridad"
ms.assetid: 318c34ce-f643-468c-83a1-843196f5d845
caps.latest.revision: 20
caps.handback.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Seguridad en Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Las consideraciones sobre seguridad se deben aplicar a todo el desarrollo de la aplicación, desde el diseño hasta la implementación.  Comience ejecutando Visual Studio de la forma más segura posible.  Vea [Permisos de usuario](../ide/user-permissions-and-visual-studio.md).  
  
 Para desarrollar de forma eficaz aplicaciones seguras, es preciso tener unos conocimientos básicos sobre los conceptos y las características de seguridad de las plataformas para las que se desarrolla.  También es necesario que conozca las técnicas de codificación segura.  
  
## Conceptos de seguridad  
 [Security](../Topic/Security%20in%20the%20.NET%20Framework.md)  
 Describe la seguridad de acceso del código de .NET Framework, la seguridad basada en roles, la directiva de seguridad y las herramientas de seguridad.  
  
 [Proteger el código con diez consejos de seguridad que todo desarrollador debe conocer](http://go.microsoft.com/fwlink/?LinkId=72877)  
 Describe los problemas más importantes que debería tener en cuenta para no poner en peligro los datos ni el sistema.  
  
## Codificación de seguridad  
 La mayoría de los errores de codificación que tienen como resultado la aparición de puntos vulnerables de seguridad se producen porque los programadores no hacen suposiciones válidas cuando trabajan con los datos que proporciona el usuario o porque no acaban de entender la plataforma para la que están desarrollando.  
  
 [Secure Coding Guidelines](../Topic/Secure%20Coding%20Guidelines.md)  
 Proporciona instrucciones para clasificar sus componentes y tratar los problemas de seguridad.  
  
 [Procedimientos recomendados](/visual-cpp/top/security-best-practices-for-cpp)  
 Explica las saturaciones del búfer e incluye una descripción completa de la característica de comprobación de seguridad de Microsoft Visual C\+\+ que proporciona el marcador en tiempo de compilación \/GS.