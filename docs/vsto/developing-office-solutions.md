---
title: "Desarrollar soluciones de Office"
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
  - "desarrollo de Office en Visual Studio, acerca del desarrollo de soluciones"
  - "soluciones [desarrollo de Office en Visual Studio], desarrollar"
  - "soluciones de Office [desarrollo de Office en Visual Studio], desarrollar"
ms.assetid: 7361cfe0-dee4-48d7-a066-232f87f093ca
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 30
---
# Desarrollar soluciones de Office
  Después de diseñar un proyecto con Office Developer Tools en Visual Studio y configurar los archivos del proyecto, puede empezar a centrarse en la implementación del código y la interfaz de usuario personalizada \(UI\).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Modelo de programación de soluciones de Office  
 El modelo de objetos de Office expone una variedad de objetos que se pueden programar. Cuando se programan soluciones de Office mediante código administrado, se escribe código que utiliza tipos de los ensamblados de interoperabilidad primarios de Office. En las soluciones que se crean mediante plantillas de proyecto de Office en Visual Studio, también se escribe código directamente relacionado con las clases generadas en el proyecto. Para obtener más información, consulta [Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md).  
  
## Programar diferentes tipos de soluciones de Office  
 El tipo de solución que esté creando determina las características que puede usar en el proyecto. Por ejemplo, puede agregar controles de formularios Windows Forms y controles de Office extendidos \(denominados *controles host*\) a las personalizaciones de nivel de documento, arrastrando para ello elementos desde el **cuadro de herramientas** de Visual Studio en tiempo de diseño. Sin embargo, si está desarrollando un complemento de VSTO, solo puede agregar este tipo de controles a los documentos en tiempo de ejecución, mediante la escritura de código.  
  
 Para obtener más información acerca de las características específicas para cada tipo de solución, vea los temas siguientes:  
  
-   [Programar complementos de VSTO](../vsto/programming-vsto-add-ins.md).  
  
-   [Programar personalizaciones de nivel de documento](../vsto/programming-document-level-customizations.md).  
  
-   [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md).  
  
 Para obtener información general con la que le resultará más fácil planear las soluciones de Office y procedimientos que le ayudarán a crear proyectos, consulte [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)  
  
## Temas relacionados  
  
|Título|Descripción|  
|------------|-----------------|  
|[Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)|Describe distintos aspectos de la escritura de código en soluciones de Office.|  
|[Programar complementos de VSTO](../vsto/programming-vsto-add-ins.md)|Proporciona información general sobre el modelo de programación de complementos de VSTO y las tareas de programación relacionadas.|  
|[Programar personalizaciones de nivel de documento](../vsto/programming-document-level-customizations.md)|Proporciona información general sobre el modelo de programación de personalizaciones de nivel de documento y las tareas de programación relacionadas.|  
|[Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)|Describe las distintas formas de personalizar las aplicaciones de interfaz de usuario de Office mediante complementos de VSTO y personalizaciones de nivel de documento.|  
|[Datos en las soluciones de Office](../vsto/data-in-office-solutions.md)|Describe las distintas maneras de trabajar con datos en soluciones de Office, como enlazar datos a controles y almacenar datos en caché en las personalizaciones de nivel de documento.|  
|[Solución de problemas de soluciones de Office](../vsto/troubleshooting-office-solutions.md)|Proporciona sugerencias para resolver problemas comunes que pueden surgir al crear soluciones de Office.|  
|[Compatibilidad del subprocesamiento en Office](../vsto/threading-support-in-office.md)|Proporciona información general sobre cómo trabajar con varios subprocesos en soluciones de Office.|  
|[Accesibilidad en proyectos de Office](../vsto/accessibility-in-office-projects.md)|Describe las características de accesibilidad que están disponibles en las soluciones de Office.|  
  
## Vea también  
 [Cómo: Crear y modificar propiedades personalizadas para documentos](../vsto/how-to-create-and-modify-custom-document-properties.md)   
 [Cómo: Leer y escribir en propiedades de un documento](../vsto/how-to-read-from-and-write-to-document-properties.md)   
 [Cómo: Apuntar a MUI &#40;Multilingual User Interface, Interfaz de usuario multilingüe&#41; de Office](../vsto/how-to-target-the-office-multilingual-user-interface.md)   
 [Tutorial: Crear el primer complemento de VSTO para Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)   
 [Tutorial: Crear la primera personalización en el nivel del documento para Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)   
 [Tutorial: Crear el primer complemento de VSTO para Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)   
 [Tutorial: Crear el primer complemento de VSTO para PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)   
 [Tutorial: Crear el primer complemento de VSTO para Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)   
 [Tutorial: Crear el primer complemento de VSTO para Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)   
 [Tutorial: Crear la primera personalización en el nivel del documento para Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)  
  
  