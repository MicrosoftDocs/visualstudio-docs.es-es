---
title: Idiomas de los recursos neutros para la localización | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- localization [Visual Studio], resources
- NeutralResourcesLanguageAttribute class
- globalization [Visual Studio], resources
- resources [Visual Studio], fallback system
- culture, locating resources
- neutral resources
ms.assetid: ef064995-3b84-4698-a708-9689b7723533
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 45fadacc75b2772ba32d7cb0d796c972076b81ef
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49256705"
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
  
## <a name="see-also"></a>Vea también  
 <xref:System.Resources.ResourceManager>   
 [Introducción a aplicaciones internacionales basadas en .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)   
 [Organización jerárquica de recursos para la localización](../ide/hierarchical-organization-of-resources-for-localization.md)   
 [Localizar aplicaciones](../ide/localizing-applications.md)   
 [Globalizar y localizar aplicaciones](../ide/globalizing-and-localizing-applications.md)

