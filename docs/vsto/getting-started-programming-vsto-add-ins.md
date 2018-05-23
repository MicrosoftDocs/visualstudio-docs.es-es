---
title: Empezar a programar complementos VSTO
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7249c3971c8008f70b9e5add79adddde17fe6a82
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/22/2018
---
# <a name="get-started-programming-vsto-add-ins"></a>Empezar a programar complementos VSTO
  Puede utilizar complementos de VSTO para automatizar las aplicaciones de Microsoft Office, ampliar las características de la aplicación y personalizar la interfaz de usuario de la aplicación. Para obtener información acerca de los complementos de VSTO en comparación con otros tipos de soluciones de Office que puede crear con Visual Studio, vea [información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## <a name="create-vsto-add-in-projects"></a>Crear proyectos de complemento de VSTO  
 Crear proyectos de complemento de VSTO, use una de las plantillas de proyecto complemento de VSTO en el **nuevo proyecto** cuadro de diálogo. Estas plantillas incluyen las referencias de ensamblado necesarias y los archivos del proyecto. Visual Studio proporciona plantillas de proyecto de complementos de VSTO para la mayoría de las aplicaciones de Office.  
  
 Para obtener más información sobre cómo crear un proyecto de complemento de VSTO, consulte [Cómo: proyectos de Office crear en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Para obtener más información acerca de las plantillas de proyecto, vea [información general de plantillas de proyecto de Office](../vsto/office-project-templates-overview.md).  
  
## <a name="develop-vsto-add-in-projects"></a>Desarrollar proyectos de complemento de VSTO  
 Cuando crea un proyecto de complemento de VSTO, Visual Studio crea automáticamente un *ThisAddIn.vb* (en [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]) o *ThisAddIn.cs* (en C#) el archivo de código. Este archivo contiene el `ThisAddIn` (clase), que proporciona la base para el complemento de VSTO. Puede utilizar los miembros de esta clase para ejecutar código cuando el complemento de VSTO se carga o descarga, para tener acceso al modelo de objetos de la aplicación host y para ampliar las características de la aplicación. Para obtener más información, consulte [los complementos de VSTO de programa](../vsto/programming-vsto-add-ins.md).  
  
## <a name="automate-applications-by-using-the-object-models"></a>Automatizar aplicaciones mediante los modelos de objetos  
 Los modelos de objetos de las aplicaciones de Microsoft Office exponen muchos tipos que se pueden programar en un complemento de VSTO. Puede usar estos tipos para automatizar la aplicación. Por ejemplo, puede crear y enviar un mensaje de correo electrónico en Outlook o abrir un documento y agregar contenido en Word mediante programación. Para obtener más información acerca de cómo obtener acceso al modelo de objeto de la aplicación host en el código, vea [los complementos de VSTO de programa](../vsto/programming-vsto-add-ins.md).  
  
 Para obtener más información acerca de los modelos de objetos de aplicaciones de Microsoft Office concretas, vea los temas siguientes:  
  
-   [Información general sobre el modelo de objetos de Excel](../vsto/excel-object-model-overview.md)  
  
-   [Información general sobre el modelo de objetos de Word](../vsto/word-object-model-overview.md)  
  
-   [Información general sobre el modelo de objetos de Outlook](../vsto/outlook-object-model-overview.md)  
  
-   [Soluciones de InfoPath](../vsto/infopath-solutions.md)  
  
-   [Soluciones de PowerPoint](../vsto/powerpoint-solutions.md)  
  
-   [Soluciones de Project](../vsto/project-solutions.md)  
  
-   [Información general sobre el modelo de objetos de Visio](../vsto/visio-object-model-overview.md)  
  
## <a name="customize-the-user-interface-of-applications"></a>Personalizar la interfaz de usuario de aplicaciones  
 Hay varias maneras de personalizar la interfaz de usuario de la aplicación host mediante un complemento de VSTO:  
  
-   Para Excel y Word, puede agregar controles administrados a documentos. Para obtener más información, consulte [documentos de Word extender y libros de Excel en complementos VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
-   Puede personalizar la cinta de opciones si la aplicación lo admite. Para obtener más información, consulte [información general de la cinta de opciones](../vsto/ribbon-overview.md).  
  
-   Puede crear un panel de tareas personalizado si la aplicación lo admite. Para obtener más información, consulte [paneles de tareas personalizados](../vsto/custom-task-panes.md).  
  
-   Para Outlook, puede crear un área de formulario personalizada. Para obtener más información, consulte [áreas de formulario de Outlook crear](../vsto/creating-outlook-form-regions.md).  
  
-   Para todas las aplicaciones de Microsoft Office, puede mostrar Windows Forms en el complemento de VSTO.  
  
 Para obtener más información sobre cómo personalizar las aplicaciones de interfaz de usuario de Microsoft Office, consulte [personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md).  
  
## <a name="next-steps"></a>Pasos siguientes  
 Para obtener información sobre cómo crear complementos de VSTO, vea los siguientes tutoriales:  
  
-   [Tutorial: Crear el primer complemento de VSTO para Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)  
  
-   [Tutorial: Crear el primer complemento de VSTO para Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)  
  
-   [Tutorial: Crear el primer complemento de VSTO para PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)  
  
-   [Tutorial: Crear el primer complemento de VSTO para Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)  
  
-   [Tutorial: Crear el primer complemento de VSTO para Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)  
  
 Estos tutoriales presentan las herramientas de desarrollo de Office en Visual Studio y el modelo de programación de complementos de VSTO.  
  
 Para obtener una lista de temas que le guiarán a través de algunas de las tareas comunes en proyectos de Office, consulte [tareas comunes de programación en Office](../vsto/common-tasks-in-office-programming.md).  
  
## <a name="see-also"></a>Vea también  
 [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Introducción &#40;desarrollo de Office en Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)   
 [Arquitectura de complementos VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Programar complementos VSTO](../vsto/programming-vsto-add-ins.md)  
  
  