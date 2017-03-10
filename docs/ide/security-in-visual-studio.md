---
title: Seguridad en Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code access security, coding errors
- security [.NET Framework], about security
ms.assetid: 318c34ce-f643-468c-83a1-843196f5d845
caps.latest.revision: 20
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 8e34062596ab2f87ae97934b89b4c292e8f28f32
ms.lasthandoff: 02/22/2017

---
# <a name="security-in-visual-studio"></a>Seguridad en Visual Studio
Las consideraciones sobre seguridad se deben aplicar a todo el desarrollo de la aplicación, desde el diseño hasta la implementación. Comience ejecutando Visual Studio de la forma más segura posible. Consulte [Permisos de usuario](../ide/user-permissions-and-visual-studio.md).  
  
 Para desarrollar de forma eficaz aplicaciones seguras, es preciso tener unos conocimientos básicos sobre los conceptos y las características de seguridad de las plataformas para las que se desarrolla. También es necesario que conozca las técnicas de codificación segura.  
  
## <a name="understanding-security"></a>Conceptos de seguridad  
 [Seguridad](http://msdn.microsoft.com/Library/9a9621d7-8883-4a4f-a874-65e8e09e20a6)  
 Describe la seguridad de acceso del código de .NET Framework, la seguridad basada en roles, la directiva de seguridad y las herramientas de seguridad.  
  
 [Defend Your Code with Top Ten Security Tips Every Developer Must Know](http://go.microsoft.com/fwlink/?LinkId=72877) (Proteger el código con diez consejos de seguridad que todo desarrollador debe conocer)  
 Describe los problemas más importantes que debería tener en cuenta para no poner en peligro los datos ni el sistema.  
  
## <a name="coding-for-security"></a>Codificación de seguridad  
 La mayoría de los errores de codificación que tienen como resultado la aparición de puntos vulnerables de seguridad se producen porque los programadores no hacen suposiciones válidas cuando trabajan con los datos que proporciona el usuario o porque no acaban de entender la plataforma para la que están desarrollando.  
  
 [Instrucciones de codificación segura](http://msdn.microsoft.com/Library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)  
 Proporciona instrucciones para clasificar sus componentes y tratar los problemas de seguridad.  
  
 [Procedimientos recomendados para la seguridad](/visual-cpp/top/security-best-practices-for-cpp)  
 Explica las saturaciones del búfer e incluye una descripción completa de la característica de comprobación de seguridad de Microsoft Visual C++ que proporciona el marcador en tiempo de compilación /GS.
