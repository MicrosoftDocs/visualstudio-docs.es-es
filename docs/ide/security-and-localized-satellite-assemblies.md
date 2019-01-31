---
title: Seguridad y ensamblados satélite localizados
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- key pairs for strong-named assemblies
- strong-named assemblies, security considerations
- satellite assemblies, localized
- code signing, assemblies
- security [Visual Studio], assemblies
- strong-named assemblies, localized
- assemblies [Visual Studio], security
- localization, satellite assemblies
ms.assetid: 6d953840-b301-47d5-8d34-30c1b29b5071
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9938398f0a4f9c81e26b3ddb3c0754e56a31a286
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55040274"
---
# <a name="security-and-localized-satellite-assemblies"></a>Seguridad y ensamblados satélite localizados

Si el ensamblado principal usa nombres seguros, los ensamblados satélite deben firmarse con la misma clave privada que el ensamblado principal. Si el par de clave pública y privada de los ensamblados principal y satélite no coincide, los recursos no se cargarán. Para obtener más información sobre la firma de ensamblados, vea [Cómo: Firmar un ensamblado con un nombre seguro](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name).

 En general, es posible que necesite el grupo de firmas de su organización o la firma de una organización de firmas externa con la clave privada. Esto es debido a la naturaleza confidencial de la clave privada: el acceso suele estar restringido a unas pocas personas. Puede retrasar la firma durante el desarrollo. Para obtener más información, vea [Retrasar la firma de un ensamblado](/dotnet/framework/app-domains/delay-sign-assembly).

## <a name="see-also"></a>Vea también

- [Consideraciones de seguridad sobre ensamblados](/dotnet/framework/app-domains/assembly-security-considerations)  - [Conceptos clave de seguridad](/dotnet/standard/security/key-security-concepts)
- [Introducción a aplicaciones internacionales basadas en .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)
- [Localizar aplicaciones](../ide/localizing-applications.md)
- [Globalizar y localizar aplicaciones](../ide/globalizing-and-localizing-applications.md)