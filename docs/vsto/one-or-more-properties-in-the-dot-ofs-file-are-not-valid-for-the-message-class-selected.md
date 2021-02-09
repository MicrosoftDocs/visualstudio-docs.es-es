---
title: Propiedades no válidas en el archivo. OFS para la clase de mensaje "
description: Obtenga información sobre cómo corregir un error que se produce cuando una o varias propiedades del archivo. OFS no son válidas para la clase de mensaje seleccionada.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VSTO.NewFormRegionWizard.OFSPropertyError
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b22870cdb038adee84adc0fd7a56c269cb048626
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841925"
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
