---
title: "Soluciones de PowerPoint"
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
  - "soluciones de Office [desarrollo de Office en Visual Studio], PowerPoint"
  - "plantillas [desarrollo de Office en Visual Studio], PowerPoint"
  - "soluciones [desarrollo de Office en Visual Studio], PowerPoint"
  - "proyectos [desarrollo de Office en Visual Studio], PowerPoint"
  - "PowerPoint [desarrollo de Office en Visual Studio]"
  - "proyectos de Office [desarrollo de Office en Visual Studio], PowerPoint"
ms.assetid: 02ebad64-9fd3-495f-ab27-4f6206b3d6d2
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# Soluciones de PowerPoint
  Visual Studio ofrece plantillas de proyecto que puede usarse para crear complementos de VSTO para Microsoft Office Outlook. Los complementos de VSTO se pueden usar para automatizar PowerPoint, ampliar las características de PowerPoint o personalizar la interfaz de usuario \(UI\) de PowerPoint.  
  
 Para obtener más información sobre los complementos de VSTO, consulte [Introducción a la programación de complementos de VSTO](../vsto/getting-started-programming-vsto-add-ins.md) y [Arquitectura de complementos de VSTO](../vsto/architecture-of-vsto-add-ins.md). Si no sabe cómo programar con Microsoft Office, consulte [Introducción &#40;Desarrollo de Office en Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).  
  
 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]  
  
 ![vínculo a vídeo](../vsto/media/playvideo.png "vínculo a vídeo") Para ver una demostración en vídeo relacionada, consulte [Cómo: crear un complemento para Microsoft PowerPoint](http://go.microsoft.com/fwlink/?LinkId=132767).  
  
## Automatizar PowerPoint usando el modelo de objetos de PowerPoint  
 El modelo de objetos de PowerPoint expone muchos tipos que puede usar para automatizar PowerPoint. Estos tipos le permiten escribir código para llevar a cabo tareas comunes:  
  
-   Crear y dar formato a presentaciones mediante programación.  
  
-   Agregar o quitar diapositivas de las presentaciones.  
  
-   Agregar formas a una diapositiva o cambiar las formas de una diapositiva.  
  
 Para acceder al modelo de objetos de PowerPoint desde un complemento de VSTO, use el campo `Application` de la clase `ThisAddIn` del proyecto. El campo `Application` devuelve un objeto <xref:Microsoft.Office.Interop.PowerPoint.Application> que representa la instancia actual de PowerPoint. Para obtener más información, consulta [Programar complementos de VSTO](../vsto/programming-vsto-add-ins.md).  
  
 Cuando se llama al modelo de objetos de PowerPoint, se usan los tipos que se proporcionan en el ensamblado de interoperabilidad primario de PowerPoint. El ensamblado de interoperabilidad primario actúa como un puente entre el código administrado del complemento de VSTO y el modelo de objetos COM de PowerPoint. Todos los tipos del ensamblado de interoperabilidad primario de PowerPoint se definen en el espacio de nombres <xref:Microsoft.Office.Interop.PowerPoint>. Para obtener más información sobre los ensamblados de interoperabilidad primarios, consulte [Información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) y [Ensamblados de interoperabilidad primarios de Office](../vsto/office-primary-interop-assemblies.md).  
  
##  <a name="WordOMDocumentation"></a> Usar la documentación del modelo de objetos de PowerPoint  
 Para obtener información completa sobre el modelo de objetos de PowerPoint, puede consultar la referencia del ensamblado de interoperabilidad primario \(PIA\) de PowerPoint y la referencia del modelo de objetos VBA.  
  
### Referencia de ensamblado de interoperabilidad primario  
 La documentación de referencia de los PIA de PowerPoint describe los tipos Del ensamblado de interoperabilidad primario para PowerPoint. Esta documentación está disponible en la siguiente ubicación: [Referencia de ensamblados de interoperabilidad primarios de PowerPoint 2010](http://go.microsoft.com/fwlink/?LinkId=189588).  
  
 Para obtener más información sobre el diseño de los ensamblados de interoperabilidad primarios \(PIA\) de PowerPoint, como las diferencias entre las clases y las interfaces en los PIA y cómo se implementan los eventos en los PIA, consulte [Información general sobre las clases y las interfaces de los ensamblados de interoperabilidad primarios de Office](http://go.microsoft.com/fwlink/?LinkId=199885).  
  
### Referencia del modelo de objetos de VBA  
 La referencia del modelo de objetos de VBA documenta el modelo de objetos de PowerPoint tal como se expone al código de Visual Basic para Aplicaciones \(VBA\). Para obtener más información, consulte la [Referencia del modelo de objetos de PowerPoint 2010](http://go.microsoft.com/fwlink/?LinkId=199770).  
  
 Todos los objetos y miembros de la referencia del modelo de objetos de VBA corresponden a tipos y miembros del ensamblado de interoperabilidad primario \(PIA\) de PowerPoint. Por ejemplo, el objeto Presentation en la referencia del modelo de objetos VBA corresponde al tipo <xref:Microsoft.Office.Interop.PowerPoint.Presentation> del PIA de PowerPoint. Aunque la referencia del modelo de objetos de VBA proporciona ejemplos de código para la mayoría de las propiedades, los métodos y los eventos, debe traducir el código de VBA de esta referencia a Visual Basic o Visual C\# si quiere usarlo en un proyecto de complemento de VSTO para PowerPoint creado con Visual Studio.  
  
## Personalizar la interfaz de usuario de PowerPoint  
 Puede modificar la interfaz de usuario \(UI\) de PowerPoint de las siguientes maneras:  
  
|Tarea|Para obtener más información|  
|-----------|----------------------------------|  
|Crear un panel de tareas personalizado.|[Paneles de tareas personalizados](../vsto/custom-task-panes.md)|  
|Agregar pestañas personalizadas a la cinta.|[Información general sobre la cinta de opciones](../vsto/ribbon-overview.md)|  
|Agregar grupos personalizados a una pestaña integrada en la cinta.|[Cómo: Personalizar una pestaña integrada](../vsto/how-to-customize-a-built-in-tab.md)|  
  
 Para obtener más información sobre cómo personalizar la interfaz de usuario de PowerPoint y de otras aplicaciones de Microsoft Office, consulte [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md).  
  
## Vea también  
 [Tutorial: Crear el primer complemento de VSTO para PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)   
 [Introducción a la programación de complementos de VSTO](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Arquitectura de complementos de VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programar complementos de VSTO](../vsto/programming-vsto-add-ins.md)   
 [Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)   
 [Ensamblados de interoperabilidad primarios de Office](../vsto/office-primary-interop-assemblies.md)   
 [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)   
 [Desarrollo de PowerPoint 2010 en Office](http://go.microsoft.com/fwlink/?LinkId=199015)  
  
  