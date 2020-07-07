---
title: Crear soluciones de flujo de trabajo de SharePoint | Microsoft Docs
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
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015280"
---
# <a name="create-sharepoint-workflow-solutions"></a>Crear soluciones de flujo de trabajo de SharePoint

[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]proporciona herramientas para ayudarle a crear flujos de trabajo personalizados que administran el ciclo de vida de los documentos y los elementos de lista de un sitio web de SharePoint. Entre los elementos proporcionados se incluyen un diseñador, un conjunto de controles de actividad y las referencias de ensamblado necesarias. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]también incluye el **Asistente para la personalización de SharePoint**, que le ayudará a crear y configurar los flujos de trabajo.

Para obtener más información acerca de SharePoint, vea [productos y tecnologías de Microsoft SharePoint](/sharepoint/dev/).

## <a name="workflows-in-sharepoint"></a>Flujos de trabajo en SharePoint
 Cuando se agrega un flujo de trabajo a una biblioteca o lista de SharePoint, se aplica un proceso empresarial en todos los elementos de la biblioteca o la lista. Un flujo de trabajo describe las acciones que el sistema o los usuarios deben realizar en cada elemento, como enviar el elemento que se va a editar y revisar. Estas acciones, conocidas como *actividades*, son los bloques de creación del flujo de trabajo.

 Puede crear flujos de trabajo de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e implementarlos en un sitio web de SharePoint. Una vez implementado un flujo de trabajo en SharePoint, se asocia a una biblioteca o lista. Un usuario puede iniciarlo automáticamente, por un proceso o manualmente. Para obtener más información sobre la operación de flujo de trabajo, consulte [desarrollo de flujos de trabajo de SharePoint con Visual Studio](/sharepoint/dev/general-development/develop-sharepoint-workflows-using-visual-studio).

