---
title: "Crear soluciones de flujo de trabajo de SharePoint | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VSTO.NewSharePointWorkflowWizard.Page3"
  - "VS.SharePointTools.Workflow.WorkflowName"
  - "VSTO.NewSharePointWorkflowWizard.Page2"
  - "VSTO.NewSharePointWorkflowWizard.Page1"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "desarrollo de SharePoint en Visual Studio, flujos de trabajo"
  - "flujos de trabajo [desarrollo de SharePoint en Visual Studio]"
ms.assetid: fe79b99a-cb7c-4a14-8d9f-bce0c0805ba0
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Crear soluciones de flujo de trabajo de SharePoint
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] proporciona herramientas que ayudan a crear flujos de trabajo personalizados para administrar el ciclo de vida de los documentos y los elementos de lista de un sitio web de SharePoint.  Los elementos proporcionados incluyen un diseñador, un conjunto de controles de actividad, y las referencias de ensamblado necesarias.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] también incluye el **Asistente para la personalización de SharePoint** que ayuda a crear y configurar los flujos de trabajo.  
  
 Para obtener una lista de los requisitos previos para crear proyectos de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], vea [Requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  Para obtener más información sobre SharePoint, vea[Microsoft SharePoint Productos y Tecnologías](http://go.microsoft.com/fwlink/?LinkId=178470).  
  
## Flujos de trabajo en SharePoint  
 Al agregar un flujo de trabajo a una biblioteca o una lista de SharePoint, se aplica un proceso de negocio a todos los elementos de la biblioteca o la lista.  Un flujo de trabajo describe las acciones que deben realizar en cada elemento el sistema o los usuarios, como enviar el elemento para editarlo y revisarlo a continuación.  Estas acciones, conocidas como *actividades*, son los bloques de compilación del flujo de trabajo.  
  
 Puede crear los flujos de trabajo de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e implementarlos en un sitio web de SharePoint.  Una vez implementado un flujo de trabajo en SharePoint, lo tiene que asociar a una biblioteca o lista.  A continuación el flujo de trabajo lo puede iniciar un proceso automáticamente o un usuario manualmente.  Para obtener más información sobre la operación de flujo de trabajo, vea [Utilizando los flujos de trabajo para administrar procesos](http://go.microsoft.com/fwlink/?LinkId=79757).  
  
## Crear flujos de trabajo de SharePoint personalizados  
 Dispone de dos proyectos de flujo de trabajo de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]: **Flujo de trabajo secuencial** y **Flujo de trabajo de máquina de estados.**  
  
 Un *flujo de trabajo secuencial* representa una serie de pasos.  Los pasos se realizan uno tras otro hasta que se complete la última actividad.  Los flujos de trabajo secuenciales siempre son estrictamente secuenciales en su ejecución.  Como pueden recibir eventos externos e incluyen flujos de lógica paralelos, el orden exacto de ejecución puede variar.  En la ilustración siguiente se muestra un ejemplo de un flujo de trabajo secuencial.  
  
 ![Flujo de trabajo secuencial](../sharepoint/media/sp-sequential.png "Flujo de trabajo secuencial")  
  
 Un *flujo de trabajo de equipo de estado* representa un conjunto de estados, transiciones y acciones.  Los pasos de un flujo de trabajo de máquina de estados se ejecutan de forma asincrónica.  Esto significa que no se realizan necesariamente uno después de otro, sino que se activan por acciones y estados.  Se indica un estado como estado de inicio y, a continuación, se hace una transición a otro estado, en función de un evento.  La máquina de estados puede tener un estado final que determina el fin del flujo de trabajo.  En el diagrama siguiente se muestra un ejemplo de un flujo de trabajo de equipo de estado.  
  
 ![Flujo de trabajo de equipo de estado](../sharepoint/media/sp-state.png "Flujo de trabajo de equipo de estado")  
  
 Para obtener más información sobre los tipos de flujo de trabajo, vea [Los tipos de flujo de trabajo](http://go.microsoft.com/fwlink/?LinkId=178995).  
  
### Utilizar el asistente  
 Cuando crear un proyecto de flujo de trabajo de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], primero especifica su configuración en el **Asistente para la personalización de SharePoint**.  El asistente usa esta configuración para crear un proyecto en el **Explorador de soluciones**.  Este proyecto contiene un archivo de código, varios archivos que se utilizan para implementar la plantilla de flujo de trabajo y las referencias a ensamblados necesarias para crear un flujo de trabajo de SharePoint personalizado.  
  
 Después de crear el flujo de trabajo, puede modificar sus propiedades en la ventana Propiedades.  Aunque la mayoría de las propiedades de flujo de trabajo se pueden cambiar directamente en la ventana Propiedades, algunas requieren que haga clic en un botón de puntos suspensivos \(![Elipse del Diseñador de ASP.NET Mobile](../sharepoint/media/mwellipsis.png "Elipse del Diseñador de ASP.NET Mobile")\) para cambiar sus valores.  Este botón reinicia el **Asistente para la personalización de SharePoint**.  Después de realizar los cambios de valores de propiedad, elija el botón de **Finalizar** para finalizarlos.  
  
> [!NOTE]  
>  La propiedad **Workflow Type** es de solo lectura y no se puede cambiar.  Si desea cambiar el tipo de flujo de trabajo, debe crear otro flujo de trabajo.  
  
## Diseñar un flujo de trabajo de SharePoint  
 Después de definir todos los pasos del proceso, utilice el diseñador de flujo de trabajo de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] para diseñar el flujo de trabajo de SharePoint.  Para abrir el diseñador, haga doble clic en Workflow1.cs o Workflow1.vb en **Explorador de soluciones**, o abrir el menú contextual para cualquiera de esos archivos y elegir **Abierta**.  
  
### Actividades  
 Para diseñar un flujo de trabajo, agregue actividades del **Cuadro de herramientas** a una *programación de flujo de trabajo* del diseñador.  Una programación de flujo de trabajo contiene la secuencia de actividades en el orden en que se deben realizar.  
  
 Hay dos tipos de actividades:  
  
-   *Actividades simples*, que realizan una única unidad de trabajo, como "retrasar 1 día" o "iniciar servicio Web".  
  
-   *Actividades compuestas*, que contienen otras actividades; por ejemplo, una actividad condicional puede contener dos bifurcaciones.  
  
 Ambos tipos de actividades están disponibles en el **Cuadro de herramientas**.  
  
 Las actividades pueden tener propiedades, métodos y eventos.  Utilice la ventana **Propiedades** para establecer las propiedades de una actividad.  
  
 También puede crear una actividad personalizada.  Para obtener más información, vea [Tutorial: Crear una actividad de flujo de trabajo personalizada](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md).  
  
 Las actividades se organizan en las dos pestañas siguientes del **Cuadro de herramientas**:  
  
-   **Flujo de trabajo de SharePoint**  
  
-   **Windows Workflow v3.0**  
  
-   **Windows Workflow v3.5**  
  
 No todas las actividades de flujo de trabajo básicas se admiten en SharePoint.  Para obtener más información, vea [Actividades de flujo de trabajo para obtener información general de Windows SharePoint services](http://go.microsoft.com/fwlink/?LinkID=156094).  
  
#### Actividades de flujo de trabajo de SharePoint  
 Las pestañas de **Flujo de trabajo de SharePoint** contienen actividades especializadas que se van a usar en [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)].  Estas actividades simplifican y aprovechan el desarrollo de flujos de trabajo de ciclo de vida de documento.  Para obtener más información sobre las actividades enumeradas en la pestaña de **Flujo de trabajo de SharePoint** , vea[Actividades de flujo de trabajo para obtener información general de Windows SharePoint services](http://go.microsoft.com/fwlink/?LinkID=156094).  
  
#### Actividades de flujo de trabajo de Windows  
 Las pestañas **Windows Workflow** contienen actividades que proporciona [!INCLUDE[TLA#tla_workflow](../sharepoint/includes/tlasharptla-workflow-md.md)].  Puede utilizar estas actividades para crear programaciones de flujos de trabajo para cualquier tipo de aplicación de flujo de trabajo de Windows.  
  
 Para obtener más información sobre las actividades enumeradas en la pestaña de **Flujos de trabajo de Windows** , vea [Actividades de Windows Workflow Foundation](http://go.microsoft.com/fwlink/?LinkID=156096).  Para obtener más información sobre Windows Workflow Foundation, vea [Información general de Windows Workflow Foundation](http://go.microsoft.com/fwlink/?LinkID=128632).  
  
### Trabajar con actividades en el Diseñador  
 La programación del flujo de trabajo puede contener una combinación de actividades de flujo de trabajo de Windows y de SharePoint.  
  
 El diseñador muestra indicaciones visuales para ayudarle a ubicar y configurar las actividades correctamente.  Al arrastrar o copia una actividad a la programación del flujo de trabajo, iconos de signo más verdes del diseñador \(\+\) que indican las ubicaciones válidas para esa actividad en el flujo de trabajo.  No puede colocar una actividad en una ubicación donde no es válida.  Por ejemplo, no puede colocar una actividad de envío como primera actividad de una bifurcación de actividades de escucha.  Para obtener más información, vea [Centro de desarrollador diseñador de SharePoint](http://go.microsoft.com/fwlink/?LinkId=178476).  
  
## Recopilar información durante el flujo de trabajo  
 Puede que desee recopilar información de los usuarios en momentos predefinidos del flujo de trabajo.  Para recopilar información utilice formularios o propiedades de elementos.  
  
### Formularios  
 Los formularios son como cuadros de diálogo que contienen preguntas y proporcionan métodos para obtener respuestas de los usuarios.  
  
 Hay cuatro tipos de formularios que se pueden usar en un flujo de trabajo:  
  
-   Asociación  
  
-   Iniciación  
  
-   Modificación  
  
-   Tarea  
  
 De estos, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] incluye plantillas de elementos para los formularios de asociación e iniciación.  Un ejemplo de un *formulario de asociación* es uno que permite al administrador que instala el flujo de trabajo escribir parámetros que se relacionan con el flujo de trabajo, como un límite del gastos para un flujo de trabajo de gastos.  Un ejemplo *de un formulario de iniciación* es aquel que permite al usuario de un flujo de trabajo de gastos escribir la cantidad que dedicaron al flujo de trabajo.  Para obtener más información sobre estos tipos de formularios, vea [Plantillas de proyecto y de elementos de proyecto de SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
### Propiedades de elemento  
 Para recopilar información de los usuarios también puede utilizar las propiedades de un elemento de la biblioteca o la lista de SharePoint.  El archivo de código principal \(Workflow1.cs o Workflow1.vb\) declara una instancia de la clase Microsoft.SharePoint.Workflow.SPWorkflowActivationProperties.WorkflowProperties denominada `workflowProperties`.  Utilice el objeto `workflowProperties` para obtener acceso a las propiedades de la biblioteca o la lista en el código.  Para obtener un ejemplo, vea [Tutorial: Crear y depurar una solución de flujo de trabajo de SharePoint](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md).  
  
## Depurar una plantilla de flujo de trabajo de SharePoint  
 Puede depurar un proyecto de flujo de trabajo de SharePoint de la misma forma que otros proyectos basados en Web de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Cuando se inicia el depurador de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] utiliza los valores especificados en el **Asistente para la personalización de SharePoint** para abrir el sitio web de SharePoint adecuado y asociar automáticamente la plantilla de flujo de trabajo a la biblioteca o lista correspondiente.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] también adjunta el depurador de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] al proceso de [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] denominado w3wp.exe.  
  
 Para probar el flujo de trabajo, debe iniciarlo manualmente.  Para obtener más información, vea la sección "Depurar flujos de trabajo" en el tema [Depurar soluciones de SharePoint](../sharepoint/debugging-sharepoint-solutions.md).  Para obtener más información sobre la depuración de aplicaciones web en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], vea [Depurar script y aplicaciones web](../debugger/debugging-web-applications-and-script.md).  
  
## Implementar una plantilla de flujo de trabajo de SharePoint  
 Los proyectos de flujo de trabajo de SharePoint de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] se implementan del mismo modo que los demás proyectos de SharePoint de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Para obtener más información, vea [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md).  
  
## Importar flujos de trabajo reutilizables globalmente  
 Además de crear flujos de trabajo reutilizables específicos para sitios, SharePoint Designer permite crear *flujos de trabajo reutilizables globalmente*, que son flujos de trabajo que se pueden usar en cualquier sitio de SharePoint.  El proyecto de flujo de trabajo reutilizable de importación en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] no importa actualmente flujos de trabajo reutilizables globalmente.  Sin embargo, puede usar SharePoint Designer para convertir un flujo de trabajo reutilizable globalmente en un flujo de trabajo reutilizable o importar el flujo de trabajo como un flujo de trabajo declarativo sin convertir.  Para obtener más información, vea [Importar elementos de un sitio de SharePoint existente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).  
  
