---
title: Seguridad
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code access security, coding errors
- security [.NET Framework], about security
ms.assetid: 318c34ce-f643-468c-83a1-843196f5d845
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d546ade1599411dd2880a8c645b340ed86373304
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53931202"
---
# <a name="security-in-visual-studio"></a>Seguridad en Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Las consideraciones sobre seguridad se deben aplicar a todo el desarrollo de la aplicación, desde el diseño hasta la implementación. Comience ejecutando Visual Studio de la forma más segura posible. Consulte [Permisos de usuario](../ide/user-permissions-and-visual-studio.md).

 Para desarrollar de forma eficaz aplicaciones seguras, es preciso tener unos conocimientos básicos sobre los conceptos y las características de seguridad de las plataformas para las que se desarrolla. También es necesario que conozca las técnicas de codificación segura.

## <a name="understanding-security"></a>Conceptos de seguridad
 [Seguridad](http://msdn.microsoft.com/library/9a9621d7-8883-4a4f-a874-65e8e09e20a6) Describe la seguridad de acceso del código de .NET Framework, la seguridad basada en roles, la directiva de seguridad y las herramientas de seguridad.

 En el artículo [Defend your code with top ten security tips every developer must know](http://go.microsoft.com/fwlink/?LinkId=72877) (Proteger el código con diez consejos de seguridad que todo desarrollador debe conocer) se describen los problemas más importantes que debería tener en cuenta para no poner en peligro los datos ni el sistema.

## <a name="coding-for-security"></a>Codificación de seguridad
 La mayoría de los errores de codificación que tienen como resultado la aparición de puntos vulnerables de seguridad se producen porque los programadores no hacen suposiciones válidas cuando trabajan con los datos que proporciona el usuario o porque no acaban de entender la plataforma para la que están desarrollando.

 En la [guía de codificación segura](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) se proporcionan instrucciones para clasificar los componentes a fin de solucionar problemas de seguridad.

 En el artículo [Procedimientos recomendados de seguridad](http://msdn.microsoft.com/library/86acaccf-cdb4-4517-bd58-553618e3ec42) se explican las saturaciones del búfer y se incluye una descripción completa de la característica de comprobación de seguridad de Microsoft Visual C++ que proporciona el marcador en tiempo de compilación /GS.
