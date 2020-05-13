---
title: Compatibilidad de Visual Studio con el modo de funcionamiento aprobado 140-2 de FIPS
ms.date: 04/14/2020
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 06d147397a168bb78a31a8fbe6929d6c2184d080
ms.sourcegitcommit: cc58ca7ceae783b972ca25af69f17c9f92a29fc2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/15/2020
ms.locfileid: "81386691"
---
# <a name="visual-studio-support-for-the-fips-140-2-approved-mode-of-operation"></a>Compatibilidad de Visual Studio con el modo de funcionamiento aprobado 140-2 de FIPS

A partir de la [versión 16.4](/visualstudio/releases/2019/release-notes-v16.4/), Visual Studio 2019 admite el modo de funcionamiento aprobado 140-2 de la publicación del Estándar federal de procesamiento de información (FIPS) para Windows, Azure y .NET. Además, con la [versión 16.5](/visualstudio/releases/2019/release-notes-v16.5/), ahora Visual Studio admite el modo de funcionamiento aprobado 140-2 de FIPS al desarrollar [aplicaciones C++ destinadas a un sistema Linux remoto](/cpp/linux/set-up-fips-compliant-secure-remote-linux-development/).

Para configurar el modo de funcionamiento aprobado 140-2 de FIPS para Visual Studio, [instale .NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48) y, después, habilite el valor de directiva de grupo, **Criptografía del sistema: Usar algoritmos que cumplan el estándar FIPS para cifrado, firma y operaciones hash.** .

Para obtener más información sobre el modo de funcionamiento aprobado 140-2 de FIPS y cómo habilitarlo, vea [Validación de 140-2 de FIPS](/windows/security/threat-protection/fips-140-validation/).

> [!NOTE]
> Es posible que las herramientas que se usan para desarrollar aplicaciones para plataformas que no son de Microsoft como iOS o Android no utilicen algoritmos compatibles con FIPS. También es posible que el software de terceros incluido con Visual Studio o las extensiones que instale tampoco use algoritmos compatibles con FIPS. Además, el desarrollo para soluciones de [SharePoint](/sharepoint/security-for-sharepoint-server/federal-information-processing-standard-security-standards/) no admite el modo de funcionamiento aprobado 140-2 de FIPS.

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información sobre el modo de funcionamiento aprobado 140-2de FIPS para Visual Studio y otros productos y servicios de Microsoft, vea los vínculos siguientes:

- [Visual Studio: Configuración del desarrollo de Linux remoto seguro compatible con FIPS con C++](/cpp/linux/set-up-fips-compliant-secure-remote-linux-development/)
- [Windows: Criptografía del sistema y uso de algoritmos compatibles con FIPS para cifrado, hash y firma](/windows/security/threat-protection/security-policy-settings/system-cryptography-use-fips-compliant-algorithms-for-encryption-hashing-and-signing)
- [.NET Core: Compatibilidad con FIPS](/dotnet/standard/security/fips-compliance/)

## <a name="see-also"></a>Vea también

[Protección de las aplicaciones](securing-applications.md)