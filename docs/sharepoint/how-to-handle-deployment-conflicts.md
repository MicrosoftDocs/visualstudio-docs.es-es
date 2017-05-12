---
title: "How to: Handle Deployment Conflicts"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SharePoint development in Visual Studio, extending deployment"
ms.assetid: 8e545873-3fed-46cf-a95f-27b5fc0d5f83
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# How to: Handle Deployment Conflicts
  Puede proporcionar su propio código para controlar los conflictos de implementación para un elemento de proyecto de SharePoint.  Por ejemplo, puede determinar si algunos archivos del elemento de proyecto actual ya existen en la ubicación de implementación y, a continuación, eliminar los archivos implementados antes de implementar el elemento de proyecto actual.  Para obtener más información sobre los conflictos de implementación, vea [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
### Para controlar un conflicto de implementación  
  
1.  Cree una extensión de elemento de proyecto, una extensión de proyecto o una definición de un nuevo tipo de elemento de proyecto.  Para obtener más información, vea los temas siguientes:  
  
    -   [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  En la extensión, controle el evento <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> de un objeto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> \(en una extensión de elemento de proyecto o en una extensión de proyecto\) o de un objeto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> \(en una definición de un nuevo tipo de elemento de proyecto\).  
  
3.  En el controlador de eventos, determine si hay un conflicto entre el elemento de proyecto que se implementa y la solución implementada en el sitio de SharePoint, basándose en los criterios que se aplican a su escenario.  Puede usar la propiedad <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemEventArgs.ProjectItem%2A> del parámetro de argumentos del evento para analizar el elemento de proyecto que se implementa y puede analizar los archivos en la ubicación de implementación si llama a un comando de SharePoint definido para este propósito.  
  
     Para muchos tipos de conflictos, sería conveniente determinar primero qué paso de implementación se está ejecutando.  Puede hacerlo mediante la propiedad <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.DeploymentStepInfo%2A> del parámetro de argumentos del evento.  Aunque normalmente tiene sentido detectar los conflictos durante el paso de implementación integrado de <xref:Microsoft.VisualStudio.SharePoint.Deployment.DeploymentStepIds.AddSolution>, puede comprobar si existen conflictos durante cualquier paso de la implementación.  
  
4.  Si existe un conflicto, use el método <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> de la propiedad <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.Conflicts%2A> de los argumentos del evento para crear un nuevo objeto <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict>.  Este objeto representa el conflicto de implementación.  En la llamada al método <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A>, especifique también el método al que se llama para resolver el conflicto.  
  
## Ejemplo  
 En el ejemplo de código siguiente se muestra el proceso básico para controlar un conflicto de implementación en una extensión de elemento de proyecto para los elementos de proyecto de la definición de lista.  Para controlar un conflicto de implementación en un tipo diferente de elemento de proyecto, pase una cadena diferente a <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>.  Para obtener más información, vea [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md).  
  
 Para simplificar, en el controlador de eventos <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> de este ejemplo se supone que existe un conflicto de implementación \(es decir, siempre agrega un nuevo objeto <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict>\) y el método `Resolve` simplemente devuelve **true** para indicar que el conflicto se resolvió.  En un escenario real, el controlador de eventos <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> determinaría primero si existe un conflicto entre un archivo del elemento de proyecto actual y un archivo almacenado en la ubicación de implementación y, a continuación, agregaría un objeto <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> solo si existe un conflicto.  Por ejemplo, podría usar la propiedad `e.ProjectItem.Files` en el controlador de eventos para analizar los archivos del elemento de proyecto y podría llamar a un comando de SharePoint de analizar los archivos en la ubicación de implementación.  De igual forma, en un escenario real el método `Resolve` podría llamar a un comando de SharePoint para resolver el conflicto en el sitio de SharePoint.  Para obtener más información sobre la creación de comandos de SharePoint, vea [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md).  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.deploymentconflict/cs/extension/deploymentconflictextension.cs#1)]
 [!code-vb[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.deploymentconflict/vb/extension/deploymentconflictextension.vb#1)]  
  
## Compilar el código  
 Para este ejemplo se requieren referencias a los siguientes ensamblados:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Implementar la extensión  
 Para implementar la extensión, cree un paquete de extensión \(VSIX\) de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] para el ensamblado y el resto de archivos que desee distribuir con la extensión.  Para obtener más información, vea [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Vea también  
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [How to: Run Code When Deployment Steps are Executed](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)   
 [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md)  
  
  