---
title: Seguridad
ms.date: 06/01/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio], applications
- application design, securability
ms.assetid: 7d32c4cf-8bec-4307-a2a8-42f0ceddf3eb
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 74643454c4e96f5f4c1faa98b26fa1f26bd2790b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53904635"
---
# <a name="secure-applications"></a>Proteger aplicaciones

Las consideraciones sobre seguridad se deben aplicar a todo el desarrollo de la aplicación, desde el diseño hasta la implementación. Comience ejecutando Visual Studio de la forma más segura posible. Vea [Permisos de usuario](../ide/user-permissions-and-visual-studio.md).

Para desarrollar de forma eficaz aplicaciones seguras, es preciso tener unos conocimientos básicos sobre los conceptos y las características de seguridad de las plataformas para las que se desarrolla. También es necesario que conozca las técnicas de codificación segura.

## <a name="code-for-security"></a>Código para seguridad

La mayoría de los errores de codificación que tienen como resultado la aparición de puntos vulnerables de seguridad se producen porque los programadores no hacen suposiciones válidas cuando trabajan con los datos que proporciona el usuario o porque no acaban de entender la plataforma para la que están desarrollando.

- Las [directrices de codificación segura](/dotnet/standard/security/secure-coding-guidelines) describen las diferentes formas en que se puede diseñar código .NET para que funcione con el sistema de seguridad.
- Los [procedimientos recomendados de seguridad para C++](/cpp/top/security-best-practices-for-cpp) contienen información sobre las herramientas de seguridad y los procedimientos recomendados para desarrolladores de C++.

## <a name="build-for-security"></a>Compilación para seguridad

La seguridad también es una consideración importante en el proceso de compilación. Algunos pasos adicionales pueden mejorar la seguridad de una aplicación implementada y ayudar a prevenir la ingeniería inversa no autorizada, la suplantación de identidad u otros ataques:

- [Dotfuscator](dotfuscator/index.md) es gratuito y ayuda a proteger los ensamblados de .NET frente al uso no autorizado y a la ingeniería inversa, como la depuración no autorizada.
- La [firma de nombre seguro](managing-assembly-and-manifest-signing.md) se puede usar para identificar los componentes de software e impide la suplantación de nombres.

## <a name="see-also"></a>Vea también

- [Seguridad en .NET Framework](/dotnet/standard/security/index)
- [Seguridad de Azure](/azure/security/)
- [Guía de seguridad de Windows 10 Mobile](/windows/security/threat-protection/windows-10-mobile-security-guide)
- [Características de seguridad de la plataforma Apache Cordova](/visualstudio/cross-platform/tools-for-cordova/security/best-practices?view=toolsforcordova-2017)
- [Seguridad de ASP.NET Core](/aspnet/core/security/?view=aspnetcore-2.1)
- [Seguridad en Windows Forms](/dotnet/framework/winforms/windows-forms-security)