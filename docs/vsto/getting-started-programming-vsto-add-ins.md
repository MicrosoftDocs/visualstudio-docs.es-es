---
title: "Introducción a la programación de complementos VSTO | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VST.ProjectItem.Outlook
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], getting started
- add-ins [Office development in Visual Studio], getting started
ms.assetid: 9ac1e6ea-9511-4633-80f9-dc7641f22b63
caps.latest.revision: "60"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: f399cd0d62cf9cf8e90191e293e56279930977e4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-programming-vsto-add-ins"></a>Getting Started Programming VSTO Add-ins
  Puede utilizar complementos de VSTO para automatizar las aplicaciones de Microsoft Office, ampliar las características de la aplicación y personalizar la interfaz de usuario de la aplicación. Para obtener información acerca de los complementos de VSTO en comparación con otros tipos de soluciones de Office que puede crear con Visual Studio, vea [información general sobre el desarrollo de soluciones de Office &#40; VSTO &#41; ](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## <a name="creating-vsto-add-in-projects"></a>Crear proyectos de complementos de VSTO  
 Crear proyectos de complemento de VSTO, use una de las plantillas de proyecto complemento de VSTO en el **nuevo proyecto** cuadro de diálogo. Estas plantillas incluyen las referencias de ensamblado necesarias y los archivos del proyecto. Visual Studio proporciona plantillas de proyecto de complementos de VSTO para la mayoría de las aplicaciones de Office.  
  
 Para obtener más información sobre cómo crear un proyecto de complemento de VSTO, consulte [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Para obtener más información acerca de las plantillas de proyecto, vea [información general de plantillas de proyecto de Office](../vsto/office-project-templates-overview.md).  
  
## <a name="developing-vsto-add-in-projects"></a>Desarrollar proyectos de complementos de VSTO  
 Cuando crea un proyecto de complemento de VSTO, Visual Studio crea automáticamente un ThisAddIn.vb (en [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]) o un archivo de código ThisAddIn.cs (en C#). Este archivo contiene el `ThisAddIn` (clase), que proporciona la base para el complemento de VSTO. Puede utilizar los miembros de esta clase para ejecutar código cuando el complemento de VSTO se carga o descarga, para tener acceso al modelo de objetos de la aplicación host y para ampliar las características de la aplicación. Para obtener más información, consulta [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
## <a name="automating-applications-by-using-the-object-models"></a>Automatizar aplicaciones mediante modelos de objetos  
 Los modelos de objetos de las aplicaciones de Microsoft Office exponen muchos tipos que se pueden programar en un complemento de VSTO. Puede usar estos tipos para automatizar la aplicación. Por ejemplo, puede crear y enviar un mensaje de correo electrónico en Outlook o abrir un documento y agregar contenido en Word mediante programación. Para obtener más información acerca de cómo obtener acceso al modelo de objeto de la aplicación host en el código, vea [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
 Para obtener más información acerca de los modelos de objetos de aplicaciones de Microsoft Office concretas, vea los temas siguientes:  
  
-   [Excel Object Model Overview](../vsto/excel-object-model-overview.md)  
  
-   [Word Object Model Overview](../vsto/word-object-model-overview.md)  
  
-   [Outlook Object Model Overview](../vsto/outlook-object-model-overview.md)  
  
-   [Soluciones de InfoPath](../vsto/infopath-solutions.md)  
  
-   [Soluciones de PowerPoint](../vsto/powerpoint-solutions.md)  
  
-   [Soluciones de proyecto](../vsto/project-solutions.md)  
  
-   [Información general sobre el modelo de objetos de Visio](../vsto/visio-object-model-overview.md)  
  
## <a name="customizing-the-user-interface-of-applications"></a>Personalización de la interfaz de usuario de las aplicaciones  
 Hay varias maneras de personalizar la interfaz de usuario de la aplicación host mediante un complemento de VSTO:  
  
-   Para Excel y Word, puede agregar controles administrados a documentos. Para obtener más información, consulta [Extending Word Documents and Excel Workbooks in VSTO Add-ins at Run Time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
-   Puede personalizar la cinta de opciones si la aplicación lo admite. Para obtener más información, consulte [información general de la cinta de opciones](../vsto/ribbon-overview.md).  
  
-   Puede crear un panel de tareas personalizado si la aplicación lo admite. Para obtener más información, consulte [paneles de tareas personalizados](../vsto/custom-task-panes.md).  
  
-   Para Outlook, puede crear un área de formulario personalizada. Para obtener más información, consulta [Creating Outlook Form Regions](../vsto/creating-outlook-form-regions.md).  
  
-   Para todas las aplicaciones de Microsoft Office, puede mostrar Windows Forms en el complemento de VSTO.  
  
 Para obtener más información sobre cómo personalizar las aplicaciones de interfaz de usuario de Microsoft Office, consulte [personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md).  
  
## <a name="next-steps"></a>Pasos siguientes  
 Para obtener información sobre cómo crear complementos de VSTO, vea los siguientes tutoriales:  
  
-   [Tutorial: Creación del primer complemento VSTO para Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)  
  
-   [Tutorial: Creación del primer complemento VSTO para Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)  
  
-   [Tutorial: Creación del primer complemento VSTO para PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)  
  
-   [Tutorial: Creación del primer complemento VSTO para Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)  
  
-   [Tutorial: Creación del primer complemento VSTO para Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)  
  
 Estos tutoriales presentan las herramientas de desarrollo de Office en Visual Studio y el modelo de programación de complementos de VSTO.  
  
 Para obtener una lista de temas que le guiarán a través de algunas de las tareas comunes en proyectos de Office, consulte [tareas comunes de programación de Office](../vsto/common-tasks-in-office-programming.md).  
  
## <a name="see-also"></a>Vea también  
 [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Introducción a &#40; desarrollo de Office en Visual Studio &#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)   
 [Arquitectura de complementos VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)  
  
  