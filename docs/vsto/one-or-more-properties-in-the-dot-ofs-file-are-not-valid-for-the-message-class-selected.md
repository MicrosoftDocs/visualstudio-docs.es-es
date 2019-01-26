---
title: Una o varias propiedades del archivo .ofs no son válidas para la clase de mensaje seleccionada
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VSTO.NewFormRegionWizard.OFSPropertyError
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a607fc0e885ea73f95f4b48a82777234977644bb
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54872994"
---
# <a name="one-or-more-properties-in-the-ofs-file-are-not-valid-for-the-message-class-selected"></a>Una o varias propiedades del archivo .ofs no son válidas para la clase de mensaje seleccionada
  Este error aparece cuando importa un área de formulario diseñada en Outlook, pero uno o varios campos en el área de formulario no son compatibles con las clases de mensaje que seleccionó en la página final de la **nueva área de formulario** asistente.  

Por ejemplo, puede seleccionar **Tarea (IPM.Tarea)** en la página final del asistente **Nueva región de formulario** . Si el área de formulario tiene un **dirección de la empresa** campo, recibirá este error porque una tarea no tiene una dirección de la empresa. Por lo tanto, el **dirección de la empresa** campo no es compatible con la `IPM.Task` message (clase).  
  
 Puede seleccionar **tarea (IPM. Tarea)** en la página final de la **nueva área de formulario** asistente. Si el área de formulario tiene un **dirección de la empresa** campo, recibirá este error porque una tarea no tiene una dirección de la empresa. Por lo tanto, el **dirección de la empresa** campo no es compatible con la `IPM.Task` message (clase).  
  
## <a name="to-correct-this-error"></a>Para corregir este error  
  
-   En la página final del asistente **Nueva región de formulario** , seleccione una clase de mensaje que sea compatible con los campos del área del formulario.  
  
-   En el Diseñador de formularios de Outlook, quite los campos que no son compatibles con las clases de mensaje. Quite los campos que se va a seleccionar en la página final de la **nueva área de formulario** asistente.  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: Importar un área de formulario diseñada en Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
