---
title: Empezar a programar complementos de VSTO
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.Outlook
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], getting started
- add-ins [Office development in Visual Studio], getting started
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: bf6577d48bed61a6dd5a1775da499ddd89f3769c
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2018
ms.locfileid: "53648686"
---
# <a name="get-started-programming-vsto-add-ins"></a>Empezar a programar complementos de VSTO
  Puede utilizar complementos de VSTO para automatizar las aplicaciones de Microsoft Office, ampliar las características de la aplicación y personalizar la interfaz de usuario de la aplicación. Para obtener información acerca de cómo se comparan los complementos de VSTO para otros tipos de soluciones de Office puede crear con Visual Studio, consulte [información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## <a name="create-vsto-add-in-projects"></a>Crear proyectos de complemento VSTO  
 Crear proyectos de complemento VSTO mediante una de las plantillas de proyecto complemento de VSTO en el **nuevo proyecto** cuadro de diálogo. Estas plantillas incluyen las referencias de ensamblado necesarias y los archivos del proyecto. Visual Studio proporciona plantillas de proyecto de complementos de VSTO para la mayoría de las aplicaciones de Office.  
  
 Para obtener más información sobre cómo crear un proyecto de complemento VSTO, consulte [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Para obtener más información acerca de las plantillas de proyecto, vea [Introducción a las plantillas de proyecto de Office](../vsto/office-project-templates-overview.md).  
  
## <a name="develop-vsto-add-in-projects"></a>Desarrollar proyectos de complemento VSTO  
 Al crear un proyecto de complemento VSTO, Visual Studio crea automáticamente un *ThisAddIn.vb* (en [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]) o *ThisAddIn.cs* archivo de código (en C#). Este archivo contiene el `ThisAddIn` (clase), que proporciona la base para el complemento de VSTO. Puede utilizar los miembros de esta clase para ejecutar código cuando el complemento de VSTO se carga o descarga, para tener acceso al modelo de objetos de la aplicación host y para ampliar las características de la aplicación. Para obtener más información, consulte [programa VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
## <a name="automate-applications-by-using-the-object-models"></a>Automatizar aplicaciones mediante el uso de los modelos de objetos  
 Los modelos de objetos de las aplicaciones de Microsoft Office exponen muchos tipos que se pueden programar en un complemento de VSTO. Puede usar estos tipos para automatizar la aplicación. Por ejemplo, puede crear y enviar un mensaje de correo electrónico en Outlook o abrir un documento y agregar contenido en Word mediante programación. Para obtener más información acerca de cómo obtener acceso al modelo de objeto de la aplicación host en el código, consulte [programa VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
 Para obtener más información acerca de los modelos de objetos de aplicaciones de Microsoft Office concretas, vea los temas siguientes:  
  
-   [Información general sobre el modelo de objetos de Excel](../vsto/excel-object-model-overview.md)  
  
-   [Información general sobre el modelo de objetos de Word](../vsto/word-object-model-overview.md)  
  
-   [Información general sobre el modelo de objetos de Outlook](../vsto/outlook-object-model-overview.md)  
  
-   [Soluciones de InfoPath](../vsto/infopath-solutions.md)  
  
-   [Soluciones de PowerPoint](../vsto/powerpoint-solutions.md)  
  
-   [Soluciones de proyecto](../vsto/project-solutions.md)  
  
-   [Información general sobre el modelo de objetos de Visio](../vsto/visio-object-model-overview.md)  
  
## <a name="customize-the-user-interface-of-applications"></a>Personalizar la interfaz de usuario de aplicaciones  
 Hay varias maneras diferentes de personalizar la interfaz de usuario de la aplicación host mediante el uso de un complemento de VSTO:  
  
- Para Excel y Word, puede agregar controles administrados a documentos. Para obtener más información, consulte [documentos ampliar Word y libros de Excel en complementos VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
- Puede personalizar la cinta de opciones si la aplicación lo admite. Para obtener más información, consulte [información general de la cinta de opciones](../vsto/ribbon-overview.md).  
  
- Puede crear un panel de tareas personalizado si la aplicación lo admite. Para obtener más información, consulte [paneles de tareas personalizados](../vsto/custom-task-panes.md).  
  
- Para Outlook, puede crear un área de formulario personalizada. Para obtener más información, consulte [crear áreas de formulario](../vsto/creating-outlook-form-regions.md).  
  
- Para todas las aplicaciones de Microsoft Office, puede mostrar Windows Forms en el complemento de VSTO.  
  
  Para obtener más información sobre cómo personalizar las aplicaciones de interfaz de usuario de Microsoft Office, consulte [personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md).  
  
## <a name="next-steps"></a>Pasos siguientes  
 Para obtener información sobre cómo crear complementos de VSTO, vea los siguientes tutoriales:  
  
- [Tutorial: Crear el primer complemento VSTO para Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)  
  
- [Tutorial: Crear el primer complemento VSTO para Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)  
  
- [Tutorial: Crear el primer complemento VSTO para PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)  
  
- [Tutorial: Crear el primer complemento VSTO para Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)  
  
- [Tutorial: Crear el primer complemento VSTO para Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)  
  
  Estos tutoriales presentan las herramientas de desarrollo de Office en Visual Studio y el modelo de programación de complementos de VSTO.  
  
  Para obtener una lista de temas que le guiarán a través de algunas de las tareas comunes en proyectos de Office, consulte [tareas comunes de programación de Office](../vsto/common-tasks-in-office-programming.md).  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Introducción a &#40;desarrollo de Office en Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)   
 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)   
 [Programar complementos VSTO](../vsto/programming-vsto-add-ins.md)  
  
  