---
title: Seguridad y ensamblados satélite localizados | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8b530cb0f85eb112c98ff9d4de07f7256c5e69c9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568062"
---
# <a name="security-and-localized-satellite-assemblies"></a>Seguridad y ensamblados satélite localizados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si el ensamblado principal usa nombres seguros, los ensamblados satélite deben firmarse con la misma clave privada que el ensamblado principal. Si el par de clave pública y privada de los ensamblados principal y satélite no coincide, los recursos no se cargarán. Para más información sobre la firma de ensamblados, vea [Cómo: Firmar un ensamblado con un nombre seguro](http://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67).  
  
 En general, es posible que necesite el grupo de firmas de su organización o la firma de una organización de firmas externa con la clave privada. Esto es debido a la naturaleza confidencial de la clave privada: el acceso suele estar restringido a unas pocas personas. Puede retrasar la firma durante el desarrollo. Para más información, vea [Retrasar la firma de un ensamblado](http://msdn.microsoft.com/library/9d300e17-5bf1-4360-97da-2aa55efd9070).  
  
## <a name="see-also"></a>Vea también  
 [Consideraciones de seguridad sobre ensamblados](http://msdn.microsoft.com/library/1b5439c1-f3d5-4529-bd69-01814703d067)   
 [Conceptos clave de seguridad](http://msdn.microsoft.com/library/3cfced4f-ea02-4e66-ae98-d69286363e98)   
 [Introducción a aplicaciones internacionales basadas en .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)   
 [Localizar aplicaciones](../ide/localizing-applications.md)   
 [Globalizar y localizar aplicaciones](../ide/globalizing-and-localizing-applications.md)

