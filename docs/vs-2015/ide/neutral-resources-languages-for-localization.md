---
title: Idiomas de los recursos neutros para la localización | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- localization [Visual Studio], resources
- NeutralResourcesLanguageAttribute class
- globalization [Visual Studio], resources
- resources [Visual Studio], fallback system
- culture, locating resources
- neutral resources
ms.assetid: ef064995-3b84-4698-a708-9689b7723533
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 85e0be0172f27732f8efeb882cbcde5b9c6aef3d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670382"
---
# <a name="neutral-resources-languages-for-localization"></a>Idiomas de los recursos neutros para la localización
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La clase <xref:System.Resources.NeutralResourcesLanguageAttribute> especifica la referencia cultural de los recursos incluidos en el ensamblado principal. Este atributo se usa para mejorar el rendimiento, de forma que el objeto <xref:System.Resources.ResourceManager> no busque los recursos que se incluyen en el ensamblado principal.

 El código siguiente muestra cómo establecer el idioma de los recursos neutros. El código se puede colocar en un script de compilación o en el archivo AssemblyInfo.vb o AssemblyInfo.cs.

```vb
' Set neutral resources language for assembly.
<Assembly: NeutralResourcesLanguageAttribute("en")>

```

```csharp
// Set neutral resources language for assembly.
[assembly: NeutralResourcesLanguageAttribute("en")]
```

## <a name="see-also"></a>Consulte también
 <xref:System.Resources.ResourceManager>[Introducción a las aplicaciones internacionales basadas en la .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md) [organización jerárquica de recursos para la localización de la localización de](../ide/hierarchical-organization-of-resources-for-localization.md) [aplicaciones](../ide/localizing-applications.md) [globalizar y localizar aplicaciones](../ide/globalizing-and-localizing-applications.md)
