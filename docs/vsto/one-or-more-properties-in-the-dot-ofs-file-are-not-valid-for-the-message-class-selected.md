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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62977866"
---
# <a name="one-or-more-properties-in-the-ofs-file-are-not-valid-for-the-message-class-selected"></a>Una o varias propiedades del archivo .ofs no son válidas para la clase de mensaje seleccionada
  Este error aparece cuando importa un área de formulario diseñada en Outlook, pero uno o más campos del área de formulario no son compatibles con las clases de mensaje que selecciona en la página final del asistente **nueva región de formulario** .

Por ejemplo, puede seleccionar **Tarea (IPM.Tarea)** en la página final del asistente **Nueva región de formulario** . Si el área de formulario tiene un campo de **dirección de trabajo** , recibirá este error porque una tarea no tiene una dirección de negocio. Por lo tanto, el campo **dirección del trabajo** no es compatible con la `IPM.Task` clase de mensaje.

 Puede seleccionar **tarea (IPM. Tarea)** en la página final del asistente **nueva región de formulario** . Si el área de formulario tiene un campo de **dirección de trabajo** , recibirá este error porque una tarea no tiene una dirección de negocio. Por lo tanto, el campo **dirección del trabajo** no es compatible con la `IPM.Task` clase de mensaje.

## <a name="to-correct-this-error"></a>Para corregir este error

- En la página final del asistente **Nueva región de formulario** , seleccione una clase de mensaje que sea compatible con los campos del área del formulario.

- En el diseñador de formularios de Outlook, quite los campos que no sean compatibles con las clases de mensaje. Quite los campos que planea seleccionar en la página final del asistente **nueva región de formulario** .

## <a name="see-also"></a>Consulte también
- [Tutorial: importar un área de formulario diseñada en Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