## <a name="create-custom-sharepoint-workflows"></a>Crear flujos de trabajo de SharePoint personalizados
 Hay dos proyectos de flujo de trabajo de SharePoint disponibles en: flujo de trabajo [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **secuencial** y **flujo de trabajo de equipo de estado**.

 Un *flujo de trabajo secuencial* representa una serie de pasos. Los pasos se realizan uno tras otro hasta que se completa la última actividad. Los flujos de trabajo secuenciales siempre son estrictamente secuenciales en su ejecución. Dado que pueden recibir eventos externos e incluir flujos de lógica en paralelo, el orden exacto de ejecución puede variar. En la ilustración siguiente se muestra un ejemplo de un flujo de trabajo secuencial.

 ![Flujo de trabajo secuencial](../sharepoint/media/sp-sequential.png "Flujo de trabajo secuencial")

 Un *flujo de trabajo de equipo de estado* representa un conjunto de Estados, transiciones y acciones. Los pasos de un flujo de trabajo de equipo de estado se ejecutan de forma asincrónica. Esto significa que no se realizan necesariamente uno después de otro, sino que se desencadenan por acciones y Estados. Se asigna un estado como estado inicial y, a continuación, en función de un evento, se realiza una transición a otro Estado. El equipo de estado puede tener un estado final que determina el final del flujo de trabajo. En el diagrama siguiente se muestra un ejemplo de un flujo de trabajo de equipo de estado.

 ![Flujo de trabajo de equipo de estado](../sharepoint/media/sp-state.png "Flujo de trabajo de equipo de estado")

 Para obtener más información sobre los tipos de flujo de trabajo, consulte [tipos de flujo de trabajo](/previous-versions/office/developer/sharepoint-2010/ms468447(v=office.14)).

### <a name="use-the-wizard"></a>Usar el asistente
 Cuando se crea un proyecto de flujo de trabajo de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , primero se especifica su configuración en el **Asistente para la personalización de SharePoint**. El asistente utiliza estos valores para crear un proyecto en **Explorador de soluciones**. Este proyecto contiene un archivo de código, varios archivos que se usan para implementar el flujo de trabajo y referencias a ensamblados que son necesarios para crear un flujo de trabajo de SharePoint personalizado.

 Después de crear el flujo de trabajo, puede modificar sus propiedades en el ventana Propiedades. Aunque la mayoría de las propiedades de flujo de trabajo se pueden cambiar directamente en el ventana Propiedades, algunas requieren que haga clic en un botón de puntos suspensivos (![ASP.NET Mobile Designer Ellipse](../sharepoint/media/mwellipsis.gif "Elipse del Diseñador de ASP.NET Mobile")) para cambiar sus valores. Este botón reinicia el **Asistente para la personalización de SharePoint**. Una vez que haya realizado los cambios en el valor de la propiedad, elija el botón **Finalizar** para finalizarlos.

> [!NOTE]
> La propiedad de **tipo de flujo de trabajo** es de solo lectura y no se puede cambiar. Si desea cambiar el tipo de flujo de trabajo, debe crear otro flujo de trabajo.

## <a name="design-a-sharepoint-workflow"></a>Diseñar un flujo de trabajo de SharePoint
 Después de definir todos los pasos del proceso empresarial, use el [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Diseñador de flujo de trabajo para diseñar el flujo de trabajo de SharePoint. Para abrir el diseñador, haga doble clic en Workflow1.cs o Workflow1. VB en **Explorador de soluciones**, o abra el menú contextual de cualquiera de esos archivos y, a continuación, elija **abrir**.

### <a name="activities"></a>Actividades
 Para diseñar un flujo de trabajo, agregue actividades desde el **cuadro de herramientas** a una programación de *flujo de trabajo* en el diseñador. Una programación de flujo de trabajo contiene la secuencia de actividades en el orden en que se deben realizar.

 Existen dos tipos de actividades:

- *Las actividades simples* realizan una sola unidad de trabajo, como "retraso durante 1 día" o "iniciar servicio Web".

- *Las actividades compuestas* contienen otras actividades; por ejemplo, una actividad condicional podría contener dos bifurcaciones.

  Ambos tipos de actividades están disponibles en el **cuadro de herramientas**.

  Las actividades pueden tener propiedades, métodos y eventos. Use la ventana **propiedades** para establecer las propiedades de una actividad.

  También puede crear una actividad personalizada. Para obtener más información, consulte [Tutorial: crear una actividad de flujo de trabajo de sitio personalizada](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md).

  Las actividades se organizan en las siguientes pestañas del **cuadro de herramientas**:

- **Flujo de trabajo de SharePoint**

- **Windows Workflow v 3.0**

- **Windows Workflow v 3.5**

  SharePoint no admite todas las actividades de flujo de trabajo principales. Para obtener más información, vea [información general sobre las actividades de flujo de trabajo para Windows SharePoint Services](/previous-versions/office/developer/sharepoint-2010/ms446847(v=office.14)).

#### <a name="sharepoint-workflow-activities"></a>Actividades de flujo de trabajo de SharePoint
 Las pestañas de **flujo de trabajo de SharePoint** contienen actividades especializadas para su uso en [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] . Estas actividades simplifican y agilizan el desarrollo de flujos de trabajo del ciclo de vida de los documentos. Para obtener más información acerca de las actividades que aparecen en la pestaña **flujo de trabajo de SharePoint** , consulte [información general sobre actividades de flujo de trabajo para Windows SharePoint Services](/previous-versions/office/developer/sharepoint-2010/ms446847(v=office.14)).

#### <a name="windows-workflow-activities"></a>Actividades de flujo de trabajo de Windows
 Las pestañas de **flujo de trabajo de Windows** contienen actividades proporcionadas por [!INCLUDE[TLA#tla_workflow](../sharepoint/includes/tlasharptla-workflow-md.md)] . Puede usar estas actividades para crear programaciones de flujo de trabajo para cualquier tipo de aplicación de Windows Workflow.

 Para obtener más información sobre las actividades que aparecen en la pestaña **flujos de trabajo de Windows** , vea [Windows Workflow Foundation actividades](/previous-versions/dotnet/netframework-3.5/ms733615(v=vs.90)). Para obtener más información sobre el Windows Workflow Foundation, consulte [información general sobre Windows Workflow Foundation](/previous-versions/dotnet/netframework-3.5/ms734631(v=vs.90)).

### <a name="work-with-activities-in-the-designer"></a>Trabajar con actividades en el diseñador
 La programación de flujo de trabajo puede contener una combinación de actividades de flujo de trabajo de Windows y actividades de flujo de trabajo de SharePoint.

 El diseñador muestra indicaciones visuales para ayudarle a colocar y configurar las actividades correctamente. Al arrastrar o copiar una actividad en la programación de flujo de trabajo, el diseñador muestra iconos de signo más (+) verdes que muestran ubicaciones válidas para esa actividad en el flujo de trabajo. No se puede colocar una actividad en una ubicación donde no sea válida. Por ejemplo, no se puede colocar una actividad de envío como la primera actividad en una bifurcación de actividad de escucha. Para obtener más información, vea [Centro para desarrolladores de SharePoint Designer](https://developer.microsoft.com/office/docs).

## <a name="collect-information-during-the-workflow"></a>Recopilar información durante el flujo de trabajo
 Es posible que desee recopilar información de los usuarios en momentos predefinidos en el flujo de trabajo. Puede recopilar información mediante las propiedades de los formularios o los elementos.

### <a name="forms"></a>Formularios
 Los formularios son como los cuadros de diálogo que contienen preguntas y proporcionan formas para que los usuarios proporcionen respuestas.

 Hay cuatro tipos de formularios que se pueden usar en un flujo de trabajo:

- Asociación

- Comienzo

- Modificación

- Tarea

  Entre ellas, se [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] incluyen las plantillas de elementos para los formularios de asociación e inicio. Un ejemplo de un *formulario de asociación* es uno que permite al administrador instalar el flujo de trabajo especificar parámetros relacionados con el flujo de trabajo, como un límite de gasto para un flujo de trabajo de gastos. Un ejemplo de un *formulario de inicio* es el que permite al usuario de un flujo de trabajo de gastos especificar la cantidad que invierte en el flujo de trabajo. Para obtener más información sobre estos tipos de formularios, vea [plantillas de proyecto y de elemento de proyecto de SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).

### <a name="item-properties"></a>Propiedades del elemento
 También puede recopilar información de los usuarios mediante las propiedades de un elemento en la lista o biblioteca de SharePoint. El archivo de código principal (Workflow1.cs o Workflow1. VB) declara una instancia de la clase Microsoft. SharePoint. Workflow. SPWorkflowActivationProperties. WorkflowProperties denominada `workflowProperties` . Use el `workflowProperties` objeto para tener acceso a las propiedades de la biblioteca o lista en el código. Para obtener un ejemplo, vea [Tutorial: crear y depurar una solución de flujo de trabajo de SharePoint](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md).

## <a name="debug-a-sharepoint-workflow-template"></a>Depurar una plantilla de flujo de trabajo de SharePoint
 Puede depurar un proyecto de flujo de trabajo de SharePoint del mismo modo que depura otros [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] proyectos basados en Web. Al iniciar el [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] depurador, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] usa la configuración que especifique en el Asistente para la **Personalización de SharePoint** para abrir el sitio web de SharePoint adecuado y asociar automáticamente la plantilla de flujo de trabajo a la biblioteca o lista adecuada. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]también asocia el [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] depurador al [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] proceso denominado *w3wp.exe*.

 Para probar el flujo de trabajo, debe iniciarlo manualmente. Para obtener más información, vea la sección sobre depuración de flujos de trabajo en [depurar soluciones de SharePoint](../sharepoint/debugging-sharepoint-solutions.md). Para obtener más información sobre la [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] depuración de aplicaciones Web, vea [depurar aplicaciones y scripts web](../debugger/how-to-enable-debugging-for-aspnet-applications.md).

## <a name="deploy-a-sharepoint-workflow-template"></a>Implementar una plantilla de flujo de trabajo de SharePoint
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Los proyectos de flujo de trabajo de SharePoint se implementan igual que otros [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] proyectos de SharePoint. Para obtener más información, vea [empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md).

## <a name="import-globally-reusable-workflows"></a>Importar flujos de trabajo reutilizables globalmente
 Además de crear flujos de trabajo reutilizables específicos del sitio, SharePoint Designer le permite crear *flujos de trabajo reutilizables globalmente*, que son flujos de trabajo que se pueden usar en cualquier sitio de SharePoint. El proyecto importar flujo de trabajo reutilizable de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] actualmente no importa flujos de trabajo reutilizables globalmente. Sin embargo, puede usar SharePoint Designer para convertir un flujo de trabajo reutilizable globalmente en un flujo de trabajo reutilizable o importar el flujo de trabajo como un flujo de trabajo declarativo sin convertir. Para obtener más información, vea [importar elementos de un sitio de SharePoint existente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

## <a name="related-topics"></a>Temas relacionados

|Title|Descripción|
|-----------|-----------------|
|[Tutorial: crear y depurar una solución de flujo de trabajo de SharePoint](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md)|Conduce paso a paso a través de la creación y depuración de un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] flujo de trabajo simple.|
|[Tutorial: creación de un flujo de trabajo con formularios de asociación e iniciación](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)|Conduce paso a paso a la creación de un flujo de trabajo más completo [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] con los formularios de asociación e iniciación.|
|[Tutorial: agregar una página de aplicación a un flujo de trabajo](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)|Se basa en el tema [Tutorial: crear un flujo de trabajo con formularios de asociación e iniciación](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) agregando una página de aplicación *. aspx* adicional que informa de los datos introducidos en el flujo de trabajo.|
|[Tutorial: crear una actividad de flujo de trabajo de sitio personalizada](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md)|Muestra cómo realizar dos tareas clave: crear un flujo de trabajo de nivel de sitio y crear una actividad de flujo de trabajo personalizada.|
|[Tutorial: importar un flujo de trabajo reutilizable de SharePoint Designer en Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)|Muestra cómo importar flujos de trabajo declarativos reutilizables creados en SharePoint Designer 2010 en un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] proyecto de SharePoint.|

## <a name="see-also"></a>Consulte también

- [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Build and debug SharePoint solutions](../sharepoint/building-and-debugging-sharepoint-solutions.md) (Compilar y depurar las soluciones de SharePoint)
- [Crear páginas de aplicación para SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)