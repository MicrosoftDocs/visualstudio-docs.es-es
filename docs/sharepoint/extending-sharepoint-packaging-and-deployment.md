---
title: "Extender SharePoint empaquetado e implementación | Documentos de Microsoft"
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
helpviewer_keywords: SharePoint development in Visual Studio, extending deployment
ms.assetid: 4789ebb2-12bc-42b9-9427-e63d77137765
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: d2239a73b5a6f35a3571af90f8bd2814150da9d9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="extending-sharepoint-packaging-and-deployment"></a>Extender el empaquetado e implementación de SharePoint
  El proceso de empaquetado e implementación de proyectos de SharePoint se puede ampliar.
  
##  <a name="creating-deployment-steps"></a>Crear pasos de implementación  
 Al implementar un proyecto de SharePoint, [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] ejecuta una serie de pasos de implementación. Visual Studio incluye pasos de implementación integrados para muchas tareas, como retirar y agregar soluciones. Sin embargo, también puede crear sus propios pasos de implementación.  
  
 Para ver un tutorial que muestra cómo crear un paso de implementación, consulte [Tutorial: crear un paso de implementación personalizado para proyectos de SharePoint de](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
##  <a name="creating-deployment-configurations"></a>Crear configuraciones de implementación  
 Una configuración de implementación es un conjunto de pasos de implementación que se ejecuta en relación con un proyecto determinado, pero que puede afectar a todos los elementos del proyecto de SharePoint. Cada configuración de implementación incluye un conjunto de pasos que se ejecuta cuando el proyecto se implementa y otro conjunto que se ejecuta cuando ese proyecto se retira. [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)]incluye dos configuraciones de implementación integradas, pero también puede crear sus propias. Cuando crea una configuración de implementación, puede incluir tanto pasos de implementación integrados como pasos de implementación de su propia cosecha.  
  
 Para ver un tutorial que muestra cómo crear una configuración de implementación, consulte [Tutorial: crear un paso de implementación personalizado para proyectos de SharePoint de](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
##  <a name="run-code-when-a-sharepoint-solution-is-deployed-or-retracted"></a>Ejecutar código cuando un proyecto de SharePoint se implementa o retira  
 Puede controlar eventos para realizar más tareas al implementar o retirar una solución de SharePoint. Visual Studio genera eventos que puede controlar en los siguientes escenarios:  
  
-   Antes y después de que cada paso de implementación se ejecute para un elemento del proyecto de SharePoint. Para obtener más información, consulte [Cómo: ejecutar código cuando pasos de implementación se ejecutan](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md).  
  
-   Antes y después de que un proyecto de SharePoint se implemente o retire Para obtener más información, consulte [Cómo: ejecutar código cuando un proyecto de SharePoint es implementa o retira](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md).  
  
##  <a name="handling-deployment-conflicts"></a>Abordar conflictos de implementación  
 Algunos tipos de elementos de proyecto de SharePoint, como los módulos, los elementos web, las instancias de lista y los tipos de contenido, proporcionan una resolución integrada de conflictos de implementación. Al implementar una solución que contiene uno de estos elementos de proyecto, Visual Studio comprueba primero si ya existe un archivo en el sitio de SharePoint con el mismo nombre, dirección URL o identificador que un archivo en el elemento que se va a implementar. Si existe un conflicto, Visual Studio puede resolver el conflicto automáticamente, o bien pedirle que decida si quiere que Visual Studio resuelva el conflicto o cancele la implementación. Para obtener más información, consulte [SharePoint de la solución de problemas de empaquetado e implementación](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).  
  
 Puede extender esta característica suministrando un código propio que busca y resuelve conflictos de implementación. Para obtener más información, consulte [Cómo: controlar los conflictos de implementación](../sharepoint/how-to-handle-deployment-conflicts.md).  
  
##  <a name="run-command-line-operations-before-or-after-a-project-is-deployed"></a>Ejecutar operaciones de línea de comandos antes o después de que un proyecto se implemente  
 Si quiere ejecutar una operación de línea de comandos cuando hay implementada una solución de SharePoint, puede establecer las propiedades <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PreDeploymentCommand%2A> y <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PostDeploymentCommand%2A> de un objeto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>. Visual Studio ejecuta estos comandos antes y después de que el proyecto se implemente.  
  
 En algunos casos, pueden producirse conflictos de implementación. Hay varias formas de resolver estos conflictos. Para obtener más información, consulte [SharePoint de la solución de problemas de empaquetado e implementación](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).  
  
##  <a name="customizing-validation-rules"></a>Personalizar reglas de validación  
 Antes de implementar un paquete de solución (.wsp), puede crear reglas personalizadas de validación de características y paquetes para comprobar la validez de la característica o el paquete. Así, por ejemplo, puede mostrar información, advertencias o errores a los desarrolladores para ayudarles a solucionar problemas de validación. Para obtener más información, consulte [Cómo: Create Custom Feature y reglas de validación de paquetes para soluciones de SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).  
  
## <a name="see-also"></a>Vea también  
 [Cómo: ejecutar código cuando implementación se ejecutan los pasos](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)   
 [Tutorial: Crear un paso de implementación personalizado para proyectos de SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)   
 [Cómo: crear reglas de validación de paquetes y características personalizada para soluciones de SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)   
 [Extender el sistema de proyectos de SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  
