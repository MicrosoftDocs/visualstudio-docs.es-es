---
title: "Error PRJ0039 al compilar el proyecto | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PRJ0039"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0039"
ms.assetid: 207bbc28-922f-44d6-8bdd-3016c850f5b9
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Error PRJ0039 al compilar el proyecto
No se puede crear un archivo temporal. Es necesario realizar esta operación para poder ejecutar la herramienta NMake.  
  
 Al crear un proyecto de archivos MAKE \(vea [crear un proyecto de archivos MAKE](/visual-cpp/ide/creating-a-makefile-project)\), el sistema de proyecto de Visual C\+\+ necesita crear algunos archivos temporales. Este error indica que el sistema del proyecto no pudo crear uno o varios de esos archivos.  
  
 La variable de entorno TMP contiene el nombre del directorio temporal.  
  
 A continuación se indican las causas posibles de este error y las resoluciones sugeridas:  
  
 El usuario no tiene acceso de escritura al directorio temporal  
 Asegúrese de tener acceso de escritura al directorio temporal.  
  
 Hay demasiados archivos temporales en el directorio temporal  
 Otros procesos podrían haber creado archivos temporales, pero no los eliminaron. Elimine algunos de estos archivos temporales o todos.  
  
 No hay espacio libre en disco  
 Elimine algunos archivos del disco o cambie el directorio temporal a un disco con espacio libre.  
  
 La variable de entorno TMP es incorrecta  
 Es posible que la variable de entorno TMP señale un directorio que no existe.