---
title: "Formulario de soporte técnico en flujos de trabajo | Documentos de Microsoft"
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
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
ms.assetid: 1706f6a2-ea84-4234-85ae-19feb8540507
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e2c63af83c6ca8249e87d60f23043c0639c7fd43
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="form-support-in-workflows"></a>Compatibilidad con formularios en los flujos de trabajo
  Cuatro tipos de formularios se pueden usar en un flujo de trabajo: asociación, la iniciación, tarea y modificación. Estos tipos de formulario pueden basarse en un formulario ASPX o un formulario de InfoPath. El nivel de compatibilidad que [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] proporciona para una forma determinada depende de varios factores, que se describen en las tablas siguientes. Para obtener más información sobre los tipos de formulario de flujo de trabajo, consulte [información general de formularios de flujo de trabajo](http://go.microsoft.com/fwlink/?LinkId=185228) en el sitio Web de MSDN.  
  
## <a name="xml-refactoring"></a>Refactorización de XML  
 Al agregar un formulario de inicio ni la asociación de ASPX para un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] elemento de proyecto de flujo de trabajo, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] automáticamente refactoriza el código XML en el archivo Elements.xml del flujo de trabajo para mantener el atributo que hace referencia a la asociación o iniciación forman sincronizada Cuando se actualice la ruta de acceso de implementación o el nombre de formato o se elimina el formulario. Sin embargo, cuando se utilizan otros tipos de formulario en un flujo de trabajo, como un formulario de tareas o modificación, no se refactoriza el archivo Elements.xml.  
  
## <a name="form-support-in-new-visual-studio-workflows"></a>Compatibilidad con formularios en nuevos flujos de trabajo de Visual Studio  
 La siguiente tabla se recogen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] compatibilidad para tipos de forma diferente en los formularios ASPX o InfoPath en flujos de trabajo que se crean en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
|Tipo de formulario|Flujo de trabajo creado en Visual Studio con un formulario de ASPX|Flujo de trabajo creado en Visual Studio mediante el uso de un formulario de InfoPath|  
|---------------|---------------------------------------------------------|-----------------------------------------------------------------|  
|Asociación|-Un formulario de asociación de ASPX se puede agregar al flujo de trabajo mediante el **formulario de asociación de flujo de trabajo** plantilla de elemento.<br />-El archivo Elements.xml del flujo de trabajo se refactoriza cuando el formulario se agrega, cambia el nombre o eliminado, o cuando cambia su ruta de acceso de implementación.<br />-Para obtener más información, consulte [Tutorial: crear un flujo de trabajo con una asociación y formularios de iniciación](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-No hay ninguna plantilla de formulario de InfoPath asociación en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-No hay ninguna integración entre [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] y el Diseñador de InfoPath.<br />-No se ha refactorizado el archivo Elements.xml del flujo de trabajo.|  
|Inicio|-Un formulario de inicio de ASPX se puede agregar al flujo de trabajo mediante el **formulario de iniciación de flujo de trabajo** plantilla de elemento.<br />-El archivo Elements.xml del flujo de trabajo se refactoriza cuando el formulario se agrega, cambia el nombre o eliminado, o cuando cambia su ruta de acceso de implementación.<br />-Para obtener más información, consulte [Tutorial: crear un flujo de trabajo con una asociación y formularios de iniciación](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-No hay ninguna plantilla de formulario de InfoPath asociación en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-No hay ninguna integración entre [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] y el Diseñador de InfoPath.<br />-No se ha refactorizado el archivo Elements.xml del flujo de trabajo.|  
|Tarea|-Ninguna plantilla de formulario de tareas ASPX está disponible en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Debe crear una página de aplicación y agregue código a él.<br />-No se ha refactorizado el archivo Elements.xml del flujo de trabajo.<br />-Para obtener más información, vea [formularios de tareas de flujo de trabajo (SharePoint Foundation)](http://go.microsoft.com/fwlink/?LinkId=187674)|-No hay ninguna plantilla de formulario de tareas de InfoPath en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-No hay ninguna integración entre [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] y el Diseñador de InfoPath.<br />-No se ha refactorizado el archivo Elements.xml del flujo de trabajo.|  
|Modificación|-Ninguna plantilla de formulario de modificación de ASPX está disponible en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Para agregar un formulario de modificación, debe crear una página de aplicación y agregue código a él.<br />-No se ha refactorizado el archivo Elements.xml del flujo de trabajo. Se debe editar manualmente según corresponda.<br />-Para obtener más información, vea [formularios de modificación de flujo de trabajo (SharePoint Foundation)](http://go.microsoft.com/fwlink/?LinkId=187675)|-No hay ninguna plantilla de formulario de InfoPath modificación en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-No hay ninguna integración entre [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] y el Diseñador de InfoPath.<br />-No se ha refactorizado el archivo Elements.xml del flujo de trabajo.|  
  
## <a name="form-support-in-imported-sharepoint-reusable-workflows"></a>Compatibilidad con formularios en los flujos de trabajo reutilizable de SharePoint importados  
 La siguiente tabla se recogen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] compatibilidad para tipos de forma diferente en los formularios ASPX o InfoPath en SharePoint flujos de trabajo reutilizables que se importan en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
|Tipo de formulario|Flujo de trabajo reutilizable que tiene un formulario ASPX importado desde SharePoint Designer|Flujo de trabajo reutilizable que tiene un formulario de InfoPath que se importan desde SharePoint Designer|  
|---------------|-------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|Asociación|-El formulario se hace referencia en el archivo Elements.xml del flujo de trabajo.<br />-El archivo Elements.xml del flujo de trabajo se refactoriza cuando el formulario se cambia el nombre o eliminado, o cuando cambia su ruta de acceso de implementación.|-El formulario se importa, pero no hace referencia en el Elements.xml del flujo de trabajo.<br />-No se ha refactorizado el archivo Elements.xml del flujo de trabajo.|  
|Inicio|-El formulario se hace referencia el flujo de trabajo en el archivo Elements.xml del flujo de trabajo.<br />-El archivo Elements.xml del flujo de trabajo se refactoriza cuando el formulario se cambia el nombre o eliminado, o cuando cambia su ruta de acceso de implementación.|-El formulario se importa, pero no hace referencia en el Elements.xml del flujo de trabajo.<br />-No se ha refactorizado el archivo Elements.xml del flujo de trabajo. **Nota:** reglas y propiedades deben agregarse y cambiadas para que este escenario funcione.|  
|Tarea|-El formulario se hace referencia en el archivo Elements.xml del flujo de trabajo.<br />-No se ha refactorizado el archivo Elements.xml del flujo de trabajo.|-El formulario se importa, pero no hace referencia en el Elements.xml del flujo de trabajo.<br />-No se ha refactorizado el archivo Elements.xml del flujo de trabajo. **Nota:** reglas y propiedades deben agregarse y cambiadas para que este escenario funcione.|  
|Modificación|No es aplicable. No se puede crear formularios de modificación de ASPX en SharePoint Designer.|No es aplicable. No se puede crear formularios de modificación de InfoPath en SharePoint Designer, excepto para el flujo de trabajo de servidor de SharePoint integrado, que no se incluye en el archivo .wsp cuando se exporta el flujo de trabajo.|  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: Crear un flujo de trabajo con una asociación y formularios de iniciación](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)   
 [Crear soluciones de flujo de trabajo de SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [Importar elementos de un sitio de SharePoint existente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)  
  
  