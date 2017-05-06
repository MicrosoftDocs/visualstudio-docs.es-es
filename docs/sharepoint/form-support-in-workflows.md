---
title: "Compatibilidad con formularios en los flujos de trabajo"
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
  - "desarrollo de SharePoint en Visual Studio, flujos de trabajo"
  - "flujos de trabajo [desarrollo de SharePoint en Visual Studio]"
ms.assetid: 1706f6a2-ea84-4234-85ae-19feb8540507
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Compatibilidad con formularios en los flujos de trabajo
  Se pueden usar cuatro tipos de formularios en un flujo de trabajo: asociación, iniciación, tarea y modificación.  Estos tipos de formulario pueden estar basados en un formulario ASPX o un formulario de InfoPath.  El nivel de compatibilidad que [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] proporciona para un formulario determinado depende de varios factores, que se describen en las siguientes tablas.  Para obtener más información sobre los tipos de formulario de flujo de trabajo, vea [El flujo de trabajo introducción](http://go.microsoft.com/fwlink/?LinkId=185228) en el sitio web de MSDN.  
  
## Refactorización de XML  
 Al agregar una asociación de ASPX o un formulario de iniciación a un elemento de proyecto de flujo de trabajo [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] refactoriza automáticamente el XML en el archivo Elements.xml del flujo de trabajo para mantener el atributo que hace referencia a la asociación o el formulario de iniciación en sincronización cada vez que se actualiza el nombre del formulario o la ruta de distribución o se elimina el formulario.  Sin embargo, al usar otros tipos de formulario en un flujo de trabajo, como, por ejemplo, una tarea o un formulario de modificación, no se refactoriza el archivo Elements.xml.  
  
## Compatibilidad con formularios en los nuevos flujos de trabajo de Visual Studio  
 En la siguiente tabla se hace una lista de la compatibilidad de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] con diferentes tipos de formulario en ASPX o formularios de InfoPath en los flujos de trabajo que se crean en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
|Tipo de formulario|Flujo de trabajo creado en Visual Studio con un formulario ASPX|Flujo de trabajo creado en Visual Studio con un formulario de InfoPath|  
|------------------------|---------------------------------------------------------------------|----------------------------------------------------------------------------|  
|Asociación|-   Se puede agregar un formulario de asociación de ASPX al flujo de trabajo mediante la plantilla de elemento **Formulario de asociación de flujo de trabajo**.<br />-   El archivo Elements.xml del flujo de trabajo se refactoriza cuando se agrega o se elimina el formulario, se le cambia el nombre o se cambia su ruta de distribución.<br />-   Para obtener más información, vea [Tutorial: Crear un flujo de trabajo con formularios de asociación y de iniciación](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-   No hay ninguna plantilla de formulario de asociación de InfoPath en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-   No existe ninguna integración entre [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e InfoPath Designer.<br />-   El archivo Elements.xml del flujo de trabajo no se refactoriza.|  
|Iniciación|-   Se puede agregar un formulario de iniciación de ASPX al flujo de trabajo mediante la plantilla de elemento **Formulario de iniciación de flujo de trabajo**.<br />-   El archivo Elements.xml del flujo de trabajo se refactoriza cuando se agrega o se elimina el formulario, se le cambia el nombre o se cambia su ruta de distribución.<br />-   Para obtener más información, vea [Tutorial: Crear un flujo de trabajo con formularios de asociación y de iniciación](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-   No hay ninguna plantilla de formulario de asociación de InfoPath en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-   No existe ninguna integración entre [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e InfoPath Designer.<br />-   El archivo Elements.xml del flujo de trabajo no se refactoriza.|  
|Tarea|-   No hay ninguna plantilla de formulario de tareas de ASPX disponible en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Se debe crear una página de aplicación y agregarle el código.<br />-   El archivo Elements.xml del flujo de trabajo no se refactoriza.<br />-   Para obtener más información, vea [Formularios de tareas de flujo de trabajo \(base de SharePoint\)](http://go.microsoft.com/fwlink/?LinkId=187674)|-   No hay ninguna plantilla de formulario de tarea de InfoPath en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-   No existe ninguna integración entre [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e InfoPath Designer.<br />-   El archivo Elements.xml del flujo de trabajo no se refactoriza.|  
|Modificación|-   No hay ninguna plantilla de formulario de modificación de ASPX disponible en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Para agregar un formulario de modificación, se debe crear una página de aplicación y agregarle el código.<br />-   El archivo Elements.xml del flujo de trabajo no se refactoriza.  Debe modificarlo manualmente según corresponda.<br />-   Para obtener más información, vea [Formularios de modificación de flujo de trabajo \(base de SharePoint\)](http://go.microsoft.com/fwlink/?LinkId=187675)|-   No hay ninguna plantilla de formulario de modificación de InfoPath en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-   No existe ninguna integración entre [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e InfoPath Designer.<br />-   El archivo Elements.xml del flujo de trabajo no se refactoriza.|  
  
## Compatibilidad con los flujos de trabajo reutilizables de SharePoint importados  
 En la siguiente tabla se hace una lista de la compatibilidad de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] con los diferentes tipos de formulario de ASPX o los formularios de InfoPath en los flujos de trabajo reutilizables de SharePoint importados a [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
|Tipo de formulario|Flujo de trabajo reutilizable que tiene un formulario ASPX importado de SharePoint Designer|Flujo de trabajo reutilizable que tiene un formulario de InfoPath importado de SharePoint Designer|  
|------------------------|-------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------|  
|Asociación|-   Se hace referencia al formulario en el archivo Elements.xml del flujo de trabajo.<br />-   El archivo Elements.xml del flujo de trabajo se refactoriza cuando se elimina el formulario, se le cambia el nombre o se cambia su ruta de distribución.|-   El formulario se importa, pero no se hace referencia al mismo en el archivo Elements.xml del flujo de trabajo.<br />-   El archivo Elements.xml del flujo de trabajo no se refactoriza.|  
|Iniciación|-   El flujo de trabajo hace referencia al formulario en el archivo Elements.xml del flujo de trabajo.<br />-   El archivo Elements.xml del flujo de trabajo se refactoriza cuando se elimina el formulario, se le cambia el nombre o se cambia su ruta de distribución.|-   El formulario se importa, pero no se hace referencia al mismo en el archivo Elements.xml del flujo de trabajo.<br />-   El archivo Elements.xml del flujo de trabajo no se refactoriza. **Note:**  Se deben agregar y cambiar las reglas y propiedades para que este escenario funcione.|  
|Tarea|-   Se hace referencia al formulario en el archivo Elements.xml del flujo de trabajo.<br />-   El archivo Elements.xml del flujo de trabajo no se refactoriza.|-   El formulario se importa, pero no se hace referencia al mismo en el archivo Elements.xml del flujo de trabajo.<br />-   El archivo Elements.xml del flujo de trabajo no se refactoriza. **Note:**  Se deben agregar y cambiar las reglas y propiedades para que este escenario funcione.|  
|Modificación|No es aplicable  Los formularios de modificación de ASPX no se pueden crear en SharePoint Designer.|No es aplicable  En SharePoint Designer no se pueden crear formularios de modificación de InfoPath, salvo el flujo de trabajo de SharePoint Servidor integrado, que no está incluido en el archivo .wsp cuando se exporta el flujo de trabajo.|  
  
## Vea también  
 [Tutorial: Crear un flujo de trabajo con formularios de asociación y de iniciación](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)   
 [Crear soluciones de flujo de trabajo de SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [Importar elementos de un sitio de SharePoint existente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)  
  
  