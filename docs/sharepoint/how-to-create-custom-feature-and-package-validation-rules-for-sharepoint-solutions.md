---
title: "How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions | Microsoft Docs"
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
  - "SharePoint development in Visual Studio, validation rules"
ms.assetid: 17e818f8-0f3a-4a96-a6fc-1634ddb4825d
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions
  Puede crear reglas de validación personalizadas para comprobar el paquete de solución generado por Visual Studio.  Puede realizar una validación completa de toda una característica o paquete seleccionando **Validar** en el menú contextual de un paquete o característica en el **Exploradorde empaquetado**.  Cuando se agregan nuevos elementos de proyecto o características de SharePoint al proyecto para determinar si el paquete o la característica tendrían un estado válido, se realiza una validación parcial.  
  
### Para crear una regla de validación de paquetes personalizada  
  
1.  Cree un proyecto de biblioteca de clases  
  
2.  Agregue referencias a los siguientes ensamblados:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  Cree una clase que implemente una de las siguientes interfaces:  
  
    -   Para crear una regla de validación de paquetes, implemente la interfaz <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule>.  
  
    -   Para crear una regla de validación de características, implemente la interfaz <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule>.  
  
4.  Agregue <xref:System.ComponentModel.Composition.ExportAttribute> a la clase.  Este atributo permite que Visual Studio detecte y cargue la regla de validación.  Pase el tipo <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> o <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> al constructor del atributo.  
  
## Ejemplo  
 En el ejemplo de código siguiente se muestra cómo se crea una regla de validación de características personalizada.  
  
 [!code-csharp[SPExtensibility.FeatureValidation#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.featurevalidation/cs/extension/customfeaturevalidationrule.cs#1)]
 [!code-vb[SPExtensibility.FeatureValidation#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.featurevalidation/vb/extension/customvalidationrule.vb#1)]  
  
## Compilar el código  
 Para este ejemplo se requieren referencias a los siguientes ensamblados:  
  
-   Microsoft.VisualStudio.SharePoint.  
  
-   System.ComponentModel.Composition.  
  
## Implementar la extensión  
 Para implementar la extensión, cree un paquete de extensión \(VSIX\) de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] para el ensamblado y el resto de archivos que desee distribuir con la extensión.  Para obtener más información, vea [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Vea también  
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  
  