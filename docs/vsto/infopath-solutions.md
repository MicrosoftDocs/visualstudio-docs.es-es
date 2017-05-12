---
title: "Soluciones de InfoPath"
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
  - "soluciones [desarrollo de Office en Visual Studio], InfoPath"
  - "plantillas [desarrollo de Office en Visual Studio], InfoPath"
  - "InfoPath [desarrollo de Office en Visual Studio]"
  - "Desarrollo de Office en Visual Studio, soluciones InfoPath"
  - "proyectos [desarrollo de Office en Visual Studio], InfoPath"
  - "soluciones de Office [desarrollo de Office en Visual Studio], InfoPath"
  - "proyectos de Office [desarrollo de Office en Visual Studio], InfoPath"
ms.assetid: 20ac6bee-b17f-4217-9f78-11304a11236a
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Soluciones de InfoPath
  Visual Studio proporciona plantillas de proyecto que puede utilizar para crear complementos de VSTO para Microsoft Office InfoPath 2013 e InfoPath 2010. InfoPath no está disponible en Office 2016.  
  
> [!NOTE]  
>  Puede crear un complemento para VSTO aunque haya instalado Office 2016. Solo tiene que instalar InfoPath 2013 u Office 2013 en paralelo con Office 2016.  
  
 [!INCLUDE[appliesto_infoallapp](../vsto/includes/appliesto-infoallapp-md.md)]  
  
 Los complementos de VSTO para InfoPath son similares a los complementos VSTO para otras aplicaciones de Microsoft Office. Estos tipos de soluciones constan de un ensamblado cargado por la aplicación. Los usuarios finales pueden tener acceso a la funcionalidad de este ensamblado independientemente del formulario o la plantilla de formulario que haya abiertos. Para obtener más información sobre los complementos de VSTO, consulte [Introducción a la programación de complementos de VSTO](../vsto/getting-started-programming-vsto-add-ins.md) y [Arquitectura de complementos de VSTO](../vsto/architecture-of-vsto-add-ins.md).  
  
> [!NOTE]  
>  Visual Studio 2015 no incluye los proyectos de plantilla de formulario de InfoPath incorporados en versiones anteriores de Visual Studio. Tampoco puede utilizar Visual Studio 2015 para abrir o modificar un proyecto de plantilla de formulario de InfoPath creado en una versión anterior de Visual Studio. Sin embargo, puede abrir y editar un proyecto de plantilla de formulario de InfoPath con Visual Studio Tools para Aplicaciones. Para obtener más información, vea [Trabajar con proyectos de VSTO 2008 en InfoPath 2010.](http://go.microsoft.com/fwlink/?LinkID=218903).  
  
## Automatizar InfoPath mediante un complemento  
 Para obtener acceso al modelo de objetos de InfoPath desde un complemento de VSTO para Office creado con las herramientas de desarrollo de Office en Visual Studio, utilice el campo `Application` de la clase `ThisAddIn` en el proyecto. El campo `Application` devuelve un objeto <xref:Microsoft.Office.Interop.InfoPath.Application> que representa la instancia actual de InfoPath. Para obtener más información, consulta [Programar complementos de VSTO](../vsto/programming-vsto-add-ins.md).  
  
 Cuando llame al modelo de objetos de InfoPath desde un complemento de VSTO, utilice los tipos proporcionados en el ensamblado de interoperabilidad primario de InfoPath. El ensamblado de interoperabilidad primario actúa como un puente entre el código administrado del complemento de VSTO y el modelo de objetos COM de InfoPath. Todos los tipos del ensamblado de interoperabilidad primario de InfoPath se definen en el espacio de nombres <xref:Microsoft.Office.Interop.InfoPath>. Para obtener más información sobre el ensamblado de interoperabilidad primario de InfoPath, vea [Acerca del ensamblado de interoperabilidad primario de Microsoft Office InfoPath](http://msdn.microsoft.com/es-es/1b3ae03c-6951-49e4-a489-4712d3f7ba72). Para obtener más información sobre los ensamblados de interoperabilidad primarios en general, consulte [Información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) y [Ensamblados de interoperabilidad primarios de Office](../vsto/office-primary-interop-assemblies.md).  
  
## Personalizar la interfaz de usuario de InfoPath mediante un complemento  
 Al crear un complemento de VSTO para InfoPath, tiene varias opciones de personalización de la IU diferentes. En la tabla siguiente se enumeran algunas de estas opciones.  
  
|Tarea|Para obtener más información|  
|-----------|----------------------------------|  
|Crear un panel de tareas personalizado.|[Paneles de tareas personalizados](../vsto/custom-task-panes.md)|  
|Agregar pestañas personalizadas a la cinta de opciones en InfoPath.|[Personalizar una Cinta para InfoPath](../vsto/customizing-a-ribbon-for-infopath.md)|  
  
 Para obtener más información sobre cómo personalizar la interfaz de usuario de InfoPath y de otras aplicaciones de Microsoft Office, consulte [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md).  
  
## Vea también  
 [Sobre el ensamblado de interoperabilidad de Microsoft Office InfoPath principal](http://msdn.microsoft.com/es-es/1b3ae03c-6951-49e4-a489-4712d3f7ba72)   
 [Introducción a la programación de complementos de VSTO](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Arquitectura de complementos de VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programar complementos de VSTO](../vsto/programming-vsto-add-ins.md)   
 [Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)   
 [Ensamblados de interoperabilidad primarios de Office](../vsto/office-primary-interop-assemblies.md)   
 [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)   
 [Desarrollo de InfoPath 2010 en Office](http://go.microsoft.com/fwlink/?LinkId=199012)  
  
  