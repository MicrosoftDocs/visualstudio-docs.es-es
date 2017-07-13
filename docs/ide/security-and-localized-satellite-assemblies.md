---
title: "Seguridad y ensamblados satélite localizados | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
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
caps.latest.revision: 8
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 3d32d11a430227800cb3ed53831a9565eb6adeb3
ms.openlocfilehash: 2bac6b9d00c52e782cf2993ce70c3bd3466aba55
ms.contentlocale: es-es
ms.lasthandoff: 05/30/2017

---
# Seguridad y ensamblados satélite localizados
<a id="security-and-localized-satellite-assemblies" class="xliff"></a>
Si el ensamblado principal usa nombres seguros, los ensamblados satélite deben firmarse con la misma clave privada que el ensamblado principal. Si el par de clave pública y privada de los ensamblados principal y satélite no coincide, los recursos no se cargarán. Para más información sobre la firma de ensamblados, vea [Cómo: Firmar un ensamblado con un nombre seguro](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name).  
  
 En general, es posible que necesite el grupo de firmas de su organización o la firma de una organización de firmas externa con la clave privada. Esto es debido a la naturaleza confidencial de la clave privada: el acceso suele estar restringido a unas pocas personas. Puede retrasar la firma durante el desarrollo. Para más información, vea [Retrasar la firma de un ensamblado](/dotnet/framework/app-domains/delay-sign-assembly).  
  
## Vea también
<a id="see-also" class="xliff"></a>  
 [Consideraciones de seguridad sobre ensamblados](/dotnet/framework/app-domains/assembly-security-considerations)   
 [Conceptos clave de seguridad](/dotnet/standard/security/key-security-concepts)   
 [Introducción a aplicaciones internacionales basadas en .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)   
 [Localizar aplicaciones](../ide/localizing-applications.md)   
 [Globalizar y localizar aplicaciones](../ide/globalizing-and-localizing-applications.md)
