---
title: Compatibilidad con formularios en los flujos de trabajo | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
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
ms.openlocfilehash: b064df6729b914af7758cde86b03b886fd0e5d26
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72986260"
---
# <a name="form-support-in-workflows"></a>Compatibilidad con formularios en los flujos de trabajo
  En un flujo de trabajo se pueden usar cuatro tipos de formularios: Asociación, Inicio, tarea y modificación. Estos tipos de formulario se pueden basar en un formulario ASPX o en un formulario de InfoPath. El nivel de compatibilidad que [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] proporciona para un determinado formulario depende de varios factores, que se describen en las tablas siguientes. Para obtener más información sobre los tipos de formulario de flujo de trabajo, consulte [información general sobre formularios de flujo de trabajo](/previous-versions/office/developer/sharepoint-2010/ms457061(v=office.14)).

## <a name="xml-refactoring"></a>Refactorización XML
 Al agregar una asociación ASPX o un formulario de inicio a un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] elemento de proyecto de flujo de trabajo, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] refactoriza automáticamente el XML en el archivo de *Elements.xml* del flujo de trabajo para mantener el atributo que hace referencia al formulario de asociación o de inicio en sincronización siempre que el nombre del formulario o la ruta de acceso de la implementación se actualice o se elimine el formulario. Sin embargo, cuando se usan otros tipos de formulario en un flujo de trabajo, como una tarea o un formulario de modificación, el archivo *Elements.xml* no se refactoriza.

## <a name="form-support-in-new-visual-studio-workflows"></a>Compatibilidad con formularios en nuevos flujos de trabajo de Visual Studio
 En la tabla siguiente [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] se muestra la compatibilidad con los distintos tipos de formulario en los formularios aspx o InfoPath de los flujos de trabajo que se crean en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

|Tipo de formulario|Flujo de trabajo creado en Visual Studio con un formulario ASPX|Flujo de trabajo creado en Visual Studio mediante un formulario de InfoPath|
|---------------|---------------------------------------------------------|-----------------------------------------------------------------|
|Asociación|-Se puede Agregar un formulario de asociación ASPX al flujo de trabajo mediante la plantilla de elemento de **formulario de Asociación de flujo de trabajo** .<br />-El archivo de *Elements.xml* del flujo de trabajo se refactoriza al agregar, cambiar de nombre o eliminar el formulario, o cuando cambia la ruta de implementación.<br />-Para obtener más información, vea [Tutorial: crear un flujo de trabajo con formularios de asociación e iniciación](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-No hay ninguna plantilla de formulario de Asociación de InfoPath en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .<br />-No hay ninguna integración entre [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] y el diseñador de InfoPath.<br />-El archivo de *Elements.xml* del flujo de trabajo no se refactoriza.|
|Comienzo|-Se puede Agregar un formulario de inicio de ASPX al flujo de trabajo mediante la plantilla de elemento **formulario de inicio de flujo de trabajo** .<br />-El archivo de *Elements.xml* del flujo de trabajo se refactoriza al agregar, cambiar de nombre o eliminar el formulario, o cuando cambia la ruta de implementación.<br />-Para obtener más información, vea [Tutorial: crear un flujo de trabajo con formularios de asociación e iniciación](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-No hay ninguna plantilla de formulario de Asociación de InfoPath en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .<br />-No hay ninguna integración entre [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] y el diseñador de InfoPath.<br />-El archivo de *Elements.xml* del flujo de trabajo no se refactoriza.|
|Tarea|-No hay ninguna plantilla de formulario de tarea ASPX disponible en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Debe crear una página de aplicación y agregarle código.<br />-El archivo de *Elements.xml* del flujo de trabajo no se refactoriza.<br />-Para obtener más información, vea [formularios de tareas de flujo de trabajo (SharePoint Foundation)](/previous-versions/office/developer/sharepoint-2010/ms438856(v=office.14))|-No hay ninguna plantilla de formulario de tarea de InfoPath en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .<br />-No hay ninguna integración entre [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] y el diseñador de InfoPath.<br />-El archivo de *Elements.xml* del flujo de trabajo no se refactoriza.|
|Modificación|-No hay ninguna plantilla de formulario de modificación de ASPX disponible en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Para agregar un formulario de modificación, debe crear una página de aplicación y agregarle código.<br />-El archivo de *Elements.xml* del flujo de trabajo no se refactoriza. Debe editarlo manualmente según corresponda.<br />-Para obtener más información, vea [formularios de modificación de flujo de trabajo (SharePoint Foundation)](/previous-versions/office/developer/sharepoint-2010/ms480794(v=office.14))|-No hay ninguna plantilla de formulario de modificación de InfoPath en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .<br />-No hay ninguna integración entre [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] y el diseñador de InfoPath.<br />-El archivo de *Elements.xml* del flujo de trabajo no se refactoriza.|

## <a name="form-support-in-imported-sharepoint-reusable-workflows"></a>Compatibilidad con formularios en flujos de trabajo reutilizables de SharePoint importados
 En la tabla siguiente [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] se muestra la compatibilidad con distintos tipos de formulario en formularios aspx o InfoPath en flujos de trabajo reutilizables de SharePoint que se importan en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

|Tipo de formulario|Flujo de trabajo reutilizable que tiene un formulario ASPX importado desde SharePoint Designer|Flujo de trabajo reutilizable que tiene un formulario de InfoPath importado desde SharePoint Designer|
|---------------|-------------------------------------------------------------------------------| - |
|Asociación|-Se hace referencia al formulario en el archivo *Elements.xml* del flujo de trabajo.<br />-El archivo de *Elements.xml* del flujo de trabajo se refactoriza cuando se cambia el nombre del formulario o se elimina, o cuando cambia la ruta de implementación.|-El formulario se importa, pero no se hace referencia a él en el *Elements.xml* del flujo de trabajo.<br />-El archivo de *Elements.xml* del flujo de trabajo no se refactoriza.|
|Comienzo|-El flujo de trabajo hace referencia al formulario en el archivo *Elements.xml* del flujo de trabajo.<br />-El archivo de *Elements.xml* del flujo de trabajo se refactoriza cuando se cambia el nombre del formulario o se elimina, o cuando cambia la ruta de implementación.|-El formulario se importa, pero no se hace referencia a él en el *Elements.xml* del flujo de trabajo.<br />-El archivo de *Elements.xml* del flujo de trabajo no se refactoriza. **Nota:**  Las reglas y propiedades deben agregarse y modificarse para que este escenario funcione.|
|Tarea|-Se hace referencia al formulario en el archivo *Elements.xml* del flujo de trabajo.<br />-El archivo de *Elements.xml* del flujo de trabajo no se refactoriza.|-El formulario se importa, pero no se hace referencia a él en el *Elements.xml* del flujo de trabajo.<br />-El archivo de *Elements.xml* del flujo de trabajo no se refactoriza. **Nota:**  Las reglas y propiedades deben agregarse y modificarse para que este escenario funcione.|
|Modificación|No aplicable. Los formularios de modificación de ASPX no se pueden crear en SharePoint Designer.|No aplicable. Los formularios de modificación de InfoPath no se pueden crear en SharePoint Designer, salvo el flujo de trabajo de SharePoint Server integrado, que no se incluye en el archivo. wsp cuando se exporta el flujo de trabajo.|

## <a name="see-also"></a>Vea también
- [Tutorial: creación de un flujo de trabajo con formularios de asociación e iniciación](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)
- [Crear soluciones de flujo de trabajo de SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [Importar elementos de un sitio de SharePoint existente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
