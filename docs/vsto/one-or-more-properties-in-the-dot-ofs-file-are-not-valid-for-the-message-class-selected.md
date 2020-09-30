---
title: Propiedades no válidas en el archivo. OFS para la clase de mensaje "
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
ms.openlocfilehash: 66e8ecacffb58e945a3f80d03f47edc1329668d1
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584664"
---
# <a name="invalid-properties-in-the-ofs-file-for-the-message-class"></a>Propiedades no válidas en el archivo. OFS para la clase de mensaje

  El error "una o varias propiedades del archivo. OFS no son válidas para la clase de mensaje seleccionada" aparece al importar un área de formulario diseñada en Outlook, pero uno o más campos del área de formulario no son compatibles con las clases de mensaje que selecciona en la página final del asistente **nueva región de formulario** .

Por ejemplo, puede seleccionar **Tarea (IPM.Tarea)** en la página final del asistente **Nueva región de formulario** . Si el área de formulario tiene un campo de **dirección de trabajo** , recibirá este error porque una tarea no tiene una dirección de negocio. Por lo tanto, el campo **dirección del trabajo** no es compatible con la `IPM.Task` clase de mensaje.

 Puede seleccionar **tarea (IPM. Tarea)** en la página final del asistente **nueva región de formulario** . Si el área de formulario tiene un campo de **dirección de trabajo** , recibirá este error porque una tarea no tiene una dirección de negocio. Por lo tanto, el campo **dirección del trabajo** no es compatible con la `IPM.Task` clase de mensaje.

## <a name="to-correct-this-error"></a>Para corregir este error

- En la página final del asistente **Nueva región de formulario** , seleccione una clase de mensaje que sea compatible con los campos del área del formulario.

- En el diseñador de formularios de Outlook, quite los campos que no sean compatibles con las clases de mensaje. Quite los campos que planea seleccionar en la página final del asistente **nueva región de formulario** .

## <a name="see-also"></a>Vea también
- [Tutorial: importar un área de formulario diseñada en Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
