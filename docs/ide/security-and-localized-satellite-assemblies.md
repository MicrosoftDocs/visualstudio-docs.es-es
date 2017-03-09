---
title: "Seguridad y ensamblados sat&#233;lite localizados | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ensamblados [Visual Studio], seguridad"
  - "firma de código, ensamblados"
  - "pares de claves para ensamblados con nombre seguro"
  - "localización, ensamblados satélite"
  - "ensamblados satélite, localizado"
  - "seguridad [Visual Studio], ensamblados"
  - "ensamblados con nombre seguro, localizado"
  - "ensamblados con nombre seguro, consideraciones de seguridad"
ms.assetid: 6d953840-b301-47d5-8d34-30c1b29b5071
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Seguridad y ensamblados sat&#233;lite localizados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si el ensamblado principal utiliza nombres seguros, los ensamblados satélite deben firmarse con la misma clave privada que el ensamblado principal.  Si el par clave pública y clave privada no coincide entre los ensamblados principal y satélite, no se cargarán los recursos.  Para obtener más información sobre la firma de ensamblados, vea [Cómo: Firmar un ensamblado con un nombre seguro](../Topic/How%20to:%20Sign%20an%20Assembly%20with%20a%20Strong%20Name.md).  
  
 En general, es posible que necesite un grupo de firmas de su organización o una firma de la organización con firmas externas con la clave privada.  Esto es debido a la naturaleza sensible de la clave privada: la clave privada suele estar restringida sólo a algunas personas.  Puede utilizar la firma postergada durante el desarrollo.  Para obtener más información, vea [Retrasar la firma de un ensamblado](../Topic/Delay%20Signing%20an%20Assembly.md).  
  
## Vea también  
 [Consideraciones de seguridad sobre ensamblados](../Topic/Assembly%20Security%20Considerations.md)   
 [Key Security Concepts](../Topic/Key%20Security%20Concepts.md)   
 [Introducción a aplicaciones internacionales basadas en .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)   
 [Localizar aplicaciones](../ide/localizing-applications.md)   
 [Globalizar y localizar aplicaciones](../ide/globalizing-and-localizing-applications.md)