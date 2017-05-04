---
title: "Soluciones de Visio | Microsoft Docs"
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
  - "proyectos de Office [desarrollo de Office en Visual Studio], Visio"
  - "soluciones [desarrollo de Office en Visual Studio], Visio"
  - "Visio [desarrollo de Office en Visual Studio]"
  - "plantillas [desarrollo de Office en Visual Studio], Visio"
  - "proyectos [desarrollo de Office en Visual Studio], Visio"
  - "soluciones de Office [desarrollo de Office en Visual Studio], Visio"
ms.assetid: c52948c6-6891-43ec-93ff-c54c74ec6016
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 36
---
# Soluciones de Visio
  Visual Studio proporciona plantillas de proyecto que puede usar para crear complementos de VSTO para Microsoft Office Visio. Puede usar los complementos de VSTO para automatizar Visio, ampliar las características de Visio o personalizar la interfaz de usuario de Visio.  
  
 Para obtener más información acerca de los complementos VSTO, consulte [Introducción a la programación de complementos de VSTO](../vsto/getting-started-programming-vsto-add-ins.md) y [Arquitectura de complementos de VSTO](../vsto/architecture-of-vsto-add-ins.md). Si no sabe cómo programar con Microsoft Office, consulte [Introducción &#40;Desarrollo de Office en Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).  
  
 **Aplicación:** la información de este tema se aplica a los proyectos de complementos VSTO para Visio 2010. Para obtener más información, consulta [Características disponibles por aplicación y tipo de proyecto de Office](../vsto/features-available-by-office-application-and-project-type.md).  
  
## Automatizar Visio mediante el modelo de objetos de Visio  
 El modelo de objetos de Visio expone muchas clases que puede usar para automatizar Visio a fin de crear diagramas para organigramas, diagramas de flujo, escalas de tiempo del proyecto, diagramas de red, espacios de oficina, etc. La API permite escribir código para llevar a cabo tareas comunes:  
  
-   Construir y colocar formas y texto en los diagramas.  
  
-   Administrar el comportamiento de las formas de acuerdo con la lógica de negocios y los datos proporcionados por el usuario.  
  
-   Controlar la visualización de diagramas, como el modo de panorámica y el zoom.  
  
-   Personalizar la interfaz de usuario de la aplicación.  
  
-   Importar datos externos a Visio, vincularlos a formas y mostrarlos gráficamente en una página.  
  
 Encontrará procedimientos paso a paso y ejemplos de código para usar el modelo de objetos de Visio para trabajar con documentos y formas en [Trabajar con documentos de Visio](../vsto/working-with-visio-documents.md) y [Trabajar con formas de Visio](../vsto/working-with-visio-shapes.md).  
  
 Para obtener acceso al modelo de objetos de Visio desde un complemento de VSTO, use el campo `Application` de la clase `ThisAddIn` del proyecto. El campo `Application` devuelve un objeto Microsoft.Office.Interop.Visio.Application que representa la instancia actual de Visio. Para obtener más información, consulta [Programar complementos de VSTO](../vsto/programming-vsto-add-ins.md).  
  
 Cuando se llama al modelo de objetos de Visio, se usan los tipos que se proporcionan en el ensamblado de interoperabilidad primario \(PIA\) para Visio. El PIA actúa como puente entre el código administrado del complemento de VSTO y el modelo de objetos COM de Visio. Todo tipo de PIA de Visio se define en el espacio de nombres Microsoft.Office.Interop.Visio. Para obtener más información acerca de los ensamblados de interoperabilidad primarios, consulte [Información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) y [Ensamblados de interoperabilidad primarios de Office](../vsto/office-primary-interop-assemblies.md).  
  
## Información general sobre el modelo de objetos de Visio  
 Aquí encontrará información general del modelo de objetos de Visio en [Información general sobre el modelo de objetos de Visio](../vsto/visio-object-model-overview.md), que incluye vínculos para consultar referencias acerca del modelo de objetos de Visio y los SDK.  
  
## Personalización de la interfaz de usuario de Visio  
 La interfaz de usuario de Visio tiene las siguientes opciones de personalización.  
  
|Tarea|Para obtener más información|  
|-----------|----------------------------------|  
|Personalizar la cinta de opciones.|[Información general sobre la cinta de opciones](../vsto/ribbon-overview.md)|  
  
 Para obtener información sobre cómo personalizar la interfaz de usuario de Visio, consulte la documentación de referencia de VBA correspondiente a la clase [Visio.UIObject](HV10077129).  
  
## Vea también  
 [Introducción a la programación de complementos de VSTO](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Arquitectura de complementos de VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programar complementos de VSTO](../vsto/programming-vsto-add-ins.md)   
 [Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)   
 [Ensamblados de interoperabilidad primarios de Office](../vsto/office-primary-interop-assemblies.md)   
 [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)   
 [Información general sobre el modelo de objetos de Visio](../vsto/visio-object-model-overview.md)   
 [Desarrollo de Visio 2010 en Office](http://go.microsoft.com/fwlink/?LinkId=199017)  
  
  