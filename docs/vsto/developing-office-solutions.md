---
title: Desarrollar soluciones de Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, about developing solutions
- solutions [Office development in Visual Studio], developing
- Office solutions [Office development in Visual Studio], developing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fd5829a3d09d96ad0ed9cfce3dd4bc329e70f907
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
ms.locfileid: "34268193"
---
# <a name="develop-office-solutions"></a>Desarrollar soluciones de Office
  Después de diseñar un proyecto con Office Developer Tools en Visual Studio y configurar los archivos del proyecto, puede empezar a centrarse en la implementación del código y la interfaz de usuario personalizada (UI).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
> [!NOTE]  
>  ¿Está interesado en el desarrollo de soluciones que amplían la experiencia de Office en [varias plataformas](https://dev.office.com/add-in-availability)? Visite la nueva [modelo de complementos de Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Complementos de Office tienen una superficie pequeña en comparación con las soluciones y los complementos de VSTO, y puede compilarlas mediante prácticamente cualquier tecnología, como HTML5, JavaScript, CSS3 y XML de programación web.  
  
## <a name="office-solutions-programming-model"></a>Modelo de programación de soluciones de Office  
 El modelo de objetos de Office expone una variedad de objetos que se pueden programar. Cuando se programan soluciones de Office mediante código administrado, se escribe código que utiliza tipos de los ensamblados de interoperabilidad primarios de Office. En las soluciones que se crean mediante plantillas de proyecto de Office en Visual Studio, también se escribe código directamente relacionado con las clases generadas en el proyecto. Para obtener más información, consulte [escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md).  
  
## <a name="program-different-types-of-office-solutions"></a>Diferentes tipos de soluciones de Office de programa  
 El tipo de solución que esté creando determina las características que puede usar en el proyecto. Por ejemplo, puede agregar controles de formularios Windows Forms y controles de Office extendidos (denominados *controles host*) a las personalizaciones de nivel de documento, arrastrando para ello elementos desde el **cuadro de herramientas** de Visual Studio en tiempo de diseño. Sin embargo, si está desarrollando un complemento de VSTO, solo puede agregar este tipo de controles a los documentos en tiempo de ejecución, mediante la escritura de código.  
  
 Para obtener más información acerca de las características específicas para cada tipo de solución, vea los temas siguientes:  
  
-   [Programar complementos VSTO](../vsto/programming-vsto-add-ins.md).  
  
-   [Programar personalizaciones de nivel de documento](../vsto/programming-document-level-customizations.md).  
  
-   [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md).  
  
 Para que obtener información general le ayudará a planear las soluciones de Office y procedimientos que le ayudarán a crear proyectos, vea [diseño y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md).  
  
## <a name="related-topics"></a>Temas relacionados  
  
|Título|Descripción|  
|-----------|-----------------|  
|[Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)|Describe distintos aspectos de la escritura de código en soluciones de Office.|  
|[Programar complementos VSTO](../vsto/programming-vsto-add-ins.md)|Proporciona información general sobre el modelo de programación de complementos de VSTO y las tareas de programación relacionadas.|  
|[Programar personalizaciones de nivel de documento](../vsto/programming-document-level-customizations.md)|Proporciona información general sobre el modelo de programación de personalizaciones de nivel de documento y las tareas de programación relacionadas.|  
|[Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)|Describe las distintas formas de personalizar las aplicaciones de interfaz de usuario de Office mediante complementos de VSTO y personalizaciones de nivel de documento.|  
|[Datos en soluciones de Office](../vsto/data-in-office-solutions.md)|Describe las distintas maneras de trabajar con datos en soluciones de Office, como enlazar datos a controles y almacenar datos en caché en las personalizaciones de nivel de documento.|  
|[Cómo Autoguardado afecta a las soluciones de Office](./how-autosave-impacts-office-solutions.md)|Describe los ajustes que necesite realizar en las soluciones de Office cuando Autoguardado esté habilitado.|
|[Solucionar problemas de soluciones de Office](../vsto/troubleshooting-office-solutions.md)|Proporciona sugerencias para resolver problemas comunes que pueden surgir al crear soluciones de Office.|  
|[Compatibilidad del subprocesamiento en Office](../vsto/threading-support-in-office.md)|Proporciona información general sobre cómo trabajar con varios subprocesos en soluciones de Office.|  
|[Accesibilidad en proyectos de Office](../vsto/accessibility-in-office-projects.md)|Describe las características de accesibilidad que están disponibles en las soluciones de Office.|  
  
## <a name="see-also"></a>Vea también  
 [Cómo: crear y modificar propiedades de documento personalizadas](../vsto/how-to-create-and-modify-custom-document-properties.md)   
 [Cómo: de lectura y escritura a las propiedades de documento](../vsto/how-to-read-from-and-write-to-document-properties.md)   
 [Cómo: tener como destino la interfaz de usuario multilingüe de Office](../vsto/how-to-target-the-office-multilingual-user-interface.md)   
 [Tutorial: Crear el primer complemento de VSTO para Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)   
 [Tutorial: Crear la primera personalización de nivel de documento para Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)   
 [Tutorial: Crear el primer complemento de VSTO para Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)   
 [Tutorial: Crear el primer complemento de VSTO para PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)   
 [Tutorial: Crear el primer complemento de VSTO para Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)   
 [Tutorial: Crear el primer complemento de VSTO para Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)   
 [Tutorial: Crear la primera personalización de nivel de documento para Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)  
  
  