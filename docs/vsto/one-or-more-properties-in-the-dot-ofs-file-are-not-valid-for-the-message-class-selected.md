---
title: "Una o varias propiedades del archivo .ofs no son válidas para la clase de mensaje seleccionada | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VSTO.NewFormRegionWizard.OFSPropertyError
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 6ab0b36921911ac8c70501096868f47a40371f79
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="one-or-more-properties-in-the-ofs-file-are-not-valid-for-the-message-class-selected"></a>Una o varias propiedades del archivo .ofs no son válidas para la clase de mensaje seleccionada
  Este error aparece cuando importa un área de formulario diseñada en Outlook, pero uno o más campos del área de formulario no son compatibles con las clases de mensaje que selecciona en la página final del asistente **Nueva región de formulario** .  
  
 Por ejemplo, puede seleccionar **Tarea (IPM.Tarea)** en la página final del asistente **Nueva región de formulario** . Si el área de formulario contiene un campo **Dirección del trabajo** , recibirá este error porque una tarea no tiene una dirección de la empresa. Por tanto, el campo **Dirección de la empresa** no es compatible con la clase de mensaje IPM.Task.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   En la página final del asistente **Nueva región de formulario** , seleccione una clase de mensaje que sea compatible con los campos del área del formulario.  
  
-   En el Diseñador de formularios de Outlook, quite los campos que no son compatibles con las clases de mensaje que planea seleccionar en la página final del asistente **Nueva región de formulario** .  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: Importación de un área de formulario diseñada en Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  