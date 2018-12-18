---
title: Una o varias propiedades del archivo .ofs no son válidas para la clase de mensaje seleccionada
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VSTO.NewFormRegionWizard.OFSPropertyError
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cfae8533337bbe18c89dbb670fb58a0c89c6c54c
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34692504"
---
# <a name="one-or-more-properties-in-the-ofs-file-are-not-valid-for-the-message-class-selected"></a>Una o varias propiedades del archivo .ofs no son válidas para la clase de mensaje seleccionada
  Este error aparece cuando se importa un área de formulario diseñada en Outlook, pero uno o más campos en el área de formulario no están compatibles con las clases de mensaje que seleccionó en la página final de la **nueva área de formulario** asistente.  

Por ejemplo, puede seleccionar **Tarea (IPM.Tarea)** en la página final del asistente **Nueva región de formulario** . Si el área de formulario tiene un **dirección de la empresa** campo, recibirá este error porque una tarea no tiene una dirección de la empresa. Por lo tanto, la **dirección de la empresa** campo no es compatible con la `IPM.Task` message (clase).  
  
 Puede seleccionar **tarea (IPM.) Tarea)** en la página final de la **nueva área de formulario** asistente. Si el área de formulario tiene un **dirección de la empresa** campo, recibirá este error porque una tarea no tiene una dirección de la empresa. Por lo tanto, la **dirección de la empresa** campo no es compatible con la `IPM.Task` message (clase).  
  
## <a name="to-correct-this-error"></a>Para corregir este error  
  
-   En la página final del asistente **Nueva región de formulario** , seleccione una clase de mensaje que sea compatible con los campos del área del formulario.  
  
-   En el Diseñador de formularios de Outlook, quitar los campos que no están compatibles con las clases de mensaje. Quitar los campos que desea seleccionar en la página final de la **nueva área de formulario** asistente.  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: Importar un área de formulario diseñada en Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  