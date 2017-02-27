---
title: "Idiomas de los recursos neutros para la localizaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "referencia cultural, ubicar recursos"
  - "globalización [Visual Studio], recursos"
  - "localización [Visual Studio], recursos"
  - "recursos neutrales"
  - "NeutralResourcesLanguageAttribute (clase)"
  - "recursos [Visual Studio], sistema de reserva"
ms.assetid: ef064995-3b84-4698-a708-9689b7723533
caps.latest.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 8
---
# Idiomas de los recursos neutros para la localizaci&#243;n
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La clase <xref:System.Resources.NeutralResourcesLanguageAttribute> especifica la referencia cultural de los recursos incluidos en el ensamblado principal.  Este atributo se usa como mejora de rendimiento para que el objeto <xref:System.Resources.ResourceManager> no llegue a los recursos incluidos en el ensamblado principal.  
  
 En el código siguiente se muestra cómo establecer el idioma de los recursos neutros.  El código se puede incluir en un script de compilación o en el archivo AssemblyInfo.vb o AssemblyInfo.cs.  
  
```vb#  
' Set neutral resources language for assembly.  
<Assembly: NeutralResourcesLanguageAttribute("en")>  
  
```  
  
```c#  
// Set neutral resources language for assembly.  
[assembly: NeutralResourcesLanguageAttribute("en")]  
```  
  
## Vea también  
 <xref:System.Resources.ResourceManager>   
 [Introducción a aplicaciones internacionales basadas en .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)   
 [Organización jerárquica de recursos para la localización](../ide/hierarchical-organization-of-resources-for-localization.md)   
 [Localizar aplicaciones](../ide/localizing-applications.md)   
 [Globalizar y localizar aplicaciones](../ide/globalizing-and-localizing-applications.md)