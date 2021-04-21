---
title: Asociación de un área de formulario a una clase de mensaje de Outlook
description: Obtenga información sobre cómo especificar qué elementos Microsoft Office Outlook muestran un área de formulario asociando el área de formulario a la clase de mensaje de cada elemento.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VSTO.NewFormRegionWizard.InvalidMessageClassName
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FormRegionMessageClassAttribute
- form regions [Office development in Visual Studio], message classes
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: be3b789fabf00d853d447cb3489ef07a5b494fcd
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826998"
---
# <a name="associate-a-form-region-with-an-outlook-message-class"></a>Asociación de un área de formulario a una clase de mensaje de Outlook
  Puede especificar qué elementos Microsoft Office Outlook muestran un área de formulario asociando el área de formulario a la clase de mensaje de cada elemento. Por ejemplo, si desea anexar un área de formulario a la parte inferior de un elemento de correo, puede asociar el área de formulario a la `IPM.Note` clase de mensaje.

 Para asociar un área de formulario a una clase de mensaje, especifique el nombre de la clase de mensaje en el Asistente para nueva región de formulario de **Outlook** o aplique un atributo a la clase de generador del área de formulario.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="understand-outlook-message-classes"></a>Comprender las clases de mensajes de Outlook
 Una clase de mensaje de Outlook identifica un tipo de elemento de Outlook. En la tabla siguiente se enumeran estos ocho tipos estándar de elementos y sus nombres de clase de mensaje.

|Tipo de elemento de Outlook|Nombre de clase de mensaje|
|-----------------------|------------------------|
|Appointmentitem|`IPM.Appointment`|
|ContactItem|`IPM.Contact`|
|DistListItem|`IPM.DistList`|
|JournalItem|`IPM.Activity`|
|Mailitem|`IPM.Note`|
|PostItem|`IPM.Post` o `IPM.Post.RSS`|
|TaskItem|`IPM.Task`|

 También puede especificar los nombres de las clases de mensaje personalizadas. Las clases de mensajes personalizadas identifican los formularios personalizados que se definen en Outlook.

> [!NOTE]
> Para las regiones de formulario de reemplazo y reemplazo, puede especificar un nuevo nombre de clase de mensaje personalizado. No es necesario usar el nombre de clase de mensaje de un formulario personalizado existente. El nombre de la clase de mensaje personalizada debe ser único. Una manera de asegurarse de que el nombre es único es usar una convención de nomenclatura similar a la siguiente: \<*StandardMessageClassName*> \<*Company*> .\<*MessageClassName*> (por ejemplo: `IPM.Note.Contoso.MyMessageClass` ).

## <a name="associate-a-form-region-with-an-outlook-message-class"></a>Asociación de un área de formulario a una clase de mensaje de Outlook
 Hay dos maneras de asociar un área de formulario a una clase de mensaje:

- Use el **Asistente para nueva área de formulario de Outlook.**

- Aplicar atributos de clase.

### <a name="use-the-new-outlook-form-region-wizard"></a>Usar el Asistente para nueva área de formulario de Outlook
 En la página final del Asistente para nueva área de formulario de **Outlook,** puede seleccionar clases de mensaje estándar y escribir los nombres de las clases de mensaje personalizadas que desea asociar al área de formulario.

 Las clases de mensaje estándar no están disponibles si el área de formulario está diseñada para reemplazar todo el formulario o la página predeterminada de un formulario. Puede especificar nombres de clase de mensaje estándar solo para formularios que agregan una nueva página a un formulario o que se anexan a la parte inferior de un formulario. Para obtener más información, vea Cómo: Agregar un área de formulario a un proyecto [de complemento de Outlook.](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)

 Para incluir una o varias clases de mensaje personalizadas, escriba sus nombres en el cuadro ¿Qué clases de **mensaje personalizadas mostrarán este área de formulario?** .

 Los nombres que escriba deben cumplir las siguientes directrices:

- Use el nombre completo de la clase de mensaje (por ejemplo: "IPM. Nota.Contoso").

- Use punto y coma para separar varios nombres de clase de mensaje.

- No incluya clases de mensajes estándar de Outlook, como "IPM. Nota" o "IPM. Contacto". Incluya solo clases de mensaje personalizadas, como "IPM. Note.Contoso".

- No especifique la clase de mensaje base por sí misma (por ejemplo: "IPM").

- No supere los 256 caracteres para cada nombre de clase de mensaje.

  El **Asistente para nueva área** de formulario de Outlook valida el formato de la entrada al hacer clic en **Finalizar.**

> [!NOTE]
> El **Asistente para nueva región de** formulario de Outlook no comprueba que los nombres de clase de mensaje que proporcione sean correctos o válidos.

 Al completar el asistente, el Asistente para nueva región de formulario de **Outlook** aplica atributos a la clase de área de formulario que contiene los nombres de clase de mensaje especificados. También puede aplicar estos atributos manualmente.

### <a name="apply-class-attributes"></a>Aplicar atributos de clase
 Puede asociar un área de formulario a una clase de mensaje de Outlook después de completar el **Asistente para nueva región de formulario de Outlook.** Para ello, aplique atributos a la clase de generador del área de formulario.

 En el ejemplo siguiente se muestran <xref:Microsoft.Office.Tools.Outlook.FormRegionMessageClassAttribute> dos atributos que se han aplicado a una clase de generador de área de formulario denominada `myFormRegion` . El primer atributo asocia el área de formulario a una clase de mensaje estándar para un formulario de mensaje de correo. El segundo atributo asocia el área de formulario a una clase de mensaje personalizada denominada `IPM.Task.Contoso` .

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Attributes/FormRegion1.vb" id="Snippet1":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Attributes/FormRegion1.cs" id="Snippet1":::

 Los atributos deben cumplir las siguientes directrices:

- Para las clases de mensaje personalizadas, use el nombre completo de la clase de mensaje (por ejemplo: "IPM. Nota.Contoso").

- No especifique la clase de mensaje base por sí misma (por ejemplo: "IPM").

- No supere los 256 caracteres para cada nombre de clase de mensaje.

- No incluya los nombres de las clases de mensaje estándar si el área de formulario reemplaza todo el formulario o la página predeterminada de un formulario. Puede especificar nombres de clase de mensaje estándar solo para formularios que agregan una nueva página a un formulario o que se anexan a la parte inferior de un formulario. Para obtener más información, vea Cómo: Agregar un área [de formulario a un proyecto de complemento de Outlook.](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)

  Visual Studio valida el formato de los nombres de clase de mensaje al compilar el proyecto.

> [!NOTE]
> Visual Studio no comprueba que los nombres de clase de mensaje que proporcione sean correctos o válidos.

## <a name="see-also"></a>Consulte también
- [Acceso a un área de formulario en tiempo de ejecución](../vsto/accessing-a-form-region-at-run-time.md)
- [Creación de regiones de formulario de Outlook](../vsto/creating-outlook-form-regions.md)
- [Tutorial: Diseño de un área de formulario de Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Directrices para crear regiones de formulario de Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Información general sobre el nombre del formulario y la clase de mensaje](/office/vba/outlook/Concepts/Forms/form-name-and-message-class-overview)
- [Cómo funcionan conjuntamente los formularios y elementos de Outlook](/office/vba/outlook/Concepts/Forms/how-outlook-forms-and-items-work-together)
