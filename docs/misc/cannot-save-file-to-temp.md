---
title: "No se puede guardar el archivo en TEMP. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrID735"
ms.assetid: 1055fc15-9641-43b2-a40c-a0a9fbbb34b2
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se puede guardar el archivo en TEMP.
Un componente no puede encontrar un directorio denominado TEMP, o la unidad o partición que contiene el directorio TEMP carece de espacio suficiente para guardar la información.  
  
### Para corregir este error  
  
1.  Cree un directorio denominado "TEMP" y establezca la variable de entorno TEMP en su ruta de acceso.  
  
2.  Libere espacio en la unidad borrando los archivos innecesarios, o cree un directorio TEMP en otra partición y establezca la variable de entorno TEMP en su ruta de acceso.  
  
## Vea también  
 [Tipos de error](/dotnet/visual-basic/programming-guide/language-features/error-types)