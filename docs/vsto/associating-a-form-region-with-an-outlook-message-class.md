---
title: "Asociar un &#225;rea de formulario a una clase de mensaje de Outlook"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VSTO.NewFormRegionWizard.InvalidMessageClassName"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "áreas de formulario [desarrollo de Office en Visual Studio], clases de mensajes"
  - "FormRegionMessageClassAttribute"
ms.assetid: e2db8d61-fd5f-4059-beec-33b66970f520
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# Asociar un &#225;rea de formulario a una clase de mensaje de Outlook
  Puede especificar los elementos de Microsoft Office Outlook que van a mostrar un área de formulario asociando ésta a la clase de mensaje de cada elemento.  Por ejemplo, si desea anexar un área de formulario a la parte inferior de un elemento de correo, puede asociarla a la clase de mensaje IPM.Note.  
  
 Para asociar un área de formulario a una clase de mensaje, especifique el nombre de la clase de mensaje en el asistente **Nueva región de formulario de Outlook** o aplique un atributo a la clase de generador de áreas de formulario.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Descripción de las clases de mensaje de Outlook  
 Una clase de mensaje de Outlook identifica un tipo de elemento de Outlook.  En la tabla siguiente se muestran los ocho tipos estándar de elementos y los nombres de las clases de mensaje.  
  
|Tipo de elemento de Outlook|Nombre de la clase de mensaje|  
|---------------------------------|-----------------------------------|  
|AppointmentItem|IPM.Appointment|  
|ContactItem|IPM.Contact|  
|DistListItem|IPM.DistList|  
|JournalItem|IPM.Activity|  
|MailItem|IPM.Note|  
|PostItem|IPM.Post o IPM.Post.RSS|  
|TaskItem|IPM.Task|  
  
 También puede especificar los nombres de clases de mensaje personalizadas.  Las clases de mensaje personalizadas identifican los formularios personalizados que se definen en Outlook.  
  
> [!NOTE]  
>  Para las áreas de formulario de reemplazo y de reemplazo total, puede especificar un nuevo nombre de clase de mensaje personalizado.  No es necesario utilizar el nombre de clase de mensaje de un formulario personalizado existente.  El nombre de la clase de mensaje personalizada debe ser único.  Para asegurarse de que el nombre es único, utilice una convención de nomenclatura similar a la siguiente: \<*nombreDeClaseDeMensajeEstándar*\>.\<*Compañía*\>.\<*nombreDeClaseDeMensaje*\> \(por ejemplo: IPM.Note.Contoso.MyMessageClass\).  
  
## Asociar una región de formulario a una clase de mensaje de Outlook  
 Un área de formulario se puede asociar a una clase de mensaje de dos maneras:  
  
-   Usando el asistente **Nueva región de formulario de Outlook**.  
  
-   Aplicando atributos de clase.  
  
### Utilizar el asistente Nueva región de formulario de Outlook  
 En la última página del asistente **Nueva región de formulario de Outlook** , puede seleccionar clases de mensaje estándar y escribir los nombres de las clases de mensaje personalizadas que desee asociar al área de formulario.  
  
 Las clases de mensaje estándar no están disponibles si el área de formulario está diseñada para reemplazar todo el formulario o la página predeterminada de un formulario.  Puede especificar nombres de clase de mensaje estándar sólo para los formularios que agregan una nueva página a un formulario o que están anexados a la parte inferior de un formulario.  Para obtener más información, vea [Cómo: Agregar un área de formulario a un proyecto de complemento de Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
 Para incluir una o varias clases de mensaje personalizadas, escriba sus nombres en el cuadro **¿Qué clases de mensaje personalizadas mostrarán esta área de formulario?**  
  
 Los nombres que escriba deberán cumplir las siguientes instrucciones:  
  
-   Utilice el nombre de clase de mensaje completo \(por ejemplo: "IPM.Note.Contoso"\).  
  
-   Utilice los signos de punto y coma para separar varios nombres de clase de mensaje.  
  
-   No incluya clases de mensaje estándar de Outlook, como "IPM.Note" o "IPM.Contact".  Incluya sólo clases de mensaje personalizadas, como "IPM.Note.Contoso".  
  
-   No especifique la clase de mensaje base propiamente dicha \(por ejemplo: "IPM"\).  
  
-   No utilice más de 256 caracteres para cada nombre de clase de mensaje.  
  
 El asistente **Nueva región de formulario de Outlook** validará el formato de los datos proporcionados cuando el usuario haga clic en **Finalizar**.  
  
> [!NOTE]  
>  El asistente **Nueva región de formulario de Outlook** no comprueba si los nombres de clase de mensaje proporcionados son correctos o válidos.  
  
 Cuando complete el asistente **Nueva región de formulario de Outlook**, éste aplicará a la clase de área de formulario los atributos que contienen los nombres de clase de mensaje especificados.  Estos atributos también se pueden aplicar manualmente.  
  
### Aplicar atributos de clase  
 Puede asociar un área de formulario a una clase de mensaje de Outlook después de completar el asistente **Nueva región de formulario de Outlook** .  Para ello, aplique atributos a la clase de generador de áreas de formulario.  
  
 En el ejemplo siguiente se muestran dos atributos <xref:Microsoft.Office.Tools.Outlook.FormRegionMessageClassAttribute> que se han aplicado a una clase de generador de áreas de formulario denominada `myFormRegion`.  El primer atributo asocia el área de formulario a una clase de mensaje estándar para un formulario de mensaje de correo.  El segundo atributo asocia el área de formulario a una clase de mensaje personalizada que se denomina `IPM.Task.Contoso`.  
  
 [!code-csharp[Trin_Outlook_FR_Attributes#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Attributes/CS/FormRegion1.cs#1)]
 [!code-vb[Trin_Outlook_FR_Attributes#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Attributes/VB/FormRegion1.vb#1)]  
  
 Los atributos deben cumplir las siguientes instrucciones:  
  
-   Para las clases de mensaje personalizadas, utilice el nombre de clase de mensaje completo \(por ejemplo: "IPM.Note.Contoso"\).  
  
-   No especifique la clase de mensaje base propiamente dicha \(por ejemplo: "IPM"\).  
  
-   No utilice más de 256 caracteres para cada nombre de clase de mensaje.  
  
-   No incluya los nombres de las clases de mensaje estándar si el área de formulario reemplaza todo el formulario o la página predeterminada de un formulario.  Puede especificar nombres de clase de mensaje estándar sólo para los formularios que agregan una nueva página a un formulario o que están anexados a la parte inferior de un formulario.  Para obtener más información, vea [Cómo: Agregar un área de formulario a un proyecto de complemento de Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
 Visual Studio validará el formato de los nombres de las clases de mensaje cuando se compile el proyecto.  
  
> [!NOTE]  
>  No comprueba si los nombres proporcionados son correctos o válidos.  
  
## Vea también  
 [Obtener acceso a un área de formulario en tiempo de ejecución](../vsto/accessing-a-form-region-at-run-time.md)   
 [Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md)   
 [Tutorial: Diseñar un área de formulario de Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Instrucciones para crear áreas de formulario de Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [Sobre el nombre del formulario y la clase de mensaje](HV01044315)   
 [Cómo Outlook forms y elementos colaboran](HV01044298)  
  
  