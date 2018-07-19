---
title: Formulario de soporte técnico en flujos de trabajo | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9b3a07f56819818e55548292f3dbcdc1095d9f00
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/22/2018
ms.locfileid: "36326085"
---
# <a name="form-support-in-workflows"></a>Compatibilidad con formularios en los flujos de trabajo
  Se pueden usar los cuatro tipos de formularios en un flujo de trabajo: asociación, iniciación, modificación y tarea. Estos tipos de formulario pueden basarse en un formulario ASPX o un formulario de InfoPath. El nivel de compatibilidad que [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] proporciona de forma particular depende de varios factores, que se describen en las tablas siguientes. Para obtener más información sobre los tipos de formulario de flujo de trabajo, consulte [formularios de flujo de trabajo información general sobre](http://go.microsoft.com/fwlink/?LinkId=185228) en el sitio Web de MSDN.  
  
## <a name="xml-refactoring"></a>Refactorización de XML
 Al agregar un formulario de asociación o iniciación de ASPX para un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] elemento de proyecto de flujo de trabajo, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] automáticamente refactoriza el código XML en el flujo de trabajo *Elements.xml* archivo para mantener el atributo que hace referencia a la asociación o se elimina el formulario de iniciación en sincronización cada vez que se actualiza la ruta de acceso de implementación o el nombre de formulario o el formulario. Sin embargo, cuando usa otros tipos de formulario en un flujo de trabajo, como un formulario de tareas o modificación, el *Elements.xml* no se refactoriza el archivo.  
  
## <a name="form-support-in-new-visual-studio-workflows"></a>Compatibilidad con formularios en nuevos flujos de trabajo de Visual Studio
 La siguiente tabla enumera [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] compatibilidad con tipos de forma diferente en los formularios de ASPX o InfoPath en flujos de trabajo que se crean en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
|Tipo de formulario|Flujo de trabajo creado en Visual Studio con un formulario de ASPX|Flujo de trabajo creado en Visual Studio mediante el uso de un formulario de InfoPath|  
|---------------|---------------------------------------------------------|-----------------------------------------------------------------|  
|Asociación|-Un formulario de asociación de ASPX se puede agregar al flujo de trabajo mediante el uso de la **formulario de asociación de flujo de trabajo** plantilla de elemento.<br />-El *Elements.xml* archivo del flujo de trabajo se refactoriza cuando el formulario se agrega, cambia el nombre o eliminado, o cuando cambia su ruta de acceso de implementación.<br />-Para obtener más información, consulte [Tutorial: crear un flujo de trabajo con la asociación y formularios de iniciación](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-No hay ninguna plantilla de formulario de asociación de InfoPath en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-No hay ninguna integración entre [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] y Diseñador de InfoPath.<br />-El *Elements.xml* no se refactoriza el archivo del flujo de trabajo.|  
|Iniciación|-Un formulario de iniciación de ASPX se puede agregar al flujo de trabajo mediante el uso de la **formulario de iniciación de flujo de trabajo** plantilla de elemento.<br />-El *Elements.xml* archivo del flujo de trabajo se refactoriza cuando el formulario se agrega, cambia el nombre o eliminado, o cuando cambia su ruta de acceso de implementación.<br />-Para obtener más información, consulte [Tutorial: crear un flujo de trabajo con la asociación y formularios de iniciación](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-No hay ninguna plantilla de formulario de asociación de InfoPath en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-No hay ninguna integración entre [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] y Diseñador de InfoPath.<br />-El *Elements.xml* no se refactoriza el archivo del flujo de trabajo.|  
|Tarea|-Ninguna plantilla de formulario ASPX tarea está disponible en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Debe crear una página de aplicación y agregarle código.<br />-El *Elements.xml* no se refactoriza el archivo del flujo de trabajo.<br />-Para obtener más información, consulte [formularios de tareas de flujo de trabajo (SharePoint Foundation)](http://go.microsoft.com/fwlink/?LinkId=187674)|-No hay ninguna plantilla de formulario de tareas de InfoPath en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-No hay ninguna integración entre [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] y Diseñador de InfoPath.<br />-El *Elements.xml* no se refactoriza el archivo del flujo de trabajo.|  
|Modificación|-No hay ninguna plantilla de formulario ASPX modificación está disponible en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Para agregar un formulario de modificación, debe crear una página de aplicación y agregarle código.<br />-El *Elements.xml* no se refactoriza el archivo del flujo de trabajo. Se debe editar manualmente según corresponda.<br />-Para obtener más información, consulte [formularios de modificación de flujo de trabajo (SharePoint Foundation)](http://go.microsoft.com/fwlink/?LinkId=187675)|-No hay ninguna plantilla de formulario de InfoPath modificación en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-No hay ninguna integración entre [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] y Diseñador de InfoPath.<br />-El *Elements.xml* no se refactoriza el archivo del flujo de trabajo.|  
  
## <a name="form-support-in-imported-sharepoint-reusable-workflows"></a>Compatibilidad con formularios en importados flujos de trabajo reutilizables de SharePoint
 La siguiente tabla enumera [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] compatibilidad con tipos de forma diferente en los formularios de ASPX o InfoPath en SharePoint flujos de trabajo reutilizables que se importan en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
|Tipo de formulario|Flujo de trabajo reutilizable que tiene un formulario ASPX importado de SharePoint Designer|Flujo de trabajo reutilizable que tiene un formulario de InfoPath importado de SharePoint Designer|  
|---------------|-------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|Asociación|-El formulario se hace referencia en el *Elements.xml* archivo del flujo de trabajo.<br />-El *Elements.xml* archivo del flujo de trabajo se refactoriza cuando el formulario se cambia el nombre o eliminado, o cuando cambia su ruta de acceso de implementación.|-El formulario se importa, pero no hace referencia en el *Elements.xml* del flujo de trabajo.<br />-El *Elements.xml* no se refactoriza el archivo del flujo de trabajo.|  
|Iniciación|-El formulario se hace referencia el flujo de trabajo en el *Elements.xml* archivo del flujo de trabajo.<br />-El *Elements.xml* archivo del flujo de trabajo se refactoriza cuando el formulario se cambia el nombre o eliminado, o cuando cambia su ruta de acceso de implementación.|-El formulario se importa, pero no hace referencia en el *Elements.xml* del flujo de trabajo.<br />-El *Elements.xml* no se refactoriza el archivo del flujo de trabajo. **Nota:** propiedades y reglas deben se agregan y cambian para que este escenario funcione.|  
|Tarea|-El formulario se hace referencia en el *Elements.xml* archivo del flujo de trabajo.<br />-El *Elements.xml* no se refactoriza el archivo del flujo de trabajo.|-El formulario se importa, pero no hace referencia en el *Elements.xml* del flujo de trabajo.<br />-El *Elements.xml* no se refactoriza el archivo del flujo de trabajo. **Nota:** propiedades y reglas deben se agregan y cambian para que este escenario funcione.|  
|Modificación|No es aplicable. No se puede crear formularios de modificación de ASPX en SharePoint Designer.|No es aplicable. No se puede crear formularios de modificación de InfoPath en SharePoint Designer, excepto para el flujo de trabajo de servidor de SharePoint integrada, que no se incluye en el archivo .wsp cuando se exporta el flujo de trabajo.|  
  
## <a name="see-also"></a>Vea también
 [Tutorial: Crear un flujo de trabajo con formularios de asociación e iniciación](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)   
 [Crear soluciones de flujo de trabajo de SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [Importar elementos de un sitio de SharePoint existente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)  
  
  
