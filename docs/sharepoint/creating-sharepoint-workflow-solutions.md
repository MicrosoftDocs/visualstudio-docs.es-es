---
title: Creación de soluciones de flujo de trabajo de SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
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
ms.openlocfilehash: 2c787009577735213437140513ec095f81c3f43b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015280"
---
# <a name="create-sharepoint-workflow-solutions"></a>Creación de soluciones de flujo de trabajo de SharePoint

[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] proporciona herramientas para ayudarle a crear flujos de trabajo personalizados que administran el ciclo de vida de los documentos y los elementos de lista de un sitio web de SharePoint. Entre los elementos proporcionados se incluyen un diseñador, un conjunto de controles de actividad y las referencias de ensamblado necesarias. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] también incluye el **Asistente para la personalización de SharePoint** a fin de facilitar la creación y configuración de flujos de trabajo.

Para obtener más información sobre SharePoint, vea [Productos y tecnologías de Microsoft SharePoint](/sharepoint/dev/).

## <a name="workflows-in-sharepoint"></a>Flujos de trabajo en SharePoint
 Cuando se agrega un flujo de trabajo a una biblioteca o lista de SharePoint, se aplica un proceso empresarial en todos los elementos de la biblioteca o la lista. Un flujo de trabajo describe las acciones que el sistema o los usuarios deben realizar en cada elemento, como enviar el elemento para que se edite y después se revise. Estas acciones, conocidas como *actividades*, son los bloques de creación del flujo de trabajo.

 Puede crear flujos de trabajo de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e implementarlos en un sitio web de SharePoint. Una vez que se ha implementado un flujo de trabajo en SharePoint, se asocia a una biblioteca o lista. Después, lo puede iniciar un proceso (de forma automática) o un usuario (de forma manual). Para obtener más información sobre el funcionamiento de los flujos de trabajo, vea [Desarrollo de flujos de trabajo de SharePoint con Visual Studio](/sharepoint/dev/general-development/develop-sharepoint-workflows-using-visual-studio).

## <a name="create-custom-sharepoint-workflows"></a>Creación de flujos de trabajo de SharePoint personalizados
 Hay dos proyectos de flujo de trabajo de SharePoint disponibles en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]: **Flujo de trabajo secuencial** y **Flujo de trabajo de máquina de estados**.

 Un *flujo de trabajo secuencial* representa una serie de pasos. Los pasos se realizan uno tras otro hasta que se completa la última actividad. Los flujos de trabajo secuenciales siempre son estrictamente secuenciales en su ejecución. Como pueden recibir eventos externos e incluir flujos de lógica en paralelo, el orden de ejecución exacto puede variar. En la ilustración siguiente se muestra un ejemplo de un flujo de trabajo secuencial.

 ![Flujo de trabajo secuencial](../sharepoint/media/sp-sequential.png "Flujo de trabajo secuencial")

 Un *flujo de trabajo de máquina de estados* representa un conjunto de estados, transiciones y acciones. Los pasos de un flujo de trabajo de máquina de estados se ejecutan de forma asincrónica. Esto significa que no se realizan necesariamente uno tras otro, sino que se desencadenan mediante acciones y estados. Se asigna un estado como estado inicial y, después, en función de un evento, se realiza una transición a otro estado. La máquina de estados puede tener un estado final que determina el final del flujo de trabajo. En el diagrama siguiente se muestra un ejemplo de un flujo de trabajo de máquina de estados.

 ![Flujo de trabajo de equipo de estado](../sharepoint/media/sp-state.png "Flujo de trabajo de equipo de estado")

 Para obtener más información sobre los tipos de flujo de trabajo, vea [Tipos de flujo de trabajo](/previous-versions/office/developer/sharepoint-2010/ms468447(v=office.14)).

### <a name="use-the-wizard"></a>Uso del asistente
 Al crear un proyecto de flujo de trabajo de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], primero debe especificar su configuración en el **Asistente para la personalización de SharePoint**. El asistente usa estos valores para crear un proyecto en el **Explorador de soluciones**. Este proyecto contiene un archivo de código, varios archivos que se usan para implementar el flujo de trabajo y referencias a ensamblados que son necesarios para crear un flujo de trabajo de SharePoint personalizado.

 Después de crear el flujo de trabajo, puede ver y modificar sus propiedades en la ventana Propiedades. Aunque la mayoría de las propiedades de flujo de trabajo se pueden cambiar directamente en la ventana Propiedades, para algunas es necesario hacer clic en un botón de puntos suspensivos (![puntos suspensivos de ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "Elipse del Diseñador de ASP.NET Mobile")) para cambiar sus valores. Este botón reinicia el **Asistente para la personalización de SharePoint**. Una vez que haya cambiado el valor de propiedad, elija el botón **Finalizar** para finalizarlos.

