---
title: Información general sobre el modelo de objetos de Outlook
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.OutlookAddin
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], object model overview
- object models [Office development in Visual Studio], Office
- objects [Office development in Visual Studio], Office object models
- object models [Office development in Visual Studio], Outlook
- Office object models
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b11757990a17a867776376454142e5b84ee82510
ms.sourcegitcommit: 96a6d1f16d06ca28d309d05b6e9fbd52f628cdbc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40008273"
---
# <a name="outlook-object-model-overview"></a>Información general sobre el modelo de objetos de Outlook
  Para desarrollar complementos de VSTO para Microsoft Office Outlook, puede interactuar con los objetos que ofrece el modelo de objetos de Outlook. El modelo de objetos de Outlook proporciona clases e interfaces que representan elementos de la interfaz de usuario. Por ejemplo, el objeto <xref:Microsoft.Office.Interop.Outlook.Application> representa toda la aplicación, el objeto <xref:Microsoft.Office.Interop.Outlook.Folder> representa una carpeta que contiene mensajes de correo electrónico u otros elementos y el objeto <xref:Microsoft.Office.Interop.Outlook.MailItem> representa un mensaje de correo electrónico.  
  
 En este tema se proporciona una breve introducción de algunos de los objetos principales del modelo de objetos de Outlook. Para obtener recursos donde se puede obtener más información acerca de todo el modelo de objetos de Outlook, consulte [usar la documentación del modelo de objetos de Outlook](#refdoc).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 ![vínculo a vídeo](../vsto/media/playvideo.gif "vínculo al vídeo") para una demostración en vídeo relacionada, vea [¿cómo lo hago?: usar Outlook para crear un informe de tarea personalizado?](http://go.microsoft.com/fwlink/?LinkID=130315).  
  
## <a name="access-objects-in-an-outlook-project"></a>Obtener acceso a objetos en un proyecto de Outlook  
 Outlook proporciona muchos objetos con los que puede interactuar. Para usar el modelo de objetos de forma eficaz, debe estar familiarizado con los siguientes objetos de nivel superior:  
  
-   <xref:Microsoft.Office.Interop.Outlook.Application>  
  
-   <xref:Microsoft.Office.Interop.Outlook.Explorer>  
  
-   <xref:Microsoft.Office.Interop.Outlook.Inspector>  
  
-   <xref:Microsoft.Office.Interop.Outlook.Folder>  
  
-   <xref:Microsoft.Office.Interop.Outlook.MailItem>  
  
-   <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>  
  
-   <xref:Microsoft.Office.Interop.Outlook.TaskItem>  
  
-   <xref:Microsoft.Office.Interop.Outlook.ContactItem>  
  
### <a name="application-object"></a>Application (objeto)  
 El objeto <xref:Microsoft.Office.Interop.Outlook.Application> representa la aplicación Outlook y es el objeto de nivel superior en el modelo de objetos de Outlook. Algunos de los miembros más importantes de este objeto son:  
  
-   El [CreateItem](/previous-versions/office/developer/office-2003/aa220082(v=office.11)) método que puede usar para crear un nuevo elemento como un mensaje de correo electrónico, tareas o citas.  
  
-   La propiedad <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A> , que puede usar para acceder a las ventanas que muestran el contenido de una carpeta en la interfaz de usuario (UI) de Outlook.  
  
-   La propiedad <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A> , que puede usar para acceder a las ventanas que muestran el contenido de un elemento único, como una solicitud de reunión o mensaje de correo electrónico.  
  
 Para obtener una instancia de la <xref:Microsoft.Office.Interop.Outlook.Application> de objeto, utilice el campo de la aplicación de la `ThisAddIn` clase del proyecto. Para obtener más información, consulte [complementos VSTO de programa](../vsto/programming-vsto-add-ins.md).  
  
> [!NOTE]  
>  Para ayudar a evitar las advertencias de seguridad al usar propiedades y métodos que están bloqueados por la protección del modelo de objetos de Outlook, obtenga objetos de Outlook desde el campo de la aplicación de la `ThisAddIn` clase. Para obtener más información, consulte [consideraciones de seguridad específicas para soluciones de Office](../vsto/specific-security-considerations-for-office-solutions.md).  
  
### <a name="explorer-object"></a>Objeto Explorer  
 El objeto <xref:Microsoft.Office.Interop.Outlook.Explorer> representa una ventana que muestra el contenido de una carpeta que contiene elementos como mensajes de correo electrónico, tareas o citas. El objeto <xref:Microsoft.Office.Interop.Outlook.Explorer> incluye métodos y propiedades que puede usar para modificar la ventana, así como eventos que se generan cuando cambia la ventana.  
  
 Para obtener un objeto <xref:Microsoft.Office.Interop.Outlook.Explorer> , realice una de las acciones siguientes:  
  
-   Use la propiedad <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A> del objeto <xref:Microsoft.Office.Interop.Outlook.Application> para acceder a todos los objetos <xref:Microsoft.Office.Interop.Outlook.Explorer> de Outlook.  
  
-   Use el método <xref:Microsoft.Office.Interop.Outlook._Application.ActiveExplorer%2A> del objeto <xref:Microsoft.Office.Interop.Outlook.Application> para obtener el <xref:Microsoft.Office.Interop.Outlook.Explorer> que tenga actualmente el foco.  
  
-   Use el método `GetExplorer` del objeto <xref:Microsoft.Office.Interop.Outlook.Folder> para obtener el <xref:Microsoft.Office.Interop.Outlook.Explorer> de la carpeta actual.  
  
### <a name="inspector-object"></a>Objeto Inspector  
 El objeto <xref:Microsoft.Office.Interop.Outlook.Inspector> representa una ventana que muestra un único elemento como un mensaje de correo electrónico, una tarea o una cita. El objeto <xref:Microsoft.Office.Interop.Outlook.Inspector> incluye métodos y propiedades que puede usar para modificar la ventana, así como eventos que se generan cuando cambia la ventana.  
  
 Para obtener un objeto <xref:Microsoft.Office.Interop.Outlook.Inspector> , realice una de las acciones siguientes:  
  
-   Use la propiedad <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A> del objeto <xref:Microsoft.Office.Interop.Outlook.Application> para acceder a todos los objetos <xref:Microsoft.Office.Interop.Outlook.Inspector> de Outlook.  
  
-   Use el método <xref:Microsoft.Office.Interop.Outlook._Application.ActiveInspector%2A> del objeto <xref:Microsoft.Office.Interop.Outlook.Application> para obtener el <xref:Microsoft.Office.Interop.Outlook.Inspector> que tenga actualmente el foco.  
  
-   Use el método `GetInspector` de un determinado elemento, como un <xref:Microsoft.Office.Interop.Outlook.MailItem> o <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>, para recuperar el Inspector que está asociado a él.  
  
### <a name="folder-object"></a>Objeto de carpeta  
 El objeto <xref:Microsoft.Office.Interop.Outlook.Folder> representa una carpeta que contiene mensajes de correo electrónico, contactos, tareas y otros elementos. Outlook proporciona 16 objetos <xref:Microsoft.Office.Interop.Outlook.Folder> predeterminados.  
  
 Los objetos <xref:Microsoft.Office.Interop.Outlook.Folder> predeterminados se definen mediante los valores de enumeración <xref:Microsoft.Office.Interop.Outlook.OlDefaultFolders>. Por ejemplo,  
  
 Microsoft.Office.Interop.Outlook.OlDefaultFolders.olFolderInbox corresponde a la **Bandeja de entrada** carpeta de Outlook.  
  
 Para obtener un ejemplo que muestra cómo obtener acceso a un valor predeterminado <xref:Microsoft.Office.Interop.Outlook.Folder> y cree un nuevo <xref:Microsoft.Office.Interop.Outlook.Folder>, consulte [Cómo: crear elementos de carpeta personalizados mediante programación](../vsto/how-to-programmatically-create-custom-folder-items.md).  
  
### <a name="mailitem-object"></a>Objeto MailItem  
 El objeto <xref:Microsoft.Office.Interop.Outlook.MailItem> representa un mensaje de correo electrónico. Los objetos<xref:Microsoft.Office.Interop.Outlook.MailItem> normalmente están en carpetas, como **Bandeja de entrada**, **Elementos enviados**y **Bandeja de salida**. <xref:Microsoft.Office.Interop.Outlook.MailItem> expone propiedades y métodos que se pueden usar para crear y enviar mensajes de correo electrónico.  
  
 Para obtener un ejemplo que muestra cómo crear un mensaje de correo electrónico, consulte [Cómo: crear un elemento de correo electrónico mediante programación](../vsto/how-to-programmatically-create-an-e-mail-item.md).  
  
### <a name="appointmentitem-object"></a>Objeto AppointmentItem  
 El objeto <xref:Microsoft.Office.Interop.Outlook.AppointmentItem> representa una reunión, una cita única o una reunión o cita periódica en la carpeta **Calendario** . El objeto <xref:Microsoft.Office.Interop.Outlook.AppointmentItem> incluye métodos que realizan acciones, como responder o reenviar convocatorias de reunión y propiedades que especifican los detalles de la reunión, como la ubicación y la hora.  
  
 Para obtener un ejemplo que muestra cómo crear una cita, consulte [Cómo: crear mediante programación una convocatoria de reunión](../vsto/how-to-programmatically-create-a-meeting-request.md).  
  
### <a name="taskitem-object"></a>Objeto TaskItem  
 El objeto <xref:Microsoft.Office.Interop.Outlook.TaskItem> representa una tarea que debe realizarse dentro de un período de tiempo especificado. Los objetos<xref:Microsoft.Office.Interop.Outlook.TaskItem> se encuentran en la carpeta **Tareas** .  
  
 Para crear una tarea, use el [CreateItem](/previous-versions/office/developer/office-2003/aa220082(v=office.11)) método de la <xref:Microsoft.Office.Interop.Outlook.Application> de objetos y pase el valor <xref:Microsoft.Office.Interop.Outlook.OlItemType.olTaskItem> para el parámetro.  
  
### <a name="contactitem-object"></a>Objeto ContactItem  
 El objeto <xref:Microsoft.Office.Interop.Outlook.ContactItem>representa un contacto de la carpeta **Contactos** . Los objetos<xref:Microsoft.Office.Interop.Outlook.ContactItem> contienen una gran variedad de información de contacto de las personas que representan, como direcciones postales, direcciones de correo electrónico y números de teléfono.  
  
 Para obtener un ejemplo que muestra cómo crear un nuevo contacto, consulte [Cómo: agregar una entrada a los contactos de Outlook mediante programación](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md). Para obtener un ejemplo que muestra cómo buscar un contacto ya existente, consulte [Cómo: buscar un contacto específico mediante programación](../vsto/how-to-programmatically-search-for-a-specific-contact.md).  
  
##  <a name="refdoc"></a> Utilice la documentación del modelo de objetos de Outlook  
 Para obtener información completa sobre el modelo de objetos de Outlook, puede consultar la referencia del ensamblado de interoperabilidad primario (PIA) de Outlook y la referencia del modelo de objetos VBA.  
  
### <a name="primary-interop-assembly-reference"></a>Referencia de ensamblado de interoperabilidad primario  
 La referencia de PIA de Outlook documenta los tipos en los ensamblados de interoperabilidad primarios para Outlook 2010. Para obtener más información, consulte [referencia de ensamblado de interoperabilidad primario de Outlook 2010](http://go.microsoft.com/fwlink/?LinkId=189580).  
  
 Además de proporcionar información de todos los tipos de los PIA, esta documentación proporciona información adicional acerca de la estructura de los PIA y ejemplos de código de tareas comunes de automatización de Outlook.  
  
### <a name="vba-object-model-reference"></a>Referencia del modelo de objetos VBA  
 La referencia del modelo de objetos de VBA documenta el modelo de objetos de Outlook tal como se expone al código de Visual Basic para Aplicaciones (VBA). Para obtener más información, consulte [referencia del modelo de objetos de Outlook 2010](http://go.microsoft.com/fwlink/?LinkId=199769).  
  
 Todos los objetos y miembros de la referencia del modelo de objetos de VBA corresponden a tipos y miembros del PIA de Outlook. Por ejemplo, el objeto Inspector en la referencia del modelo de objetos VBA corresponde a la <xref:Microsoft.Office.Interop.Outlook.Inspector> objeto en los PIA de Outlook. Aunque la referencia del modelo de objetos VBA proporciona ejemplos de código para la mayoría de las propiedades, métodos y eventos, debe traducir el código VBA de esta referencia a Visual Basic o Visual C# si quiere usarlo en un proyecto de complemento de VSTO de Outlook creado con Visual Studio.  
  
### <a name="related-topics"></a>Temas relacionados  
  
|Título|Descripción|  
|-----------|-----------------|  
|[Trabajar con elementos de contacto](../vsto/working-with-contact-items.md)|Proporciona temas que muestran cómo realizar tareas con los contactos.|  
|[Trabajar con elementos de correo](../vsto/working-with-mail-items.md)|Proporciona temas que muestran cómo realizar tareas con los elementos de correo.|  
|[Trabajar con carpetas](../vsto/working-with-folders.md)|Proporciona temas que muestran cómo realizar tareas con carpetas.|  
|[Trabajar con elementos de calendario](../vsto/working-with-calendar-items.md)|Proporciona temas que muestran cómo realizar tareas con elementos del calendario.|  
|[Cómo: determinar mediante programación el actual elemento de Outlook](../vsto/how-to-programmatically-determine-the-current-outlook-item.md)|Muestra cómo mostrar el nombre de la carpeta actual y alguna información sobre el elemento seleccionado.|  
  