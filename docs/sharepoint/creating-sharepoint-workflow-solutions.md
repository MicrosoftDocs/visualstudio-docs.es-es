---
title: Creación de soluciones de flujo de trabajo de SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VSTO.NewSharePointWorkflowWizard.Page3
- VS.SharePointTools.Workflow.WorkflowName
- VSTO.NewSharePointWorkflowWizard.Page2
- VSTO.NewSharePointWorkflowWizard.Page1
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d78d82a51f88bfaf076b56692629e801689e103e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443533"
---
# <a name="create-sharepoint-workflow-solutions"></a>Crear soluciones de flujo de trabajo de SharePoint

[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] proporciona herramientas para ayudarle a crear flujos de trabajo personalizados que administran el ciclo de vida de documentos y elementos de lista en un sitio Web de SharePoint. Los elementos proporcionados incluyen un diseñador, un conjunto de controles de la actividad y las referencias de ensamblado necesarias. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] También incluye el **Asistente de personalización de SharePoint**, para ayudar a crear y configurar los flujos de trabajo.

Para obtener más información acerca de SharePoint, vea [Microsoft SharePoint Products and Technologies](http://go.microsoft.com/fwlink/?LinkId=178470).

## <a name="workflows-in-sharepoint"></a>Flujos de trabajo en SharePoint
 Al agregar un flujo de trabajo a una lista o biblioteca de SharePoint, aplicar un proceso empresarial en todos los elementos de la biblioteca o lista. Un flujo de trabajo describe las acciones que el sistema o los usuarios deben realizar en cada elemento, como el envío del elemento que se puede editar y, a continuación, revisar. Estas acciones, conocidas como *actividades*, son los bloques de creación del flujo de trabajo.

 Puede crear flujos de trabajo de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e implementarlas en un sitio Web de SharePoint. Después de implementa un flujo de trabajo en SharePoint, asocia con una lista o biblioteca. Se puede, a continuación, se inicia automáticamente, mediante un proceso o manualmente por el usuario. Para obtener más información acerca de la operación de flujo de trabajo, consulte [flujos de trabajo de desarrollo de SharePoint mediante Visual Studio](https://docs.microsoft.com/sharepoint/dev/general-development/develop-sharepoint-workflows-using-visual-studio).

## <a name="create-custom-sharepoint-workflows"></a>Crear flujos de trabajo personalizados de SharePoint
 Dos proyectos de flujo de trabajo de SharePoint están disponibles en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]: **Flujo de trabajo secuencial** y **flujo de trabajo de máquina de estado**.

 Un *flujo de trabajo secuencial* representa una serie de pasos. Los pasos se realizan una tras otra hasta que se complete la última actividad. Flujos de trabajo secuenciales siempre son estrictamente secuenciales en su ejecución. Ya que pueden recibir eventos externos e incluir flujos paralelos lógicos, el orden exacto de ejecución puede variar. La siguiente ilustración muestra un ejemplo de un flujo de trabajo secuencial.

 ![Flujo de trabajo secuencial](../sharepoint/media/sp-sequential.png "flujo de trabajo secuencial")

 Un *flujo de trabajo de máquina de estados* representa un conjunto de Estados, transiciones y acciones. Los pasos de un flujo de trabajo de máquina de Estados ejecutarán de forma asincrónica. Esto significa que no se realizan necesariamente uno tras otro, pero en su lugar, se activan mediante acciones y Estados. Se asigna un estado como el estado de inicio y, a continuación, en función de un evento, se realiza una transición a otro estado. La máquina de estados puede tener un estado final que determina el final del flujo de trabajo. El siguiente diagrama muestra un ejemplo de un flujo de trabajo de máquina de Estados.

 ![Flujo de trabajo de máquina de estado](../sharepoint/media/sp-state.png "flujo de trabajo de máquina de estado")

 Para obtener más información acerca de los tipos de flujo de trabajo, consulte [tipos de flujo de trabajo](http://go.microsoft.com/fwlink/?LinkId=178995).

### <a name="use-the-wizard"></a>Use el Asistente para
 Cuando se crea un proyecto de flujo de trabajo de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], primero debe especificar su configuración en el **Asistente de personalización de SharePoint**. El asistente usa esta configuración para crear un proyecto en **el Explorador de soluciones**. Este proyecto contiene un archivo de código, varios archivos que se usan para implementar el flujo de trabajo, y las referencias a ensamblados que son necesarios para crear un flujo de trabajo de SharePoint personalizado.

 Después de crear el flujo de trabajo, puede modificar sus propiedades en la ventana Propiedades. Aunque la mayoría de las propiedades de flujo de trabajo se puede cambiar directamente en la ventana Propiedades, algunas requieren que haga clic en el botón de puntos suspensivos (![elipse del Diseñador de ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "elipse del Diseñador de ASP.NET Mobile")) para cambiar sus valores. Este botón se reinicia el **Asistente de personalización de SharePoint**. Después de realizar la propiedad cambia el valor, elija el **finalizar** botón Finalizar de ellos.

> [!NOTE]
> El **tipo flujo de trabajo** propiedad es de solo lectura y no se puede cambiar. Si desea cambiar el tipo de flujo de trabajo, debe crear otro flujo de trabajo.

## <a name="design-a-sharepoint-workflow"></a>Diseñar un flujo de trabajo de SharePoint
 Después de definir todos los pasos en el proceso empresarial, utilice el [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Diseñador de flujo de trabajo para diseñar el flujo de trabajo de SharePoint. Para abrir el diseñador, haga doble clic en Workflow1.cs o Workflow1.vb en **el Explorador de soluciones**, o abra el menú contextual de cualquiera de esos archivos y, a continuación, elija **abrir**.

### <a name="activities"></a>Actividades
 Para diseñar un flujo de trabajo, agregue las actividades desde el **cuadro de herramientas** a un *programación de flujo de trabajo* en el diseñador. Una programación de flujo de trabajo contiene la secuencia de actividades en el orden en que debe realizarse.

 Hay dos tipos de actividades:

- *Actividades simples* realizan una sola unidad de trabajo, tal como "retraso de 1 día" o "iniciar el servicio Web".

- *Las actividades compuestas* contienen otras actividades; por ejemplo, una actividad condicional puede contener dos bifurcaciones.

  Ambos tipos de actividades están disponibles en el **cuadro de herramientas**.

  Las actividades pueden tener propiedades, métodos y eventos. Use la **propiedades** ventana para establecer las propiedades de una actividad.

  También puede crear una actividad personalizada. Para obtener más información, vea [Tutorial: Crear una actividad de flujo de trabajo de sitio personalizada](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md).

  Las actividades se clasifican en las siguientes fichas en la **cuadro de herramientas**:

- **SharePoint Workflow**

- **Windows Workflow v3.0**

- **Windows Workflow v3.5**

  No todas las actividades de flujo de trabajo de core son compatibles con SharePoint. Para obtener más información, consulte [flujo de trabajo para Windows SharePoint Services Introducción a las actividades](http://go.microsoft.com/fwlink/?LinkID=156094).

#### <a name="sharepoint-workflow-activities"></a>Actividades de flujo de trabajo de SharePoint
 El **SharePoint Workflow** pestañas contienen actividades especializadas para su uso en [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]. Estas actividades simplificarán y agilizar el desarrollo de flujos de trabajo de ciclo de vida de documento. Para obtener más información acerca de las actividades que se muestran en el **SharePoint Workflow** pestaña, vea [flujo de trabajo para Windows SharePoint Services Introducción a las actividades](http://go.microsoft.com/fwlink/?LinkID=156094).

#### <a name="windows-workflow-activities"></a>Actividades de flujo de trabajo de Windows
 El **flujo de trabajo de Windows** pestañas contienen las actividades proporcionadas por el [!INCLUDE[TLA#tla_workflow](../sharepoint/includes/tlasharptla-workflow-md.md)]. Puede utilizar estas actividades para crear programaciones de flujo de trabajo para cualquier tipo de aplicación de flujo de trabajo de Windows.

 Para obtener más información acerca de las actividades que se muestran en el **flujos de trabajo de Windows** pestaña, vea [actividades Windows Workflow Foundation](http://go.microsoft.com/fwlink/?LinkID=156096). Para obtener más información acerca de la Windows Workflow Foundation, consulte [información general de Windows Workflow Foundation](http://go.microsoft.com/fwlink/?LinkID=128632).

### <a name="work-with-activities-in-the-designer"></a>Trabajar con actividades en el diseñador
 La programación de flujo de trabajo puede contener una combinación de las actividades de flujo de trabajo de Windows y las actividades de flujo de trabajo de SharePoint.

 El diseñador muestra indicaciones visuales para ayudarle a colocar y configurar actividades correctamente. Al arrastrar o copiar una actividad en la programación de flujo de trabajo, el diseñador muestra iconos de signo más verde (+) que indican las ubicaciones válidas para esa actividad del flujo de trabajo. No se puede colocar una actividad en una ubicación donde no sería válida. Por ejemplo, no puede colocar una actividad Send como primera actividad en una rama de actividad Listen. Para obtener más información, consulte [Centro para desarrolladores de SharePoint Designer](http://go.microsoft.com/fwlink/?LinkId=178476).

## <a name="collect-information-during-the-workflow"></a>Recopilar información durante el flujo de trabajo
 Es posible que desee recopilar información de usuarios en momentos en el flujo de trabajo predefinidos. Puede recopilar información mediante formularios o propiedades del elemento.

### <a name="forms"></a>Formularios
 Los formularios son como cuadros de diálogo que contienen preguntas y proporcionan maneras para que los usuarios dar respuestas.

 Hay cuatro tipos de formularios que se pueden usar en un flujo de trabajo:

- Asociación

- Iniciación

- Modificación

- Tarea

  De estos, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] incluye plantillas de elementos para formularios de asociación e iniciación. Un ejemplo de un *formulario de asociación* es uno que permite al administrador instalar el flujo de trabajo escriba los parámetros que se relacionan con el flujo de trabajo, como un límite de gasto para un flujo de trabajo de gastos. Un ejemplo de un *formulario de iniciación* es aquel que permite al usuario de un flujo de trabajo de gastos escriba la cantidad que se ha gastado en el flujo de trabajo. Para obtener más información acerca de estos tipos de formularios, consulte [SharePoint plantillas de elemento de proyecto y](../sharepoint/sharepoint-project-and-project-item-templates.md).

### <a name="item-properties"></a>Propiedades del elemento
 También puede recopilar información de los usuarios mediante las propiedades de un elemento en la lista o biblioteca de SharePoint. El archivo de código principal (Workflow1.cs o Workflow1.vb) declara una instancia de la clase Microsoft.SharePoint.Workflow.SPWorkflowActivationProperties.WorkflowProperties denominada `workflowProperties`. Use la `workflowProperties` objeto para tener acceso a las propiedades de la biblioteca o una lista de código. Para obtener un ejemplo, vea [Tutorial: Crear y depurar una solución de flujo de trabajo de SharePoint](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md).

## <a name="debug-a-sharepoint-workflow-template"></a>Depurar una plantilla de flujo de trabajo de SharePoint
 Puede depurar un proyecto de flujo de trabajo de SharePoint igual cuando depura otros [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] proyectos basados en Web. Al iniciar el [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] depurador, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] usa la configuración que especifique en el **Asistente de personalización de SharePoint** para abrir el sitio SharePoint Web adecuado y asociar automáticamente la plantilla de flujo de trabajo con la lista o biblioteca adecuada. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] también asocia el [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] del depurador para el [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] proceso denominado *w3wp.exe*.

 Para probar el flujo de trabajo, debe iniciarlo manualmente. Para obtener más información, vea la sección "Depuración de flujos de trabajo" en [depurar soluciones de SharePoint](../sharepoint/debugging-sharepoint-solutions.md). Para obtener más información acerca de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] depuración de aplicaciones Web, consulte [depurar script y aplicaciones web](../debugger/how-to-enable-debugging-for-aspnet-applications.md).

## <a name="deploy-a-sharepoint-workflow-template"></a>Implementar una plantilla de flujo de trabajo de SharePoint
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Implementación proyectos de flujo de trabajo de SharePoint como otro [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] los proyectos de SharePoint. Para obtener más información, consulte [soluciones de paquete y de implementar SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md).

## <a name="import-globally-reusable-workflows"></a>Importar flujos de trabajo reutilizables globalmente
 Además de crear flujos de trabajo reutilizables específica del sitio, SharePoint Designer le permite crear *flujos de trabajo reutilizables globalmente*, que son flujos de trabajo que se pueden usar cualquier sitio de SharePoint. El proyecto Importar flujo de trabajo reutilizable en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] actualmente importar flujos de trabajo reutilizables globalmente. Sin embargo, puede usar SharePoint Designer para convertir un flujo de trabajo reutilizable globalmente en un flujo de trabajo reutilizable o importar el flujo de trabajo como un flujo de trabajo declarativo no convertido. Para obtener más información, consulte [importar elementos de un sitio de SharePoint existente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

## <a name="related-topics"></a>Temas relacionados

|Título|Descripción|
|-----------|-----------------|
|[Tutorial: Crear y depurar una solución de flujo de trabajo de SharePoint](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md)|Le guía paso a paso para crear y depurar un sencillo [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] flujo de trabajo.|
|[Tutorial: Crear un flujo de trabajo con formularios de asociación e iniciación](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)|Le guía paso a paso para crear una más completa [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] completar el flujo de trabajo con formularios de asociación e iniciación.|
|[Tutorial: Agregar una página de aplicación a un flujo de trabajo](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)|Se basa en el tema [Tutorial: Crear un flujo de trabajo con formularios de asociación e iniciación](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) agregando más *.aspx* página de aplicación que informa sobre los datos introducidos en el flujo de trabajo.|
|[Tutorial: Crear una actividad de flujo de trabajo de sitio personalizada](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md)|Muestra cómo realizar dos tareas fundamentales: crear un flujo de trabajo de nivel de sitio y crear una actividad de flujo de trabajo personalizado.|
|[Tutorial: Importar un flujo de trabajo reutilizable de SharePoint Designer en Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)|Muestra cómo se importan flujos de trabajo declarativos reutilizables creados en SharePoint Designer 2010 en un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] proyecto de SharePoint.|

## <a name="see-also"></a>Vea también

- [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Build and debug SharePoint solutions](../sharepoint/building-and-debugging-sharepoint-solutions.md) (Compilar y depurar las soluciones de SharePoint)
- [Crear páginas de aplicación para SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)