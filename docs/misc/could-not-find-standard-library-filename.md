---
title: "No se encontr&#243; la biblioteca est&#225;ndar &#39;&lt;filename&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc40049"
  - "bc40049"
helpviewer_keywords: 
  - "BC40049"
ms.assetid: a292f97e-4852-4021-b300-7ab47beb95d9
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se encontr&#243; la biblioteca est&#225;ndar &#39;&lt;filename&gt;&#39;
[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] no pudo encontrar o abrir una de las bibliotecas DLL estándares necesarias para la compilación y la vinculación.  
  
 La biblioteca que no se puede utilizar es probablemente mscorlib.dll o microsoft.visualbasic.dll.  
  
 De forma predeterminada, este mensaje es una advertencia. Para obtener información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Id. de error:** BC40049  
  
### Para corregir este error  
  
1.  Compruebe que el archivo indicado en el mensaje de error se encuentre en el disco duro desde el que se ejecuta [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. Normalmente las bibliotecas estándares deben estar en un subdirectorio de \\WINNT\\Microsoft.NET\\Framework o \\WINDOWS\\Microsoft.NET\\Framework.  
  
2.  Compruebe que ni el archivo ni el directorio tengan una configuración o un atributo que impida el acceso de lectura mediante [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  
  
3.  Compruebe que el nombre de archivo y la extensión están escritos correctamente. No se distingue entre mayúsculas y minúsculas.  
  
4.  Si el archivo parece ser accesible y estar ubicado correctamente, puede estar dañado en el disco. Vuelva a instalar [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], si es posible.  
  
5.  Anote el nombre exacto del archivo y la extensión y póngase en contacto con los servicios de soporte técnico de Microsoft.  
  
## Vea también  
 [Compilar desde la línea de comandos](/dotnet/visual-basic/reference/command-line-compiler/building-from-the-command-line)   
 [Cómo: Invocar al compilador de la línea de comandos](../Topic/How%20to:%20Invoke%20the%20Command-Line%20Compiler%20\(Visual%20Basic\).md)   
 [Hable con nosotros](../ide/talk-to-us.md)