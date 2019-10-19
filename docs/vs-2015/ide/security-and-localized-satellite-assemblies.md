---
title: Seguridad y ensamblados satélite localizados | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 866e313a36af5ef72f910a5eafbf7b31c971d890
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672906"
---
# <a name="security-and-localized-satellite-assemblies"></a>Seguridad y ensamblados satélite localizados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si el ensamblado principal usa nombres seguros, los ensamblados satélite deben firmarse con la misma clave privada que el ensamblado principal. Si el par de clave pública y privada de los ensamblados principal y satélite no coincide, los recursos no se cargarán. Para más información sobre la firma de ensamblados, vea [Cómo: Firmar un ensamblado con un nombre seguro](https://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67).

 En general, es posible que necesite el grupo de firmas de su organización o la firma de una organización de firmas externa con la clave privada. Esto es debido a la naturaleza confidencial de la clave privada: el acceso suele estar restringido a unas pocas personas. Puede retrasar la firma durante el desarrollo. Para más información, vea [Retrasar la firma de un ensamblado](https://msdn.microsoft.com/library/9d300e17-5bf1-4360-97da-2aa55efd9070).

## <a name="see-also"></a>Otras referencias
 [Consideraciones de seguridad del ensamblado](https://msdn.microsoft.com/library/1b5439c1-f3d5-4529-bd69-01814703d067) [conceptos clave de seguridad](https://msdn.microsoft.com/library/3cfced4f-ea02-4e66-ae98-d69286363e98) [Introducción a las aplicaciones internacionales basadas en la .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md) [localizar aplicaciones](../ide/localizing-applications.md) [globalizar y localizar aplicaciones](../ide/globalizing-and-localizing-applications.md)
