---
title: Desarrollar soluciones de Office | Documentos de Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, about developing solutions
- solutions [Office development in Visual Studio], developing
- Office solutions [Office development in Visual Studio], developing
ms.assetid: 7361cfe0-dee4-48d7-a066-232f87f093ca
caps.latest.revision: "34"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: b15c9fbf2815132ac4ad84e3b321bb22db199ed2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="developing-office-solutions"></a>Desarrollar soluciones de Office
  Después de diseñar un proyecto con Office Developer Tools en Visual Studio y configurar los archivos del proyecto, puede empezar a centrarse en la implementación del código y la interfaz de usuario personalizada (UI).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
> [!NOTE]  
>  ¿Está interesado en el desarrollo de soluciones que amplían la experiencia de Office en [varias plataformas](https://dev.office.com/add-in-availability)? Visite la nueva [modelo de complementos de Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Complementos de Office tienen una superficie pequeña en comparación con las soluciones y complementos VSTO, y puede compilarlas mediante prácticamente cualquier tecnología, como HTML5, JavaScript, CSS3 y XML de programación web.  
  
## <a name="office-solutions-programming-model"></a>Modelo de programación de soluciones de Office  
 El modelo de objetos de Office expone una variedad de objetos que se pueden programar. Cuando se programan soluciones de Office mediante código administrado, se escribe código que utiliza tipos de los ensamblados de interoperabilidad primarios de Office. En las soluciones que se crean mediante plantillas de proyecto de Office en Visual Studio, también se escribe código directamente relacionado con las clases generadas en el proyecto. Para obtener más información, consulta [Writing Code in Office Solutions](../vsto/writing-code-in-office-solutions.md).  
  
## <a name="programming-different-types-of-office-solutions"></a>Programar diferentes tipos de soluciones de Office  
 El tipo de solución que esté creando determina las características que puede usar en el proyecto. Por ejemplo, puede agregar controles de formularios Windows Forms y controles de Office extendidos (denominados *controles host*) a las personalizaciones de nivel de documento, arrastrando para ello elementos desde el **cuadro de herramientas** de Visual Studio en tiempo de diseño. Sin embargo, si está desarrollando un complemento de VSTO, solo puede agregar este tipo de controles a los documentos en tiempo de ejecución, mediante la escritura de código.  
  
 Para obtener más información acerca de las características específicas para cada tipo de solución, vea los temas siguientes:  
  
-   [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
-   [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md).  
  
-   [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md).  
  
 Para obtener información general con la que le resultará más fácil planear las soluciones de Office y procedimientos que le ayudarán a crear proyectos, consulte [Designing and Creating Office Solutions](../vsto/designing-and-creating-office-solutions.md)  
  
## <a name="related-topics"></a>Temas relacionados  
  
|Título|Descripción|  
|-----------|-----------------|  
|[Writing Code in Office Solutions](../vsto/writing-code-in-office-solutions.md)|Describe distintos aspectos de la escritura de código en soluciones de Office.|  
|[Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)|Proporciona información general sobre el modelo de programación de complementos de VSTO y las tareas de programación relacionadas.|  
|[Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md)|Proporciona información general sobre el modelo de programación de personalizaciones de nivel de documento y las tareas de programación relacionadas.|  
|[Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)|Describe las distintas formas de personalizar las aplicaciones de interfaz de usuario de Office mediante complementos de VSTO y personalizaciones de nivel de documento.|  
|[Datos en las soluciones de Office](../vsto/data-in-office-solutions.md)|Describe las distintas maneras de trabajar con datos en soluciones de Office, como enlazar datos a controles y almacenar datos en caché en las personalizaciones de nivel de documento.|  
|[Cómo el autoguardado afecta a las soluciones de Office](./how-autosave-impacts-office-solutions.md)|Describe los ajustes que necesite realizar en las soluciones de Office cuando Autoguardado esté habilitado.|
|[Solución de problemas de soluciones de Office](../vsto/troubleshooting-office-solutions.md)|Proporciona sugerencias para resolver problemas comunes que pueden surgir al crear soluciones de Office.|  
|[Compatibilidad de subprocesos en Office](../vsto/threading-support-in-office.md)|Proporciona información general sobre cómo trabajar con varios subprocesos en soluciones de Office.|  
|[Accesibilidad en proyectos de Office](../vsto/accessibility-in-office-projects.md)|Describe las características de accesibilidad que están disponibles en las soluciones de Office.|  
  
## <a name="see-also"></a>Vea también  
 [Cómo: crear y modificar propiedades de documento personalizadas](../vsto/how-to-create-and-modify-custom-document-properties.md)   
 [Cómo: leer y escribir en Propiedades de un documento](../vsto/how-to-read-from-and-write-to-document-properties.md)   
 [Cómo: tener como destino la interfaz de usuario multilingüe de Office](../vsto/how-to-target-the-office-multilingual-user-interface.md)   
 [Tutorial: Crear el primer complemento de VSTO para Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)   
 [Tutorial: Crear la primera personalización de nivel de documento para Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)   
 [Tutorial: Crear el primer complemento VSTO para Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)   
 [Tutorial: Crear el primer complemento VSTO para PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)   
 [Tutorial: Crear el primer complemento VSTO para el proyecto](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)   
 [Tutorial: Crear el primer complemento VSTO para Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)   
 [Tutorial: Creación de la primera personalización en el nivel del documento para Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)  
  
  