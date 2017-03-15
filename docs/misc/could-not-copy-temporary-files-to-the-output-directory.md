---
title: "No se pueden copiar los archivos temporales en el directorio de resultados | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cannot_copy_to_run_dir"
ms.assetid: b8b54984-74c9-4b9b-8164-d0d13c141055
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# No se pueden copiar los archivos temporales en el directorio de resultados
El sistema del proyecto no pudo copiar los archivos temporales en el directorio de salida. Los compiladores siempre realizan la compilación en directorios intermedios, por ejemplo, obj\\`configname`. Al final del proceso de compilación, el sistema del proyecto copia los archivos del directorio intermedio en el directorio de salida del proyecto.  
  
 Este problema puede producirse si uno de los ensamblados que compila es mayor que 64 kilobytes \(KB\) y se cumple una de las siguientes condiciones \(o ambas\):  
  
-   La solución contiene proyectos compilados en la misma carpeta de salida.  
  
-   La propiedad Copy Local en uno de los ensamblados o los proyectos de referencia está establecida en False.  
  
 **Para corregir este error**  
  
-   Compile las salidas de proyectos individuales en carpetas diferentes.  
  
-   Establezca la propiedad Copy Local del ensamblado o el proyecto de referencia en True.  
  
-   Compruebe que no tiene la ventana Examinador de objetos abierta.  
  
-   Compruebe que no tiene el mismo proyecto \(o proyectos\) abierto en otra instancia de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Vea también  
 [No está en la compilación: Cómo: Establecer la propiedad Copy Local de una referencia](http://msdn.microsoft.com/es-es/dfe2ba13-f27f-4356-a481-ea67d5acacbd)