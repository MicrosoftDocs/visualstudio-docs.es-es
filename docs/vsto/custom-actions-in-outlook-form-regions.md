---
title: "Áreas de formulario de acciones personalizadas en Outlook | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], custom actions
- custom actions [Office development in Visual Studio]
ms.assetid: 583fd5f0-aafa-4858-9c54-38a9fdf3bede
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 89b49139db9d91ba742caeb80308f9175195a843
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="custom-actions-in-outlook-form-regions"></a>Acciones personalizadas en áreas de formulario de Outlook
  Acciones mostrar botones que permiten a los usuarios responder a un elemento de Microsoft Office Outlook. Por ejemplo, para responder a un elemento de correo, los usuarios hacen clic el **respuesta**, **responder a todos**, o **al día** botones de acción. Cada una de estas acciones crea un nuevo elemento de correo y rellena los campos del elemento utilizando información del elemento original.  
  
 Puede crear una acción personalizada que se abre cualquier tipo de elemento de Outlook. Por ejemplo, puede agregar una acción personalizada que se abre un nuevo elemento de cita o tarea. Establecer las propiedades de una acción personalizada o usar código personalizado para rellenar los campos del nuevo elemento. Las acciones personalizadas aparecen en la **acciones personalizadas** desplegable de un elemento que está abierto en una ventana del inspector de Outlook.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="adding-custom-actions-to-a-form-region"></a>Agregar acciones personalizadas a un área de formulario  
 Para agregar una acción personalizada a un área de formulario, use la **acciones personalizadas** cuadro de diálogo. Puede abrir el **acciones personalizadas** cuadro de diálogo de **el Explorador de soluciones** expandiendo el **manifiesto** nodo, al seleccionar el **elemento CustomAction**propiedad y, a continuación, haga clic en el botón de puntos suspensivos (![elipse del Diseñador de ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "elipse del Diseñador de ASP.NET Mobile")).  
  
 Puede usar el **acciones personalizadas** cuadro de diálogo para especificar un *destino formulario*. Un formulario de destino es el formulario que aparece cuando el usuario ejecuta la acción personalizada.  
  
 También puede usar el **acciones personalizadas** cuadro de diálogo para especificar cómo desea que la información del elemento original que aparezcan en el formulario de destino.  
  
 En la tabla siguiente se describe las propiedades que están disponibles en la **acciones personalizadas** cuadro de diálogo.  
  
|Property|Descripción|  
|--------------|-----------------|  
|**AddressLike**|Especifica cómo se enviará el formulario de destino.|  
|**Cuerpo**|Especifica cómo se anexa el cuerpo del elemento original en el formulario de destino.|  
|**Habilitado**|Indica si está habilitada la acción personalizada. Si esta propiedad se establece en **false**, se deshabilita la acción personalizada.|  
|**Método**|Especifica el tipo de respuesta disponible cuando se ejecuta la acción personalizada. La acción personalizada puede enviar el formulario, abra el formulario o preguntar al usuario si desea volver a enviar o abrir el formulario.|  
|**Name**|Especifica el nombre interno que puede utilizar para hacer referencia a esta acción personalizada en el código.|  
|**ShowOnRibbon**|Indica si se debe mostrar la acción personalizada en la cinta de opciones del elemento original.|  
|**SubjectPrefix**|Especifica el texto que se inserta al principio de la línea de asunto del formulario de destino.|  
|**TargetForm**|Especifica el nombre de clase de mensaje del formulario de destino. Por ejemplo, escriba **IPM. Tarea** para abrir un formulario de tareas.|  
|**Título**|Especifica la etiqueta del botón de acción personalizada.|  
  
## <a name="customizing-a-custom-action-at-run-time"></a>Personalizar una acción personalizada en tiempo de ejecución  
 También puede agregar comportamiento a la acción personalizada mediante código. Por ejemplo, puede agregar código que toma los nombres de los destinatarios de correo electrónico y agrega dichos nombres como asistentes en un nuevo elemento de cita. Para ello, controle el [CustomAction](http://msdn.microsoft.com/library/office/ff862186.aspx) eventos de la [objeto MailItem](http://msdn.microsoft.com/library/office/ff861332.aspx).  
  
## <a name="see-also"></a>Vea también  
 [Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md)   
 [Tutorial: Diseñar un área de formulario de Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Asociación de un área de formulario a una clase de mensaje de Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)  
  
  