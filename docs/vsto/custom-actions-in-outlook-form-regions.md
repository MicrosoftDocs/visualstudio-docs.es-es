---
title: Acciones personalizadas en áreas de formulario de Outlook
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], custom actions
- custom actions [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 817cf9fe8698c2908e873246a8971f90fe72b460
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2019
ms.locfileid: "71254438"
---
# <a name="custom-actions-in-outlook-form-regions"></a>Acciones personalizadas en áreas de formulario de Outlook
  Acciones que muestran botones que permiten a los usuarios responder a un Microsoft Office elemento de Outlook. Por ejemplo, para responder a un elemento de correo, los usuarios pueden hacer clic en los botones **responder**, **responder a todos**o **reenviar** acción. Cada una de estas acciones crea un nuevo elemento de correo y rellena los campos del elemento usando información del elemento original.

 Puede crear una acción personalizada que abra cualquier tipo de elemento de Outlook. Por ejemplo, puede Agregar una acción personalizada que abra una nueva cita o elemento de tarea. Establezca las propiedades de una acción personalizada o use código personalizado para rellenar los campos del nuevo elemento. Las acciones personalizadas aparecen en la lista desplegable **acciones personalizadas** de un elemento que está abierto en una ventana del inspector de Outlook.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="add-custom-actions-to-a-form-region"></a>Agregar acciones personalizadas a un área de formulario
 Para agregar una acción personalizada a un área de formulario, use el cuadro de diálogo **acciones personalizadas** . Para abrir el cuadro de diálogo **acciones personalizadas** , seleccione el área de formulario en **Explorador de soluciones**, expanda el nodo **manifiesto** en la **ventana Propiedades**, seleccione la propiedad **CustomActions** y, a continuación, haga clic en el botón de puntos suspensivos (![ASP.NET Mobile Designer ellipse](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile Designer Ellipse")).

 Puede usar el cuadro de diálogo **acciones personalizadas** para especificar un *formulario de destino*. Un formulario de destino es el formulario que aparece cuando el usuario ejecuta la acción personalizada.

 También puede usar el cuadro de diálogo **acciones personalizadas** para especificar cómo desea que la información del elemento original aparezca en el formulario de destino.

 En la tabla siguiente se describen las propiedades que están disponibles en el cuadro de diálogo **acciones personalizadas** .

|Propiedad.|Descripción|
|--------------|-----------------|
|**AddressLike**|Especifica cómo se dirigirá el formulario de destino.|
|**Cuerpo**|Especifica cómo se anexa el cuerpo del elemento original al formulario de destino.|
|**Habilitado**|Indica si la acción personalizada está habilitada. Si esta propiedad se establece en **false**, se deshabilita la acción personalizada.|
|**Método**|Especifica el tipo de respuesta disponible cuando se ejecuta la acción personalizada. La acción personalizada puede enviar el formulario, abrir el formulario o preguntar al usuario si desea enviar o abrir el formulario.|
|**Name**|Especifica el nombre interno que se puede usar para hacer referencia a esta acción personalizada en el código.|
|**ShowOnRibbon**|Indica si se va a mostrar la acción personalizada en la cinta de opciones del elemento original.|
|**SubjectPrefix**|Especifica el texto que se inserta al principio de la línea de asunto del formulario de destino.|
|**TargetForm**|Especifica el nombre de la clase de mensaje del formulario de destino. Por ejemplo, escriba **IPM. Tarea** para abrir un formulario de tareas.|
|**Título**|Especifica la etiqueta del botón de acción personalizada.|

## <a name="customize-a-custom-action-at-run-time"></a>Personalizar una acción personalizada en tiempo de ejecución
 También puede Agregar el comportamiento a la acción personalizada mediante código. Por ejemplo, puede agregar código que tome los nombres de los destinatarios de correo electrónico y agregue esos nombres como asistentes en un nuevo elemento de cita. Para ello, controle el evento [CustomAction](/office/vba/api/Outlook.MailItem.CustomAction) del [objeto MailItem](/office/vba/api/Outlook.MailItem).

## <a name="see-also"></a>Vea también
- [Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md)
- [Tutorial: Diseñar un área de formulario de Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Asociar un área de formulario a una clase de mensaje de Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
