---
title: "Acciones personalizadas en &#225;reas de formulario de Outlook | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "acciones personalizadas [desarrollo de Office en Visual Studio]"
  - "áreas de formulario [desarrollo de Office en Visual Studio], acciones personalizadas"
ms.assetid: 583fd5f0-aafa-4858-9c54-38a9fdf3bede
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Acciones personalizadas en &#225;reas de formulario de Outlook
  Las acciones muestran botones que permiten a los usuarios responder a un elemento de Microsoft Office Outlook.  Por ejemplo, para responder a un elemento de correo, los usuarios hacen clic en los botones de acción **Responder**, **Responder a todos** o **Reenviar**.  Cada una de estas acciones crea un nuevo elemento de correo y rellena los campos del elemento utilizando información del elemento original.  
  
 Puede crear una acción personalizada que abra cualquier tipo de elemento de Outlook.  Por ejemplo, puede agregar una acción personalizada que abra un nuevo elemento de cita o tarea.  Establezca las propiedades de una acción personalizada o utilice código personalizado para rellenar los campos del nuevo elemento.  Las acciones personalizadas aparecen en la listas desplegable **Acciones personalizadas** de un elemento que está abierto en una ventana de inspector de Outlook.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Agregar acciones personalizadas a un área de formulario  
 Para agregar una acción personalizada a un área de formulario, utilice el cuadro de diálogo **Acciones personalizadas**.  Puede abrir el cuadro de diálogo **Acciones personalizadas** en **Explorador de soluciones** expandiendo el nodo **Manifiesto** , seleccione la propiedad **CustomActions** , haga clic en los puntos suspensivos \(![Elipse del Diseñador de ASP.NET Mobile](../sharepoint/media/mwellipsis.png "Elipse del Diseñador de ASP.NET Mobile")\).  
  
 Puede utilizar el cuadro de diálogo **Acciones personalizadas** para especificar un *formulario de destino*.  Un formulario de destino es el formulario que aparece cuando el usuario ejecuta la acción personalizada.  
  
 También puede utilizar el cuadro de diálogo **Acciones personalizadas** para especificar cómo desea que aparezca la información del elemento original en el formulario de destino.  
  
 En la tabla siguiente se describen las propiedades disponibles en el cuadro de diálogo **Acciones personalizadas**.  
  
|Propiedad|Descripción|  
|---------------|-----------------|  
|**AddressLike**|Especifica cómo se direccionará el formulario de destino.|  
|**Body**|Especifica cómo se anexa el cuerpo del elemento original al formulario de destino.|  
|**Enabled**|Indica si la acción personalizada está habilitada.  Si esta propiedad se establece en **false**, se deshabilita la acción personalizada.|  
|**Método**|Especifica el tipo de respuesta disponible cuando se ejecuta la acción personalizada.  La acción personalizada puede enviar el formulario, abrir el formulario o preguntar al usuario si desea enviar o abrir el formulario.|  
|**Nombre**|Especifica el nombre interno que puede utilizar para hacer referencia a esta acción personalizada en código.|  
|**ShowOnRibbon**|Indica si la acción personalizada se mostrará en la cinta de opciones del elemento original.|  
|**SubjectPrefix**|Especifica texto que se inserta en el inicio de la línea de asunto del formulario de destino.|  
|**TargetForm**|Especifica el nombre de la clase de mensaje del formulario de destino.  Por ejemplo, escriba **IPM.Task** para abrir un formulario de tareas.|  
|**Título**|Especifica la etiqueta del botón de la acción personalizada.|  
  
## Personalizar una acción personalizada en tiempo de ejecución  
 También puede agregar comportamiento a la acción personalizada mediante código.  Por ejemplo, puede agregar código que recopile los nombres de los destinatarios del correo electrónico y agregue estos nombres como asistentes en un nuevo elemento de cita.  Para ello, controle el evento [CustomAction](HV05247448) del objeto [Action](HV05247650).  
  
## Vea también  
 [Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md)   
 [Tutorial: Diseñar un área de formulario de Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Asociar un área de formulario a una clase de mensaje de Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)  
  
  