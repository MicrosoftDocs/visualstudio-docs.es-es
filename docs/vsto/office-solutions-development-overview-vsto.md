---
title: "Informaci&#243;n general sobre el desarrollo de soluciones de Office (VSTO) | Microsoft Docs"
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
  - "ensamblados de interoperabilidad primarios, Office"
  - "desarrollo de Office en Visual Studio, acerca del desarrollo de soluciones"
ms.assetid: 5dfc519f-a851-4661-8d2b-47e0d221e10e
caps.latest.revision: 69
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 68
---
# Informaci&#243;n general sobre el desarrollo de soluciones de Office (VSTO)
  Mediante el uso de Microsoft Office como front\-end de soluciones, puede beneficiarse de las conocidas interfaces de usuario y herramientas de Microsoft Office, como las características de procesamiento de texto de Word, las características de análisis de datos de Excel y las características de administración de correo electrónico de Outlook. Puede desarrollar soluciones en Visual Studio para personalizar las aplicaciones de Office y agregar las características específicas que necesite para sus procesos empresariales. Por ejemplo, puede convertir Word en un generador de contratos que ensamble contratos a partir de elementos previamente existentes que se pueden hacer modificables o no modificables. Con Excel puede crear una hoja de cálculo de presupuestos automatizada y personalizada para distintos proyectos. Los usuarios pueden aprovechar las soluciones de Office sin conexión, lo que hace que soluciones complejas resulten más prácticas de lo que serían si utilizase una arquitectura basada en web.  
  
 Este tema proporciona información general sobre los tipos de soluciones de Office que puede crear mediante el uso de plantillas de Visual Studio Tools para Office \(VSTO\) disponibles en Office Developer Tools en Visual Studio. Para información general sobre cómo desarrollar con Office, vea el [Centro para desarrolladores de Office](https://dev.office.com/).  
  
## Elegir un tipo de proyecto de Office  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] proporciona los siguientes tipos de plantillas de proyecto para el desarrollo de Office basado en VSTO:  
  
-   Las **personalizaciones de nivel de documento** están asociadas a un documento concreto.  
  
-   **VSTO Add\-ins** están asociados a la propia aplicación.  
  
 Para decidir cuál de estos tipos de proyecto es mejor para su solución, piense si desea que su código se ejecute únicamente cuando se abra un documento específico o si desea que el código esté disponible cada vez que se ejecute la aplicación. Para más información sobre las plantillas de proyecto, vea [Información general sobre las plantillas de Office Project](../vsto/office-project-templates-overview.md).  
  
 Los tipos de proyectos que puede crear dependen de las aplicaciones de Office que haya instalado en el equipo de desarrollo. Para obtener más información, consulta [Características disponibles por aplicación y tipo de proyecto de Office](../vsto/features-available-by-office-application-and-project-type.md).  
  
### Personalizaciones de nivel de documento  
 Las personalizaciones de nivel de documento constan de un ensamblado que está asociado a un único documento, libro o plantilla de Microsoft Office Word o Microsoft Office Excel. El ensamblado se carga cuando se abre el documento asociado. Las características de las personalizaciones que se crean están disponibles solo cuando se abre el documento asociado. Las personalizaciones no pueden realizar cambios en toda la aplicación, como mostrar un nuevo elemento de menú o una ficha de cinta cuando se abre cualquier documento.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] incluye herramientas que le ayudan a crear personalizaciones de nivel de documento. El documento que se personaliza se hospeda como una superficie de diseño en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], lo que permite diseñar el documento arrastrando y colocando controles en él. Muchas otras características de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] están disponibles en proyectos de nivel de documento, como son los controles de Windows Forms, el enlace de datos con la función de arrastrar y colocar, y un depurador integrado.  
  
 Para obtener más información sobre las personalizaciones, vea los siguientes temas:  
  
-   [Introducción a la programación de personalizaciones de nivel de documento para Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md)  
  
-   [Introducción a la programación de personalizaciones de nivel de documento para Word](../vsto/getting-started-programming-document-level-customizations-for-word.md)  
  
-   [Arquitectura de las personalizaciones de nivel de documento](../vsto/architecture-of-document-level-customizations.md)  
  
### Complementos de VSTO  
 Los complementos de VSTO constan de un ensamblado que está asociado a una aplicación de Microsoft Office. Normalmente, el complemento de VSTO se ejecuta cuando se inicia la aplicación asociada, aunque los usuarios también pueden cargar complementos de VSTO cuando la aplicación ya se está ejecutando. Las características de los complementos de VSTO que cree estarán disponibles para la propia aplicación, con independencia de qué documentos se abran.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] incluye herramientas que le ayudan a crear complementos de VSTO. Los proyectos de complemento incluyen una clase generada automáticamente que representa el complemento de VSTO. Esta clase proporciona propiedades y eventos que puede utilizar para acceder al modelo de objetos de la aplicación host y ejecutar código cuando el complemento de VSTO se carga y se apaga. Muchas otras características de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] están disponibles en los proyectos de complementos de VSTO, como Windows Forms y un depurador integrado.  
  
 Para obtener más información sobre complementos de VSTO, vea los siguientes temas:  
  
