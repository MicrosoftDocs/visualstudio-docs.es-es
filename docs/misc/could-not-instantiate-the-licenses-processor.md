---
title: "Could not instantiate the licenses processor | Microsoft Docs"
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
  - "vs.tasklisterror.no_licx_generator"
ms.assetid: 9e95d590-f41f-4cfa-bc73-fadeacfdb879
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Could not instantiate the licenses processor
No se pueden crear instancias de la herramienta utilizada para transformar archivos .licx en recursos binarios.  
  
 Como parte de la compilación, el sistema del proyecto transformará un archivo de texto .licx en un recurso binario que proporcione compatibilidad para la licencia de controles .NET.  A continuación, el recurso binario se incrustará en los resultados del proyecto.  
  
 El proceso de compilación no finalizará correctamente si ocurre este error.  
  
 El Diseñador de Windows Forms genera o actualiza automáticamente el archivo .licx siempre que se agrega al formulario un control con licencia.  Existe un archivo .licx por proyecto; siempre se sitúa en la carpeta raíz y siempre se denomina Licenses.licx.  
  
 **Para corregir este error**  
  
-   Vuelva a instalar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Vea también  
 [How to: License Components and Controls](../Topic/How%20to:%20License%20Components%20and%20Controls.md)