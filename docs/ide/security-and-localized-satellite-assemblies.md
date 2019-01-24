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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4d0c38ae4353c7761b1cff4173b995ab6c89e0a4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53892058"
---
# <a name="security-and-localized-satellite-assemblies"></a>Seguridad y ensamblados satélite localizados

Si el ensamblado principal usa nombres seguros, los ensamblados satélite deben firmarse con la misma clave privada que el ensamblado principal. Si el par de clave pública y privada de los ensamblados principal y satélite no coincide, los recursos no se cargarán. Para obtener más información sobre la firma de ensamblados, vea [Cómo: Firmar un ensamblado con un nombre seguro](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name).

 En general, es posible que necesite el grupo de firmas de su organización o la firma de una organización de firmas externa con la clave privada. Esto es debido a la naturaleza confidencial de la clave privada: el acceso suele estar restringido a unas pocas personas. Puede retrasar la firma durante el desarrollo. Para obtener más información, vea [Retrasar la firma de un ensamblado](/dotnet/framework/app-domains/delay-sign-assembly).

## <a name="see-also"></a>Vea también

- [Consideraciones de seguridad sobre ensamblados](/dotnet/framework/app-domains/assembly-security-considerations)  - [Conceptos clave de seguridad](/dotnet/standard/security/key-security-concepts)
- [Introducción a aplicaciones internacionales basadas en .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)
- [Localizar aplicaciones](../ide/localizing-applications.md)
- [Globalizar y localizar aplicaciones](../ide/globalizing-and-localizing-applications.md)