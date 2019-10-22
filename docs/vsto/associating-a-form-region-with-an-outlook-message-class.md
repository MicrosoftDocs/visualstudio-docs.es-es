---
title: Asociar un área de formulario a una clase de mensaje de Outlook
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 45db262b6bf7843a3893c5d60f0b6eaea5fcb70b
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2019
ms.locfileid: "71254577"
---
# <a name="associate-a-form-region-with-an-outlook-message-class"></a>Asociar un área de formulario a una clase de mensaje de Outlook
  Puede especificar qué elementos de Outlook Microsoft Office muestran un área de formulario asociando el área de formulario a la clase de mensaje de cada elemento. Por ejemplo, si desea anexar un área de formulario a la parte inferior de un elemento de correo, puede asociar el área de `IPM.Note` formulario a la clase de mensaje.

 Para asociar un área de formulario a una clase de mensaje, especifique el nombre de la clase de mensaje en el asistente **nueva área de formulario de Outlook** o aplique un atributo a la clase de generador de áreas de formulario.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="understand-outlook-message-classes"></a>Descripción de las clases de mensaje de Outlook
 Una clase de mensaje de Outlook identifica un tipo de elemento de Outlook. En la tabla siguiente se enumeran los ocho tipos estándar de elementos y sus nombres de clase de mensaje.

|Tipo de elemento de Outlook|Nombre de clase de mensaje|
|-----------------------|------------------------|
|AppointmentItem|`IPM.Appointment`|
|ContactItem|`IPM.Contact`|
|Evento|`IPM.DistList`|
|JournalItem|`IPM.Activity`|
|MailItem|`IPM.Note`|
|Elemento PostItem|`IPM.Post` o `IPM.Post.RSS`|
|TaskItem|`IPM.Task`|

 También puede especificar los nombres de las clases de mensaje personalizadas. Las clases de mensaje personalizadas identifican los formularios personalizados que se definen en Outlook.

> [!NOTE]
> En el caso de las áreas de formulario de reemplazo y reemplazo de todos, puede especificar un nuevo nombre de clase de mensaje personalizado. No es necesario usar el nombre de clase de mensaje de un formulario personalizado existente. El nombre de la clase de mensaje personalizada debe ser único. Una manera de asegurarse de que el nombre es único es usar una Convención de nomenclatura similar a la siguiente: \<> *StandardMessageClassName*. > De la *compañía.* \< > MessageClassName (por ejemplo: `IPM.Note.Contoso.MyMessageClass`). \<

## <a name="associate-a-form-region-with-an-outlook-message-class"></a>Asociar un área de formulario a una clase de mensaje de Outlook
 Hay dos formas de asociar un área de formulario a una clase de mensaje:

- Use el asistente **nueva área de formulario de Outlook** .

- Aplicar atributos de clase.

### <a name="use-the-new-outlook-form-region-wizard"></a>Usar el asistente nueva área de formulario de Outlook
 En la página final del asistente **nueva área de formulario de Outlook** , puede seleccionar clases de mensaje estándar y escribir los nombres de las clases de mensaje personalizadas que desee asociar al área de formulario.

 Las clases de mensaje estándar no están disponibles si el área de formulario está diseñada para reemplazar todo el formulario o la página predeterminada de un formulario. Los nombres de clase de mensaje estándar solo se pueden especificar para los formularios que agregan una nueva página a un formulario o que se anexan a la parte inferior de un formulario. Para obtener más información, vea [Cómo: Agregar un área de formulario a un proyecto](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)de complemento de Outlook.

 Para incluir una o varias clases de mensaje personalizadas, escriba sus nombres en el cuadro **¿Qué clases de mensaje personalizadas mostrarán este área de formulario?** .

 Los nombres que escriba deben cumplir las siguientes directrices:

- Use el nombre completo de la clase de mensaje (por ejemplo: Plaga. Nota. contoso ").

- Use punto y coma para separar varios nombres de clase de mensaje.

- No incluya clases de mensaje estándar de Outlook, como "IPM. Note "or" IPM. Contacto ". Incluya solo clases de mensaje personalizadas, como "IPM. Nota. contoso ".

- No especifique la clase de mensaje base por sí sola (por ejemplo: "IPM").

- No supere los 256 caracteres por cada nombre de clase de mensaje.

  El asistente **nueva área de formulario de Outlook** valida el formato de la entrada al hacer clic en **Finalizar**.

> [!NOTE]
> El asistente **nueva área de formulario de Outlook** no comprueba que los nombres de clase de mensaje que proporcione sean correctos o válidos.

 Al completar el asistente, el asistente **nueva área de formulario de Outlook** aplica los atributos a la clase de área de formulario que contiene los nombres de clase de mensaje especificados. También puede aplicar estos atributos manualmente.

### <a name="apply-class-attributes"></a>Aplicar atributos de clase
 Puede asociar un área de formulario a una clase de mensaje de Outlook después de completar el asistente **nueva área de formulario de Outlook** . Para ello, aplique los atributos a la clase de generador de áreas de formulario.

 En el ejemplo siguiente se <xref:Microsoft.Office.Tools.Outlook.FormRegionMessageClassAttribute> muestran dos atributos que se han aplicado a una clase de generador `myFormRegion`de áreas de formulario denominada. El primer atributo asocia el área de formulario a una clase de mensaje estándar para un formulario de mensaje de correo. El segundo atributo asocia el área de formulario a una clase de mensaje `IPM.Task.Contoso`personalizada denominada.

 [!code-vb[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Attributes/FormRegion1.vb#1)]
 [!code-csharp[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Attributes/FormRegion1.cs#1)]

 Los atributos deben cumplir las siguientes directrices:

- En el caso de las clases de mensaje personalizadas, utilice el nombre completo de la clase de mensaje (por ejemplo: Plaga. Nota. contoso ").

- No especifique la clase de mensaje base por sí sola (por ejemplo: "IPM").

- No supere los 256 caracteres por cada nombre de clase de mensaje.

- No incluya los nombres de las clases de mensaje estándar si el área de formulario reemplaza todo el formulario o la página predeterminada de un formulario. Los nombres de clase de mensaje estándar solo se pueden especificar para los formularios que agregan una nueva página a un formulario o que se anexan a la parte inferior de un formulario. Para obtener más información, vea [Cómo: Agregar un área de formulario a un proyecto](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)de complemento de Outlook.

  Visual Studio valida el formato de los nombres de clase de mensaje al compilar el proyecto.

> [!NOTE]
> Visual Studio no comprueba que los nombres de clase de mensaje que proporcione sean correctos o válidos.

## <a name="see-also"></a>Vea también
- [Obtener acceso a un área de formulario en tiempo de ejecución](../vsto/accessing-a-form-region-at-run-time.md)
- [Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md)
- [Tutorial: Diseñar un área de formulario de Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Instrucciones para crear áreas de formulario de Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Información general sobre el nombre de formulario y la clase de mensaje](/office/vba/outlook/Concepts/Forms/form-name-and-message-class-overview)
- [Cómo funcionan los formularios y elementos de Outlook juntos](/office/vba/outlook/Concepts/Forms/how-outlook-forms-and-items-work-together)
