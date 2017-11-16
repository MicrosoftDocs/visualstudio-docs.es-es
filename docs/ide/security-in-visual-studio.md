---
title: Seguridad en Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 02/17/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code access security, coding errors
- security [.NET Framework], about security
ms.assetid: 318c34ce-f643-468c-83a1-843196f5d845
caps.latest.revision: "20"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 25b0f76c657f4d4df7375b4fc9e418e8806bd51f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="security-in-visual-studio"></a>Seguridad en Visual Studio
Las consideraciones sobre seguridad se deben aplicar a todo el desarrollo de la aplicación, desde el diseño hasta la implementación. Comience ejecutando Visual Studio de la forma más segura posible. Consulte [Permisos de usuario](../ide/user-permissions-and-visual-studio.md).  
  
 Para desarrollar de forma eficaz aplicaciones seguras, es preciso tener unos conocimientos básicos sobre los conceptos y las características de seguridad de las plataformas para las que se desarrolla. También es necesario que conozca las técnicas de codificación segura.  
  
## <a name="understanding-security"></a>Conceptos de seguridad  
 [Seguridad](/dotnet/standard/security/index)  
 Describe la seguridad de acceso del código de .NET Framework, la seguridad basada en roles, la directiva de seguridad y las herramientas de seguridad.  
  
 [Defend Your Code with Top Ten Security Tips Every Developer Must Know](http://go.microsoft.com/fwlink/?LinkId=72877) (Proteger el código con diez consejos de seguridad que todo desarrollador debe conocer)  
 Describe los problemas más importantes que debería tener en cuenta para no poner en peligro los datos ni el sistema.  
  
## <a name="coding-for-security"></a>Codificación de seguridad  
 La mayoría de los errores de codificación que tienen como resultado la aparición de puntos vulnerables de seguridad se producen porque los programadores no hacen suposiciones válidas cuando trabajan con los datos que proporciona el usuario o porque no acaban de entender la plataforma para la que están desarrollando.  
  
 [Instrucciones de codificación segura](/dotnet/standard/security/secure-coding-guidelines)  
 Proporciona instrucciones para clasificar sus componentes y tratar los problemas de seguridad.  
  
 [Procedimientos recomendados para la seguridad](/cpp/top/security-best-practices-for-cpp)  
 Explica las saturaciones del búfer e incluye una descripción completa de la característica de comprobación de seguridad de Microsoft Visual C++ que proporciona el marcador en tiempo de compilación /GS.

## <a name="building-for-security"></a>Compilación para seguridad  
 La seguridad también es una consideración importante en el proceso de compilación.  Algunos pasos adicionales pueden mejorar la seguridad de una aplicación implementada y ayudar a prevenir la ingeniería inversa no autorizada, la suplantación de identidad u otros ataques.

 [Dotfuscator Community Edition (CE)](dotfuscator/index.md)  
 Explica cómo configurar y empezar a usar PreEmptive Protection - Dotfuscator Community Edition gratis para proteger los ensamblados de .NET del uso no autorizado y de la ingeniería inversa (como, por ejemplo, la depuración no autorizada).
  
 [Administrar la firma de ensamblados y manifiestos](managing-assembly-and-manifest-signing.md)  
 Describe la firma de nombre seguro, que se puede usar para identificar los componentes de software, impidiendo la suplantación de nombres.