## Temas relacionados  
  
|Título|Descripción|  
|------------|-----------------|  
|[Tutorial: Crear y depurar una solución de flujo de trabajo de SharePoint](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md)|Ofrece instrucciones paso a paso para crear y depurar un flujo de trabajo de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] simple.|  
|[Tutorial: Crear un flujo de trabajo con formularios de asociación y de iniciación](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)|Ofrece instrucciones paso a paso para crear un flujo de trabajo de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] completo con formularios de iniciación y asociación.|  
|[Tutorial: Agregar una página de aplicación a un flujo de trabajo](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)|Parte del tema [Tutorial: Crear un flujo de trabajo con formularios de asociación y de iniciación](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) y agrega una página de aplicación de .aspx adicional que informa sobre los datos escritos en el flujo de trabajo.|  
|[Tutorial: Crear una actividad de flujo de trabajo personalizada](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md)|Muestra cómo realizar dos tareas clave: crear un flujo de trabajo de nivel de sitio y crear una actividad de flujo de trabajo personalizada.|  
|[Tutorial: Importar un flujo de trabajo reutilizable de SharePoint Designer en Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)|Muestra cómo importar flujos de trabajo declarativos reutilizables creados en SharePoint Designer 2010 en un proyecto de SharePoint de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|  
  
## Vea también  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [Compilar y depurar soluciones de SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Crear páginas de aplicación para SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)  
  
  