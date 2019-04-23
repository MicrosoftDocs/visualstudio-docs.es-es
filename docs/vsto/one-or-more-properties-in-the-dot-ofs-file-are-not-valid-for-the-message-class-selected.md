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
ms.openlocfilehash: d58ad6ff89d8cf41ec60135cfbfe3deac1382f1e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60095274"
---
# <a name="one-or-more-properties-in-the-ofs-file-are-not-valid-for-the-message-class-selected"></a>Una o varias propiedades del archivo .ofs no son válidas para la clase de mensaje seleccionada
  Este error aparece cuando importa un área de formulario diseñada en Outlook, pero uno o varios campos en el área de formulario no son compatibles con las clases de mensaje que seleccionó en la página final de la **nueva área de formulario** asistente.

Por ejemplo, puede seleccionar **Tarea (IPM.Tarea)** en la página final del asistente **Nueva región de formulario** . Si el área de formulario tiene un **dirección de la empresa** campo, recibirá este error porque una tarea no tiene una dirección de la empresa. Por lo tanto, el **dirección de la empresa** campo no es compatible con la `IPM.Task` message (clase).

 Puede seleccionar **tarea (IPM. Tarea)** en la página final de la **nueva área de formulario** asistente. Si el área de formulario tiene un **dirección de la empresa** campo, recibirá este error porque una tarea no tiene una dirección de la empresa. Por lo tanto, el **dirección de la empresa** campo no es compatible con la `IPM.Task` message (clase).

## <a name="to-correct-this-error"></a>Para corregir este error

- En la página final del asistente **Nueva región de formulario** , seleccione una clase de mensaje que sea compatible con los campos del área del formulario.

- En el Diseñador de formularios de Outlook, quite los campos que no son compatibles con las clases de mensaje. Quite los campos que se va a seleccionar en la página final de la **nueva área de formulario** asistente.

## <a name="see-also"></a>Vea también
- [Tutorial: Importar un área de formulario diseñada en Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