> [!NOTE]
> La propiedad **Tipo de flujo de trabajo** es de solo lectura y no se puede cambiar. Si quiere cambiar el tipo de flujo de trabajo, debe crear otro flujo de trabajo.

## <a name="design-a-sharepoint-workflow"></a>Diseño de un flujo de trabajo de SharePoint
 Después de definir todos los pasos del proceso empresarial, use el diseñador de flujos de trabajo de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] para diseñar el flujo de trabajo de SharePoint. Para abrir el diseñador, haga doble clic en Workflow1.cs o Workflow1.vb en el **Explorador de soluciones**, o bien abra el menú contextual de cualquiera de esos archivos y, después, elija **Abrir**.

### <a name="activities"></a>Actividades
 Para diseñar un flujo de trabajo, agregue actividades desde el **Cuadro de herramientas** a una *programación de flujo de trabajo* en el diseñador. Una programación de flujo de trabajo contiene la secuencia de actividades en el orden en que se deben realizar.

 Existen dos tipos de actividades:

- Las *actividades simples* realizan una sola unidad de trabajo, como "retrasar durante 1 día" o "iniciar servicio web".

- Las *actividades compuestas* contienen otras actividades; por ejemplo, una actividad condicional podría contener dos ramas.

  Los dos tipos de actividades están disponibles en el **cuadro de herramientas**.

  Las actividades pueden tener propiedades, métodos y eventos. Use la ventana **Propiedades** para establecer las propiedades de una actividad.

  También puede crear una actividad personalizada. Para obtener más información, vea [Tutorial: Creación de una actividad de flujo de trabajo de sitio personalizada](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md).

  Las actividades se organizan en las siguientes pestañas del **cuadro de herramientas**:

- **Flujo de trabajo de SharePoint**

- **Windows Workflow v3.0**

- **Windows Workflow v3.5**

  SharePoint no admite todas las actividades de flujo de trabajo principales. Para obtener más información, vea [Información general sobre las actividades de flujo de trabajo para Windows SharePoint Services](/previous-versions/office/developer/sharepoint-2010/ms446847(v=office.14)).

#### <a name="sharepoint-workflow-activities"></a>Actividades de flujo de trabajo de SharePoint
 Las pestañas **Flujo de trabajo de SharePoint** contienen actividades especializadas para usarlas en [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]. Estas actividades simplifican y agilizan el desarrollo de flujos de trabajo del ciclo de vida de los documentos. Para obtener más información sobre las actividades enumeradas en la pestaña **Flujo de trabajo de SharePoint**, vea [Información general sobre las actividades de flujo de trabajo para Windows SharePoint Services](/previous-versions/office/developer/sharepoint-2010/ms446847(v=office.14)).