-   [Introducción a la programación de complementos de VSTO](../vsto/getting-started-programming-vsto-add-ins.md)  
  
-   [Arquitectura de complementos de VSTO](../vsto/architecture-of-vsto-add-ins.md)  
  
## Automatización de aplicaciones de Office mediante el uso de ensamblados de interoperabilidad primarios  
 Mediante programación, puede incorporar las características de una aplicación de Office en su solución escribiendo código que acceda al modelo de objetos de la aplicación. Los modelos de objetos son una disposición de clases que exponen funcionalidades a través de diversos métodos y propiedades. El modelo de objetos de cada aplicación de Office es diferente.  
  
 Para utilizar el modelo de objetos de una aplicación de Office desde una solución creada con las herramientas de desarrollo de Office en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], debe utilizar el ensamblado de interoperabilidad primario \(PIA\) de la aplicación. El PIA permite al código administrado de una solución interactuar con el modelo de objetos basado en COM de la aplicación de Office.  
  
 Para realizar la mayoría de las tareas de desarrollo, debe tener los PIA de Office instalados y registrados en la caché global de ensamblados del equipo de desarrollo. Para obtener más información, consulta [Configurar un equipo para desarrollar soluciones de Office](../vsto/configuring-a-computer-to-develop-office-solutions.md). Los PIA de Office no son obligatorios en los equipos de los usuarios finales para ejecutar soluciones de Office de VSTO. Para obtener más información, consulta [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md).  
  
 Para obtener más información acerca de cómo utilizar los PIA en las soluciones de Office de VSTO, vea los siguientes temas:  
  
-   [Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)  
  
-   [Ensamblados de interoperabilidad primarios de Office](../vsto/office-primary-interop-assemblies.md)  
  
## Ejecutar soluciones de Office de Microsoft VSTO en equipos de usuarios finales  
 Al crear una solución de Office de VSTO, tenga en cuenta cómo pueden afectar los requisitos de implementación a las opciones de desarrollo.  
  
### Opciones de implementación  
 Use ClickOnce o Windows Installer para implementar soluciones que cree mediante el uso de las herramientas de desarrollo de Office de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. La implementación mediante ClickOnce le permite crear soluciones de actualización automática que se pueden instalar y ejecutar con una mínima interacción por parte del usuario. Los archivos de Windows Installer \(.msi\) se pueden distribuir fácilmente a los equipos de usuarios finales o mediante Systems Management Server \(SMS\). Para más información sobre cómo implementar soluciones de Office de VSTO, consulte [Implementar una solución de Office](../vsto/deploying-an-office-solution.md).  
  
### Instalar los requisitos previos  
 Antes de que los usuarios finales puedan ejecutar una solución que haya creado mediante las herramientas de desarrollo de Office de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], sus equipos deben disponer de ciertos requisitos previos. Si implementa su solución mediante ClickOnce o creando un archivo de Windows Installer, estos requisitos previos se pueden instalar con la solución. Para más información, consulte [Requisitos previos de la solución de Office para la implementación](http://msdn.microsoft.com/es-es/9f672809-43a3-40a1-9057-397ce3b5126e) y [Cómo instalar los requisitos previos en equipos de usuarios finales para ejecutar soluciones de Office de VSTO](http://msdn.microsoft.com/es-es/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).  
  
### Seguridad  
 La seguridad para las soluciones de Office de VSTO se ejecuta mediante una serie de comprobaciones que realiza [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] al instalar y cargar la solución. Estas comprobaciones incluyen comprobar si son de confianza la ubicación del manifiesto de implementación o el certificado que se ha usado para firmar este manifiesto. Para obtener más información, consulta [Asegurar las soluciones de Office](../vsto/securing-office-solutions.md).  
  
## Vea también  
 [Introducción &#40;Desarrollo de Office en Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Arquitectura de las personalizaciones de nivel de documento](../vsto/architecture-of-document-level-customizations.md)   
 [Arquitectura de complementos de VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Introducción a la programación de personalizaciones de nivel de documento para Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md)   
 [Introducción a la programación de personalizaciones de nivel de documento para Word](../vsto/getting-started-programming-document-level-customizations-for-word.md)   
 [Introducción a la programación de complementos de VSTO](../vsto/getting-started-programming-vsto-add-ins.md)  
  
  