---
title: "Error copying the application configuration file to the run directory. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cant_copy_appcfg_file"
ms.assetid: 15699a76-16ef-40a8-8ed4-5eef4d2c0e72
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error copying the application configuration file to the run directory. &lt;reason&gt;
El sistema del proyecto no pueda copiar un archivo app.config en el directorio desde el que se ejecuta el proyecto.  El proceso de compilación no finalizará correctamente si ocurre este error.  
  
 Este error sólo ocurre al compilar un archivo .exe.  
  
 El sistema de compilación intenta encontrar un archivo denominado app.config en la carpeta raíz del proyecto.  A continuación, ese archivo se copiará en el directorio de resultados del proyecto; su nombre en el directorio de resultados será *outputfile.*.config.  
  
 Entre las causas de este error se incluyen:  
  
-   Espacio en disco insuficiente.  
  
-   Límite MAX\_PATH superado.  
  
 También puede resultar conveniente asegurarse de que no hay otra copia de la aplicación ejecutándose.  
  
## Vea también  
 [NIB How to: Modify Project Properties and Configuration Settings](http://msdn.microsoft.com/es-es/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)