#### <a name="windows-workflow-activities"></a>Actividades de flujo de trabajo de Windows
 Las pestañas **Flujo de trabajo de Windows** contienen actividades proporcionadas por [!INCLUDE[TLA#tla_workflow](../sharepoint/includes/tlasharptla-workflow-md.md)]. Puede usar estas actividades para crear programaciones de flujo de trabajo para cualquier tipo de aplicación de flujo de trabajo de Windows.

 Para obtener más información sobre las actividades que aparecen en la pestaña **Flujos de trabajo de Windows**, vea [Actividades de Windows Workflow Foundation](/previous-versions/dotnet/netframework-3.5/ms733615(v=vs.90)). Para obtener más información sobre Windows Workflow Foundation, vea [Información general de Windows Workflow Foundation](/previous-versions/dotnet/netframework-3.5/ms734631(v=vs.90)).

### <a name="work-with-activities-in-the-designer"></a>Uso de actividades en el diseñador
 La programación de flujo de trabajo puede contener una combinación de actividades de Windows Workflow y de flujo de trabajo de SharePoint.

 El diseñador muestra indicaciones visuales para ayudarle a colocar y configurar las actividades de forma correcta. Al arrastrar o copiar una actividad en la programación de flujo de trabajo, el diseñador muestra iconos de signo más (+) de color verde que indican ubicaciones válidas para esa actividad en el flujo de trabajo. No se puede colocar una actividad en una ubicación donde no sea válida. Por ejemplo, no se puede colocar una actividad Enviar como la primera de una rama de actividad Escuchar. Para obtener más información, vea [Centro para desarrolladores de SharePoint Designer](https://developer.microsoft.com/office/docs).

## <a name="collect-information-during-the-workflow"></a>Recopilación de información durante el flujo de trabajo
 Es posible que quiera recopilar información de los usuarios en momentos predefinidos del flujo de trabajo. Puede recopilar información mediante formularios o propiedades de elementos.

### <a name="forms"></a>Formularios
 Los formularios son como cuadros de diálogo que contienen preguntas y proporcionan formas para que los usuarios proporcionen respuestas.

 Hay cuatro tipos de formularios que se pueden usar en un flujo de trabajo:

- Asociación

- Iniciación

- Modificación

- Tarea

  De estos, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] incluye plantillas de elemento para los formularios de asociación e iniciación. Un ejemplo de un *formulario de asociación* es el que permite al administrador que instala el flujo de trabajo especificar parámetros relacionados con el flujo de trabajo, como un límite de gasto para un flujo de trabajo de gastos. Un ejemplo de un *formulario de iniciación* es el que permite al usuario de un flujo de trabajo de gastos especificar la cantidad que invierte en el flujo de trabajo. Para obtener más información sobre estos tipos de formularios, vea [Plantillas de proyecto y de elementos de proyecto de SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).

### <a name="item-properties"></a>Propiedades de elementos
 También puede recopilar información de los usuarios mediante las propiedades de un elemento en la lista o biblioteca de SharePoint. El archivo de código principal (Workflow1.cs o Workflow1.vb) declara una instancia de la clase Microsoft.SharePoint.Workflow.SPWorkflowActivationProperties.WorkflowProperties denominada `workflowProperties`. Use el objeto `workflowProperties` para acceder a las propiedades de la biblioteca o lista en el código. Para obtener un ejemplo, vea [Tutorial: Creación y depuración de una solución de flujo de trabajo de SharePoint](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md).

## <a name="debug-a-sharepoint-workflow-template"></a>Depuración de una plantilla de flujo de trabajo de SharePoint
 Puede depurar un proyecto de flujo de trabajo de SharePoint igual que otros proyectos basados en web de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Al iniciar el depurador de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] usa la configuración que especifique en el **Asistente para la personalización de SharePoint** para abrir el sitio web de SharePoint adecuado y asociar automáticamente la plantilla de flujo de trabajo a la biblioteca o lista adecuada. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] también adjunta el depurador de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] al proceso de [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] denominado *w3wp.exe*.

 Para probar el flujo de trabajo, debe iniciarlo manualmente. Para obtener más información, vea la sección "Depuración de flujos de trabajo" en [Depuración de soluciones de SharePoint](../sharepoint/debugging-sharepoint-solutions.md). Para obtener más información sobre la depuración de aplicaciones web de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], vea [Depuración de aplicaciones web y script](../debugger/how-to-enable-debugging-for-aspnet-applications.md).

## <a name="deploy-a-sharepoint-workflow-template"></a>Implementación de una plantilla de flujo de trabajo de SharePoint
 Los proyectos de flujo de trabajo de SharePoint de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] se implementan como cualquier otro proyecto de SharePoint de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Para obtener más información, vea [Empaquetado e implementación de soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md).

## <a name="import-globally-reusable-workflows"></a>Importación de flujos de trabajo reutilizables globalmente
 Además de crear flujos de trabajo reutilizables específicos del sitio, SharePoint Designer permite crear *flujos de trabajo reutilizables globalmente*, que son los que se pueden usar en cualquier sitio de SharePoint. El proyecto Importar flujo de trabajo reutilizable de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] actualmente no importa flujos de trabajo reutilizables globalmente. Pero puede usar SharePoint Designer para convertir un flujo de trabajo reutilizable globalmente en un flujo de trabajo reutilizable, o bien importar el flujo de trabajo como un flujo de trabajo declarativo sin convertir. Para obtener más información, vea [Importación de elementos desde un sitio de SharePoint existente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

## <a name="related-topics"></a>Temas relacionados

|Title|Descripción|
|-----------|-----------------|
|[Tutorial: Creación y depuración de una solución de flujo de trabajo de SharePoint](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md)|Se le guía paso a paso por la creación y depuración de un flujo de trabajo de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] simple.|
|[Tutorial: Creación de un flujo de trabajo con formularios de asociación e iniciación](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)|Se le guía paso a paso por la creación de un flujo de trabajo de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] más completo con los formularios de asociación e iniciación.|
|[Tutorial: Adición de una página de aplicación a un flujo de trabajo](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)|Se basa en el tema [Tutorial: Creación de un flujo de trabajo con formularios de asociación e iniciación](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) mediante la adición de una página de aplicación *.aspx* adicional que notifica los datos introducidos en el flujo de trabajo.|
|[Tutorial: Creación de una actividad de flujo de trabajo de sitio personalizada](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md)|Se muestra cómo realizar dos tareas clave: crear un flujo de trabajo de nivel de sitio y crear una actividad de flujo de trabajo personalizada.|
|[Tutorial: Importación de un flujo de trabajo reutilizable de SharePoint Designer a Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)|Muestra cómo importar flujos de trabajo declarativos reutilizables creados en SharePoint Designer 2010 en un proyecto de SharePoint de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|

## <a name="see-also"></a>Consulte también

- [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Build and debug SharePoint solutions](../sharepoint/building-and-debugging-sharepoint-solutions.md) (Compilar y depurar las soluciones de SharePoint)
- [Creación de páginas de aplicación para SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)