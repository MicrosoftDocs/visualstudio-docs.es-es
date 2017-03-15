---
title: "Unable to read the resource information from the licx file | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.fail_reading_licx_file"
ms.assetid: e59f0965-fa1c-4852-bd39-63430d5b7d9f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Unable to read the resource information from the licx file
El sistema del proyecto no pudo leer el archivo .licx.  Como parte de la preparación de licencias, el sistema del proyecto transformará archivos de texto .licx en archivos de recursos binarios, adecuados para utilizarlos con el modelo de licencia COM\+.  
  
 El Diseñador de Windows Forms genera o actualiza automáticamente el archivo .licx siempre que se agrega al formulario un control con licencia.  Existe un archivo .licx por proyecto; siempre se sitúa en la carpeta raíz y siempre se denomina Licenses.licx.  
  
 Algunas causas de este error son:  
  
-   Permiso denegado.  
  
-   Pérdida de comunicación con el servidor Web para proyectos web.  
  
 El proceso de compilación no finalizará correctamente si ocurre este error.  
  
## Vea también  
 [How to: License Components and Controls](../Topic/How%20to:%20License%20Components%20and%20Controls.md)