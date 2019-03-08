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
ms.openlocfilehash: 0044991b330594d80422f0c6ac1d1d64b1fec237
ms.sourcegitcommit: b7f25ae08e45fcaa84a84276b588cf6799cc7620
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/07/2019
ms.locfileid: "57567188"
---
# <a name="custom-actions-in-outlook-form-regions"></a>Acciones personalizadas en áreas de formulario de Outlook
  Acciones muestran los botones que permiten a los usuarios respondan a un elemento de Microsoft Office Outlook. Por ejemplo, para responder a un elemento de correo, los usuarios hacen clic los **respuesta**, **responder a todos**, o **reenviar** botones de acción. Cada una de estas acciones crea un nuevo elemento de correo y rellena los campos del elemento mediante el uso de información del elemento original.

 Puede crear una acción personalizada que se abre cualquier tipo de elemento de Outlook. Por ejemplo, puede agregar una acción personalizada que se abre un nuevo elemento de cita o tarea. Establecer las propiedades de una acción personalizada o usar código personalizado para rellenar los campos del nuevo elemento. Acciones personalizadas aparecen en la **acciones personalizadas** lista desplegable de un elemento que está abierto en una ventana del inspector de Outlook.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="add-custom-actions-to-a-form-region"></a>Agregar acciones personalizadas a un área de formulario
 Para agregar una acción personalizada a un área de formulario, utilice el **acciones personalizadas** cuadro de diálogo. Puede abrir el **acciones personalizadas** cuadro de diálogo, seleccione el área de formulario en **el Explorador de soluciones**, expandiendo el **manifiesto** nodo en el **propiedades Ventana**, seleccionando la **elemento CustomAction** propiedad y, a continuación, haga clic en el botón de puntos suspensivos (![elipse Diseñador de ASP.NET mobile](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile Elipse del diseñador")).

 Puede usar el **acciones personalizadas** cuadro de diálogo para especificar un *formulario de destino*. Un formulario de destino es el formulario que aparece cuando el usuario ejecuta la acción personalizada.

 También puede usar el **acciones personalizadas** cuadro de diálogo para especificar cómo desea que la información del elemento original que aparezcan en el formulario de destino.

 En la tabla siguiente se describe las propiedades que están disponibles en el **acciones personalizadas** cuadro de diálogo.

|Property|Descripción|
|--------------|-----------------|
|**AddressLike**|Especifica cómo se abordará el formulario de destino.|
|**Cuerpo**|Especifica cómo se anexa el cuerpo del elemento original en el formulario de destino.|
|**Habilitado**|Indica si está habilitada la acción personalizada. Si esta propiedad se establece en **false**, se deshabilita la acción personalizada.|
|**Método**|Especifica el tipo de respuesta disponible cuando se ejecuta la acción personalizada. La acción personalizada puede enviar el formulario, abra el formulario o preguntar al usuario si desea volver a enviar o abrir el formulario.|
|**Name**|Especifica el nombre interno que puede usar para hacer referencia a esta acción personalizada en el código.|
|**ShowOnRibbon**|Indica si se debe mostrar la acción personalizada en la cinta de opciones del elemento original.|
|**SubjectPrefix**|Especifica el texto que se inserta al principio de la línea de asunto del formulario de destino.|
|**TargetForm**|Especifica el nombre de clase de mensaje del formulario de destino. Por ejemplo, escriba **IPM. Tarea** para abrir un formulario de tareas.|
|**Título**|Especifica la etiqueta del botón de acción personalizada.|

## <a name="customize-a-custom-action-at-runtime"></a>Personalizar una acción personalizada en tiempo de ejecución
 También puede agregar comportamiento a la acción personalizada mediante código. Por ejemplo, puede agregar código que toma los nombres de los destinatarios de correo electrónico y agrega dichos nombres como asistentes en un nuevo elemento de cita. Para ello, controle el [CustomAction](/office/vba/api/Outlook.MailItem.CustomAction) eventos de la [objeto MailItem](/office/vba/api/Outlook.MailItem).

## <a name="see-also"></a>Vea también
- [Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md)
- [Tutorial: Diseñar un formulario de Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Asociar un área de formulario a una clase de mensaje de Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
