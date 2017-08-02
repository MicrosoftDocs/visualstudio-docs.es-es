---
title: "Informaci&#243;n general sobre el modelo de objetos de Outlook"
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
  - "VST.ProjectItem.OutlookAddin"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Outlook [desarrollo de Office en Visual Studio], información general del modelo de objeto"
  - "modelos de objeto [desarrollo de Office en Visual Studio], Office"
  - "objetos [desarrollo de Office en Visual Studio], modelos de objeto de Office"
  - "modelos de objeto [desarrollo de Office en Visual Studio], Outlook"
  - "modelos de objetos de Office"
ms.assetid: 59704974-b7d9-46d6-949c-e97349c75279
caps.latest.revision: 59
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 58
---
# Informaci&#243;n general sobre el modelo de objetos de Outlook
  Para desarrollar complementos de VSTO para Microsoft Office Outlook, puede interactuar con los objetos que ofrece el modelo de objetos de Outlook. El modelo de objetos de Outlook proporciona clases e interfaces que representan elementos de la interfaz de usuario. Por ejemplo, el objeto <xref:Microsoft.Office.Interop.Outlook.Application> representa toda la aplicación, el objeto <xref:Microsoft.Office.Interop.Outlook.MAPIFolder> representa una carpeta que contiene mensajes de correo electrónico u otros elementos y el objeto <xref:Microsoft.Office.Interop.Outlook.MailItem> representa un mensaje de correo electrónico.  
  
 En este tema se proporciona una breve introducción de algunos de los objetos principales del modelo de objetos de Outlook. Para acceder a recursos de los que pueda obtener más información sobre todo el modelo de objetos de Outlook, vea [Usar la documentación del modelo de objetos de Outlook](#refdoc).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 ![vínculo a vídeo](~/docs/data-tools/media/playvideo.gif "vínculo a vídeo") Para ver una demostración en vídeo relacionada, consulte [Cómo: usar Outlook para crear un informe de tarea personalizado](http://go.microsoft.com/fwlink/?LinkID=130315).  
  
## Acceder a los objetos de un proyecto de Outlook  
 Outlook proporciona muchos objetos con los que puede interactuar. Para usar el modelo de objetos de forma eficaz, debe estar familiarizado con los siguientes objetos de nivel superior:  
  
-   <xref:Microsoft.Office.Interop.Outlook.Application>  
  
-   <xref:Microsoft.Office.Interop.Outlook.Explorer>  
  
-   <xref:Microsoft.Office.Interop.Outlook.Inspector>  
  
-   <xref:Microsoft.Office.Interop.Outlook.MAPIFolder>  
  
-   <xref:Microsoft.Office.Interop.Outlook.MailItem>  
  
-   <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>  
  
-   <xref:Microsoft.Office.Interop.Outlook.TaskItem>  
  
-   <xref:Microsoft.Office.Interop.Outlook.ContactItem>  
  
### Objeto de aplicación  
 El objeto <xref:Microsoft.Office.Interop.Outlook.Application> representa la aplicación Outlook y es el objeto de nivel superior en el modelo de objetos de Outlook. Algunos de los miembros más importantes de este objeto son:  
  
-   El método [CreateItem](http://msdn.microsoft.com/es-es/771707fb-5f34-473d-9fdf-09a6a7f55ece), que puede usar para crear un nuevo elemento, como un mensaje de correo electrónico, una tarea o una cita.  
  
-   La propiedad <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A>, que puede usar para acceder a las ventanas que muestran el contenido de una carpeta en la interfaz de usuario \(UI\) de Outlook.  
  
-   La propiedad <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A>, que puede usar para acceder a las ventanas que muestran el contenido de un elemento único, como una solicitud de reunión o mensaje de correo electrónico.  
  
 Para obtener una instancia del objeto <xref:Microsoft.Office.Interop.Outlook.Application>, use el campo Application de la clase `ThisAddIn` en su proyecto. Para obtener más información, consulta [Programar complementos de VSTO](../vsto/programming-vsto-add-ins.md).  
  
> [!NOTE]  
>  Para evitar las advertencias de seguridad al usar propiedades y métodos bloqueados por el guardián del modelo de objetos de Outlook, obtenga objetos de Outlook desde el campo Application de la clase `ThisAddIn`. Para obtener más información, consulta [Consideraciones de seguridad específicas para soluciones de Office](../vsto/specific-security-considerations-for-office-solutions.md).  
  
### Objeto Explorer  
 El objeto <xref:Microsoft.Office.Interop.Outlook.Explorer> representa una ventana que muestra el contenido de una carpeta que contiene elementos como mensajes de correo electrónico, tareas o citas. El objeto <xref:Microsoft.Office.Interop.Outlook.Explorer> incluye métodos y propiedades que puede usar para modificar la ventana, así como eventos que se generan cuando cambia la ventana.  
  
 Para obtener un objeto <xref:Microsoft.Office.Interop.Outlook.Explorer>, realice una de las acciones siguientes:  
  
-   Use la propiedad <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A> del objeto <xref:Microsoft.Office.Interop.Outlook.Application> para acceder a todos los objetos <xref:Microsoft.Office.Interop.Outlook.Explorer> de Outlook.  
  
-   Use el método <xref:Microsoft.Office.Interop.Outlook._Application.ActiveExplorer%2A> del objeto <xref:Microsoft.Office.Interop.Outlook.Application> para obtener el <xref:Microsoft.Office.Interop.Outlook.Explorer> que tenga actualmente el foco.  
  
-   Use el método GetExplorer del objeto <xref:Microsoft.Office.Interop.Outlook.MAPIFolder> para obtener el <xref:Microsoft.Office.Interop.Outlook.Explorer> de la carpeta actual.  
  
### Objeto Inspector  
 El objeto <xref:Microsoft.Office.Interop.Outlook.Inspector> representa una ventana que muestra un único elemento como un mensaje de correo electrónico, una tarea o una cita. El objeto <xref:Microsoft.Office.Interop.Outlook.Inspector> incluye métodos y propiedades que puede usar para modificar la ventana, así como eventos que se generan cuando cambia la ventana.  
  
 Para obtener un objeto <xref:Microsoft.Office.Interop.Outlook.Inspector>, realice una de las acciones siguientes:  
  
-   Use la propiedad <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A> del objeto <xref:Microsoft.Office.Interop.Outlook.Application> para acceder a todos los objetos <xref:Microsoft.Office.Interop.Outlook.Inspector> de Outlook.  
  
-   Use el método <xref:Microsoft.Office.Interop.Outlook._Application.ActiveInspector%2A> del objeto <xref:Microsoft.Office.Interop.Outlook.Application> para obtener el <xref:Microsoft.Office.Interop.Outlook.Inspector> que tenga actualmente el foco.  
  
-   Use el método GetInspector de un determinado elemento, como un <xref:Microsoft.Office.Interop.Outlook.MailItem> o <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>, para recuperar el Inspector que está asociado a él.  
  
### Objeto MAPIFolder  
 El objeto <xref:Microsoft.Office.Interop.Outlook.MAPIFolder> representa una carpeta que contiene mensajes de correo electrónico, contactos, tareas y otros elementos. Outlook proporciona 16 objetos <xref:Microsoft.Office.Interop.Outlook.MAPIFolder> predeterminados.  
  
 Los objetos <xref:Microsoft.Office.Interop.Outlook.MAPIFolder> predeterminados se definen mediante los valores de enumeración <xref:Microsoft.Office.Interop.Outlook.OlDefaultFolders>. Por ejemplo,  
  
 Microsoft.Office.Interop.Outlook.OlDefaultFolders.olFolderInbox corresponde a la carpeta **Bandeja de entrada** de Outlook.  
  
 Para obtener un ejemplo en el que se muestra cómo acceder a un elemento <xref:Microsoft.Office.Interop.Outlook.MAPIFolder> predeterminado y crear un nuevo elemento <xref:Microsoft.Office.Interop.Outlook.MAPIFolder>, consulte [Cómo: Crear elementos de carpeta personalizados mediante programación](../vsto/how-to-programmatically-create-custom-folder-items.md).  
  
### Objeto MailItem  
 El objeto <xref:Microsoft.Office.Interop.Outlook.MailItem> representa un mensaje de correo electrónico. Los objetos <xref:Microsoft.Office.Interop.Outlook.MailItem> normalmente están en carpetas, como **Bandeja de entrada**, **Elementos enviados** y **Bandeja de salida**.<xref:Microsoft.Office.Interop.Outlook.MailItem> expone propiedades y métodos que se pueden usar para crear y enviar mensajes de correo electrónico.  
  
 Para obtener un ejemplo en el que se muestra cómo crear un mensaje de correo electrónico, consulte [Cómo: Crear un elemento de correo electrónico mediante programación](../vsto/how-to-programmatically-create-an-e-mail-item.md).  
  
### Objeto AppointmentItem  
 El objeto <xref:Microsoft.Office.Interop.Outlook.AppointmentItem> representa una reunión, una cita única o una reunión o cita periódica en la carpeta **Calendario**. El objeto <xref:Microsoft.Office.Interop.Outlook.AppointmentItem> incluye métodos que realizan acciones, como responder o reenviar convocatorias de reunión y propiedades que especifican los detalles de la reunión, como la ubicación y la hora.  
  
 Para obtener un ejemplo en el que se muestra cómo crear una cita, vea [Cómo: Crear una convocatoria de reunión mediante programación](../vsto/how-to-programmatically-create-a-meeting-request.md).  
  
### Objeto TaskItem  
 El objeto <xref:Microsoft.Office.Interop.Outlook.TaskItem> representa una tarea que debe realizarse dentro de un período de tiempo especificado. Los objetos <xref:Microsoft.Office.Interop.Outlook.TaskItem> se encuentran en la carpeta **Tareas**.  
  
 Para crear una tarea, use el método [CreateItem](http://msdn.microsoft.com/es-es/771707fb-5f34-473d-9fdf-09a6a7f55ece) del objeto <xref:Microsoft.Office.Interop.Outlook.Application> y pase el valor <xref:Microsoft.Office.Interop.Outlook.OlItemType.olTaskItem> para el parámetro.  
  
### Objeto ContactItem  
 El objeto <xref:Microsoft.Office.Interop.Outlook.ContactItem>representa un contacto de la carpeta **Contactos**. Los objetos <xref:Microsoft.Office.Interop.Outlook.ContactItem> contienen una gran variedad de información de contacto de las personas que representan, como direcciones postales, direcciones de correo electrónico y números de teléfono.  
  
 Para obtener un ejemplo en el que se muestra cómo crear un nuevo contacto, consulte [Cómo: Agregar una entrada a los contactos de Outlook mediante programación](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md). Para obtener un ejemplo en el que se muestra cómo buscar un contacto ya existente, vea [Cómo: Buscar un contacto específico mediante programación](../vsto/how-to-programmatically-search-for-a-specific-contact.md).  
  
##  <a name="refdoc"></a> Usar la documentación del modelo de objetos de Outlook  
 Para obtener información completa sobre el modelo de objetos de Outlook, puede consultar la referencia del ensamblado de interoperabilidad primario \(PIA\) de Outlook y la referencia del modelo de objetos VBA.  
  
### Referencia de ensamblado de interoperabilidad primario  
 La referencia de PIA de Outlook documenta los tipos en los ensamblados de interoperabilidad primarios para Outlook 2010. Para más información, consulte [Referencia de ensamblado de interoperabilidad primario de Outlook 2010](http://go.microsoft.com/fwlink/?LinkId=189580).  
  
 Además de proporcionar información de todos los tipos de los PIA, esta documentación proporciona información adicional acerca de la estructura de los PIA y ejemplos de código de tareas comunes de automatización de Outlook.  
  
### Referencia del modelo de objetos de VBA  
 La referencia del modelo de objetos de VBA documenta el modelo de objetos de Outlook tal como se expone al código de Visual Basic para Aplicaciones \(VBA\). Para más información, consulte [Referencia del modelo de objetos de Outlook 2010](http://go.microsoft.com/fwlink/?LinkId=199769).  
  
 Todos los objetos y miembros de la referencia del modelo de objetos de VBA corresponden a tipos y miembros del PIA de Outlook. Por ejemplo, el objeto Inspector en la referencia del modelo de objetos VBA corresponde al objeto <xref:Microsoft.Office.Interop.Outlook.Inspector> del PIA de Outlook. Aunque la referencia del modelo de objetos VBA proporciona ejemplos de código para la mayoría de las propiedades, métodos y eventos, debe traducir el código VBA de esta referencia a Visual Basic o Visual C\# si quiere usarlo en un proyecto de complemento de VSTO de Outlook creado con Visual Studio.  
  
### Temas relacionados  
  
|Título|Descripción|  
|------------|-----------------|  
|[Trabajar con contactos](../vsto/working-with-contact-items.md)|Proporciona temas que muestran cómo realizar tareas con los contactos.|  
|[Trabajar con elementos de correo](../vsto/working-with-mail-items.md)|Proporciona temas que muestran cómo realizar tareas con los elementos de correo.|  
|[Trabajar con carpetas](../vsto/working-with-folders.md)|Proporciona temas que muestran cómo realizar tareas con carpetas.|  
|[Trabajar con elementos del calendario](../vsto/working-with-calendar-items.md)|Proporciona temas que muestran cómo realizar tareas con elementos del calendario.|  
|[Cómo: Determinar el elemento actual de Outlook mediante programación](../vsto/how-to-programmatically-determine-the-current-outlook-item.md)|Muestra cómo mostrar el nombre de la carpeta actual y alguna información sobre el elemento seleccionado.|  
  
  