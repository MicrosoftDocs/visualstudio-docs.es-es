---
title: Asociar un área de formulario a una clase de mensaje de Outlook
ms.date: 02/02/2017
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5795931b5d964b6eb7a104338756066068f38510
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53923353"
---
# <a name="associate-a-form-region-with-an-outlook-message-class"></a>Asociar un área de formulario a una clase de mensaje de Outlook
  Puede especificar qué elementos de Microsoft Office Outlook muestran un área de formulario al asociar el área de formulario con la clase de mensaje de cada elemento. Por ejemplo, si desea anexar un área de formulario a la parte inferior de un elemento de correo, puede asociar el área de formulario con el `IPM.Note` message (clase).  
  
 Para asociar un área de formulario a una clase de mensaje, especifique el nombre de clase de mensaje en el **nueva área de formulario de Outlook** asistente o aplicar un atributo a la clase de generador de áreas de formulario.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="understand-outlook-message-classes"></a>Comprender las clases de mensaje de Outlook  
 Una clase de mensaje de Outlook identifica un tipo de elemento de Outlook. En la tabla siguiente se enumera los ocho tipos estándar de elementos y sus nombres de clase de mensaje.  
  
|Tipo de elemento de Outlook|Nombre de la clase de mensaje|  
|-----------------------|------------------------|  
|Objeto AppointmentItem|`IPM.Appointment`|  
|Objeto ContactItem|`IPM.Contact`|  
|DistListItem|`IPM.DistList`|  
|JournalItem|`IPM.Activity`|  
|Objeto MailItem|`IPM.Note`|  
|PostItem|`IPM.Post` o `IPM.Post.RSS`|  
|Objeto TaskItem|`IPM.Task`|  
  
 También puede especificar los nombres de clases de mensaje personalizadas. Clases de mensaje personalizadas identifican los formularios personalizados que defina en Outlook.  
  
> [!NOTE]  
>  Para las áreas de formulario de reemplazo y de reemplazo total, puede especificar un nuevo nombre de clase de mensaje personalizado. No es necesario usar el nombre de clase de mensaje de un formulario personalizado existente. El nombre de la clase de mensaje personalizado debe ser único. Una manera de asegurarse de que el nombre sea único es usar una convención de nomenclatura similar al siguiente: \<*NombreDeClaseDeMensajeEstándar*>.\< *Empresa*>.\< *NombreDeClaseDeMensaje*> (por ejemplo: `IPM.Note.Contoso.MyMessageClass`).  
  
## <a name="associate-a-form-region-with-an-outlook-message-class"></a>Asociar un área de formulario a una clase de mensaje de Outlook  
 Hay dos formas de asociar un área de formulario a una clase de mensaje:  
  
-   Use la **nueva área de formulario de Outlook** asistente.  
  
-   Aplicar atributos de clase.  
  
### <a name="use-the-new-outlook-form-region-wizard"></a>Use el Asistente para la nueva área de formulario de Outlook  
 En la página final de la **nueva área de formulario de Outlook** asistente, puede seleccionar las clases de mensaje estándar y escriba los nombres de clases de mensaje personalizadas que desee asociar al área de formulario.  
  
 Las clases de mensaje estándar no están disponibles si el área de formulario está diseñado para reemplazar todo el formulario o la página predeterminada de un formulario. Puede especificar los nombres de clase de mensaje estándar solo para los formularios que agregue una nueva página a un formulario o que se anexan a la parte inferior de un formulario. Para obtener más información, vea [Cómo: Agregar un área de formulario a un proyecto de complemento de Outlook en](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
 Para incluir una o más clases de mensaje personalizado, escriba sus nombres en el **qué clases de mensaje personalizadas mostrarán esta área de formulario?** cuadro.  
  
 Los nombres que escriba deben ser compatible con las siguientes directrices:  
  
- Use el nombre de clase de mensaje completo (por ejemplo: "IPM. ("Note.Contoso").  
  
- Use punto y coma para separar varios nombres de clase de mensaje.  
  
- No incluya clases de mensaje estándar de Outlook, como "IPM. Tenga en cuenta"o"IPM. Póngase en contacto con". Incluir solo las clases de mensaje personalizadas, como "IPM. Note.Contoso".  
  
- No se especifica la clase base message por sí mismo (por ejemplo: "IPM").  
  
- No superar los 256 caracteres para cada nombre de clase de mensaje.  
  
  El **nueva área de formulario de Outlook** asistente valida el formato de la entrada al hacer clic en **finalizar**.  
  
> [!NOTE]  
>  El **nueva área de formulario de Outlook** asistente no comprueba que los nombres de clase de mensaje que proporciona son correctos o válidos.  
  
 Cuando se completa el asistente, el **nueva área de formulario de Outlook** asistente aplica los atributos a la clase de áreas de formulario que contienen los nombres de clase de mensaje especificado. También puede aplicar estos atributos manualmente.  
  
### <a name="apply-class-attributes"></a>Aplicar atributos de clase  
 Puede asociar un área de formulario a una clase de mensaje de Outlook después de completar la **nueva área de formulario de Outlook** asistente. Para ello, aplicar atributos a la clase de generador de áreas de formulario.  
  
 El ejemplo siguiente muestra dos <xref:Microsoft.Office.Tools.Outlook.FormRegionMessageClassAttribute> atributos que se han aplicado a una clase de generador de áreas de formulario denominada `myFormRegion`. El primer atributo asocia el área de formulario a una clase de mensaje estándar para un formulario de mensaje de correo electrónico. El segundo atributo asocia el área de formulario a una clase de mensaje personalizado denominada `IPM.Task.Contoso`.  
  
 [!code-vb[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Attributes/FormRegion1.vb#1)]
 [!code-csharp[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Attributes/FormRegion1.cs#1)]  
  
 Los atributos deben ser compatible con las siguientes directrices:  
  
- Para las clases de mensaje personalizado, utilice el nombre de clase de mensaje completo (por ejemplo: "IPM. ("Note.Contoso").  
  
- No se especifica la clase base message por sí mismo (por ejemplo: "IPM").  
  
- No superar los 256 caracteres para cada nombre de clase de mensaje.  
  
- No se incluyen los nombres de las clases de mensaje estándar si el área de formulario reemplaza todo el formulario o la página predeterminada de un formulario. Puede especificar los nombres de clase de mensaje estándar solo para los formularios que agregue una nueva página a un formulario o que se anexan a la parte inferior de un formulario. Para obtener más información, vea [Cómo: Agregar un área de formulario a un proyecto de complemento de Outlook en](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
  Visual Studio valida el formato de los nombres de clase de mensaje al compilar el proyecto.  
  
> [!NOTE]  
>  Visual Studio no comprueba que los nombres de clase de mensaje que proporciona son correctos o válidos.  
  
## <a name="see-also"></a>Vea también  
 [Obtener acceso a un área de formulario en tiempo de ejecución](../vsto/accessing-a-form-region-at-run-time.md)   
 [Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md)   
 [Tutorial: Diseñar un formulario de Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Directrices para crear áreas de formulario de Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [Nombre del formulario y el mensaje de información general de clases](/office/vba/outlook/Concepts/Forms/form-name-and-message-class-overview)   
 [Cómo funcionan conjuntamente los elementos y formularios de Outlook](/office/vba/outlook/Concepts/Forms/how-outlook-forms-and-items-work-together)  
