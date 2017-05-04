---
title: "Soluciones de Project | Microsoft Docs"
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
  - "proyectos [desarrollo de Office en Visual Studio], Project"
  - "soluciones de Office [desarrollo de Office en Visual Studio], Project"
  - "Project [desarrollo de Office en Visual Studio]"
  - "plantillas [desarrollo de Office en Visual Studio], Project"
  - "proyectos de Office [desarrollo de Office en Visual Studio], Project"
  - "soluciones [desarrollo de Office en Visual Studio], Project"
ms.assetid: 4ce92269-eb6d-44aa-bee3-6d38ec9995f9
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 30
---
# Soluciones de Project
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] incluye plantillas de proyecto que se pueden usar para crear complementos VSTO para Microsoft Office Project. Puede usar los complementos para automatizar Project, ampliar sus características o personalizar la interfaz de usuario.  
  
 Para obtener más información acerca de los complementos VSTO, consulte [Introducción a la programación de complementos de VSTO](../vsto/getting-started-programming-vsto-add-ins.md) y [Arquitectura de complementos de VSTO](../vsto/architecture-of-vsto-add-ins.md). Si no sabe cómo programar con Microsoft Office, consulte [Introducción &#40;Desarrollo de Office en Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).  
  
 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]  
  
## Automatizar Project mediante el modelo de objetos de Project  
 El modelo de objetos de Project expone muchos tipos que se pueden usar para automatizar Project. Estos tipos le permiten escribir código para realizar tareas comunes, como crear y modificar las tareas de un proyecto mediante programación.  
  
 Para obtener acceso al modelo de objetos de Project desde un complemento VSTO, use el campo `Application` de la clase `ThisAddIn` en su proyecto. El campo `Application` devolverá un objeto Microsoft.Office.Interop.MsProject.Application  que representa la instancia actual de Project. Para obtener más información, consulta [Programar complementos de VSTO](../vsto/programming-vsto-add-ins.md).  
  
 Cuando se llama al modelo de objetos de Project, se usan los tipos que se proporcionan en el ensamblado de interoperabilidad primario de Project. El ensamblado de interoperabilidad primario actúa como un puente entre el código administrado del complemento VSTO y el modelo de objetos COM en Project. Todos los tipos del ensamblado de interoperabilidad primario de Project se definen en el espacio de nombres Microsoft.Office.Interop.MSProject. Para obtener más información acerca de los ensamblados de interoperabilidad primarios, consulte [Información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) y [Ensamblados de interoperabilidad primarios de Office](../vsto/office-primary-interop-assemblies.md).  
  
## Usar la documentación del modelo de objetos de Project  
 Para obtener información completa sobre el modelo de objetos de Project, puede consultar la referencia del modelo de objetos de VBA para Project. La referencia del modelo de objetos de VBA documenta el modelo de objetos de Project a medida que se expone al código de Visual Basic para aplicaciones \(VBA\). Para obtener más información, consulte la [Referencia 2010 del modelo de objetos de Project](http://go.microsoft.com/fwlink/?LinkId=199771).  
  
 Todos los objetos y miembros de la referencia del modelo de objetos de VBA corresponden a tipos y a miembros del ensamblado de interoperabilidad primario \(PIA\) de Project. Por ejemplo, el objeto Calendar de la referencia del modelo de objetos de VBA, corresponde al tipo Microsoft.Office.Interop.MSProject.Calendar del PIA de Project. Aunque la referencia del modelo de objetos de VBA proporciona ejemplos de código para la mayoría de las propiedades, métodos y eventos, debe convertir el código de VBA de esta referencia a Visual Basic o a Visual C\# si desea utilizarlo en un proyecto de complemento VSTO de Project que cree mediante Visual Studio.  
  
> [!NOTE]  
>  Por el momento, no existe ninguna documentación de referencia sobre el ensamblado de interoperabilidad primario de Project.  
  
### Tipos de infraestructura del ensamblado de interoperabilidad primario de Project  
 A medida que escriba el código que utiliza el PIA de Project, podrá observar que aparecen muchos tipos que no se describen en la referencia de VBA. Estos tipos adicionales ayudan a convertir los objetos del modelo de objetos basados en COM de Project a código administrado; no están pensados para su uso directo en el código.  
  
 Para obtener más información, consulte [Información general de clases e interfaces de los Ensamblados de interoperabilidad primarios de Office](http://go.microsoft.com/fwlink/?LinkId=189592).  
  
## Personalizar la interfaz de usuario de Project  
 Puede personalizar la interfaz de usuario de Project de las siguientes maneras.  
  
|Tarea|Para obtener más información|  
|-----------|----------------------------------|  
|Agregar pestañas personalizadas a la cinta de opciones en Project|[Información general sobre la cinta de opciones](../vsto/ribbon-overview.md)|  
  
 Para obtener más información sobre cómo personalizar la interfaz de usuario de Project y de otras aplicaciones de Microsoft Office, consulte [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md).  
  
## Vea también  
 [Tutorial: Crear el primer complemento de VSTO para Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)   
 [Introducción a la programación de complementos de VSTO](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Arquitectura de complementos de VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programar complementos de VSTO](../vsto/programming-vsto-add-ins.md)   
 [Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)   
 [Ensamblados de interoperabilidad primarios de Office](../vsto/office-primary-interop-assemblies.md)   
 [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)   
 [Project 2010 y Project Server 2010 en el desarrollo de Office](http://go.microsoft.com/fwlink/?LinkId=199016)  
  
  