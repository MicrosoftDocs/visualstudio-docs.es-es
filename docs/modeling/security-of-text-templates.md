---
title: "Security of Text Templates | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "text templates, security"
ms.assetid: 567a2383-7d43-4acc-af4a-cd70b7a0151e
caps.latest.revision: 23
caps.handback.revision: 23
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Security of Text Templates
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Las plantillas de texto presentan los siguientes problemas de seguridad:  
  
-   Las plantillas de texto son vulnerables a las inserciones arbitrarias de código.  
  
-   Si el mecanismo que usa el host para encontrar un procesador de directivas no es seguro, se puede ejecutar un procesador de directivas malintencionado.  
  
## Código arbitrario  
 Al escribir una plantilla, puede colocar cualquier código dentro de las etiquetas \<\# \#\>.  Esto permite ejecutar código arbitrario desde una plantilla de texto.  
  
 Asegúrese de obtener las plantillas de fuentes de confianza.  Asegúrese de advertir a los usuarios finales de la aplicación que no ejecuten plantillas que no procedan de fuentes de confianza.  
  
## Procesador de directivas malintencionado  
 El motor de plantillas de texto interactúa con un host de transformación y uno o más procesadores de directivas para transformar el texto de la plantilla en un archivo de salida.  Para obtener más información, vea [The Text Template Transformation Process](../modeling/the-text-template-transformation-process.md).  
  
 Si el mecanismo que usa el host para encontrar un procesador de directivas no es seguro, corre el riesgo de ejecutar un procesador de directivas malintencionado.  El procesador de directivas malintencionado puede proporcionar código que se ejecute en modo `FullTrust` al ejecutar la plantilla.  Si crea un host de transformación de plantillas de texto personalizado, debe utilizar un mecanismo seguro, como el Registro, para que el motor busque los procesadores de directivas.