---
title: "Una o varias propiedades del archivo .ofs no son v&#225;lidas para la clase de mensaje seleccionada | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VSTO.NewFormRegionWizard.OFSPropertyError"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: ca9e2ec1-df96-45ca-9611-cec47edfe1e4
caps.latest.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# Una o varias propiedades del archivo .ofs no son v&#225;lidas para la clase de mensaje seleccionada
  Este error aparece cuando importa un área de formulario diseñada en Outlook, pero uno o más campos del área de formulario no son compatibles con las clases de mensaje que selecciona en la página final del asistente **Nueva región de formulario**.  
  
 Por ejemplo, puede seleccionar **Tarea \(IPM.Tarea\)** en la página final del asistente **Nueva región de formulario**. Si el área de formulario contiene un campo **Dirección del trabajo**, recibirá este error porque una tarea no tiene una dirección de la empresa. Por tanto, el campo **Dirección de la empresa** no es compatible con la clase de mensaje IPM.Task.  
  
### Para corregir este error  
  
-   En la página final del asistente **Nueva región de formulario**, seleccione una clase de mensaje que sea compatible con los campos del área del formulario.  
  
-   En el Diseñador de formularios de Outlook, quite los campos que no son compatibles con las clases de mensaje que planea seleccionar en la página final del asistente **Nueva región de formulario**.  
  
## Vea también  
 [Tutorial: Importar un área de formulario diseñada en Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  