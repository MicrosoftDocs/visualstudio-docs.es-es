---
title: "Extending SharePoint Packaging and Deployment | Microsoft Docs"
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
  - "SharePoint development in Visual Studio, extending deployment"
ms.assetid: 4789ebb2-12bc-42b9-9427-e63d77137765
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# Extending SharePoint Packaging and Deployment
  El proceso de empaquetado e implementación de proyectos de SharePoint se puede ampliar.  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
##  <a name="creating_deployment_steps"></a> Crear pasos de implementación  
 Al implementar un proyecto de SharePoint, [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] ejecuta una serie de pasos de implementación.  Visual Studio incluye pasos de implementación integrados para muchas tareas, como retirar y agregar soluciones.  Sin embargo, también puede crear sus propios pasos de implementación.  
  
 Para ver un tutorial donde se explica cómo crear un paso de implementación, vea [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
##  <a name="creating_deployment_configurations"></a> Crear configuraciones de implementación  
 Una configuración de implementación es un conjunto de pasos de implementación que se ejecuta en relación con un proyecto determinado, pero que puede afectar a todos los elementos del proyecto de SharePoint.  Cada configuración de implementación incluye un conjunto de pasos que se ejecuta cuando el proyecto se implementa y otro conjunto que se ejecuta cuando ese proyecto se retira.  [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] incluye dos configuraciones de implementación integradas, pero puede crear las suyas propias.  Cuando crea una configuración de implementación, puede incluir tanto pasos de implementación integrados como pasos de implementación de su propia cosecha.  
  
 Para ver un tutorial donde se explica cómo crear una configuración de implementación, vea [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
##  <a name="run_code_before_and_after_each_deployment_step"></a> Ejecutar código cuando un proyecto de SharePoint se implementa o retira  
 Puede controlar eventos para realizar más tareas al implementar o retirar una solución de SharePoint.  Visual Studio genera eventos que puede controlar en los siguientes escenarios:  
  
-   Antes y después de que cada paso de implementación se ejecute para un elemento del proyecto de SharePoint.  Para obtener más información, vea [How to: Run Code When Deployment Steps are Executed](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md).  
  
-   Antes y después de que un proyecto de SharePoint se implemente o retire  Para obtener más información, vea [How to: Run Code When a SharePoint Project is Deployed or Retracted](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md).  
  
##  <a name="deployment_conflicts"></a> Abordar conflictos de implementación  
 Algunos tipos de elementos de proyecto de SharePoint, como los módulos, los elementos web, las instancias de lista y los tipos de contenido, proporcionan una resolución integrada de conflictos de implementación.  Al implementar una solución que contiene uno de estos elementos de proyecto, Visual Studio comprueba primero si ya existe un archivo en el sitio de SharePoint con el mismo nombre, dirección URL o identificador que un archivo en el elemento que se va a implementar.  Si existe un conflicto, Visual Studio puede resolver el conflicto automáticamente, o bien pedirle que decida si quiere que Visual Studio resuelva el conflicto o cancele la implementación.  Para obtener más información, vea [Solucionar problemas de empaquetado e implementación de SharePoint](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).  
  
 Puede extender esta característica suministrando un código propio que busca y resuelve conflictos de implementación.  Para obtener más información, vea [How to: Handle Deployment Conflicts](../sharepoint/how-to-handle-deployment-conflicts.md).  
  
##  <a name="run_command_line_operations_before_or_after_a_project_is_deployed"></a> Ejecutar operaciones de línea de comandos antes o después de que un proyecto se implemente  
 Si quiere ejecutar una operación de línea de comandos cuando hay implementada una solución de SharePoint, puede establecer las propiedades <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PreDeploymentCommand%2A> y <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PostDeploymentCommand%2A> de un objeto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>.  Visual Studio ejecuta estos comandos antes y después de que el proyecto se implemente.  
  
 En algunos casos, pueden producirse conflictos de implementación.  Hay varias formas de resolver estos conflictos.  Para obtener más información, vea [Solucionar problemas de empaquetado e implementación de SharePoint](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).  
  
##  <a name="customizing_validation_rules"></a> Personalizar reglas de validación  
 Antes de implementar un paquete de solución \(.wsp\), puede crear reglas personalizadas de validación de características y paquetes para comprobar la validez de la característica o el paquete.  Así, por ejemplo, puede mostrar información, advertencias o errores a los desarrolladores para ayudarles a solucionar problemas de validación.  Para obtener más información, vea [How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).  
  
## Vea también  
 [How to: Run Code When Deployment Steps are Executed](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)   
 [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)   
 [How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)   
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  