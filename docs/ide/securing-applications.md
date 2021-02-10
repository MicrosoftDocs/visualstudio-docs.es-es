---
title: Seguridad
description: Obtenga información sobre algunos conceptos de seguridad y las características de seguridad que pueden ayudarle a desarrollar aplicaciones seguras de forma eficaz.
ms.custom: SEO-VS-2020
ms.date: 06/01/2018
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio], applications
- application design, securability
ms.assetid: 7d32c4cf-8bec-4307-a2a8-42f0ceddf3eb
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c3d5fe8755450fd5068688064bf36b08c741c862
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878648"
---
# <a name="secure-applications"></a>Aplicaciones seguras

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

## <a name="see-also"></a>Consulte también

- [Seguridad en .NET](/dotnet/standard/security/index)
- [Seguridad de Azure](/azure/security/)
- [Guía de seguridad de Windows 10 Mobile](/windows/security/threat-protection/windows-10-mobile-security-guide)
- [Características de seguridad de la plataforma Apache Cordova](/visualstudio/cross-platform/tools-for-cordova/security/best-practices?view=toolsforcordova-2017&preserve-view=true)
- [Seguridad de ASP.NET Core](/aspnet/core/security/?view=aspnetcore-2.1&preserve-view=true)
- [Seguridad en Windows Forms](/dotnet/framework/winforms/windows-forms-security)
