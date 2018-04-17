---
title: 'Cómo: crear reglas de validación de paquetes y características personalizada para soluciones de SharePoint | Documentos de Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
- SharePoint development in Visual Studio, validation rules
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0c68df756e24fc45603d34dd6982a09889bd5203
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions"></a>Cómo: Crear reglas de validación de la característica y el paquete personalizados para las soluciones de SharePoint
  Puede crear reglas de validación personalizadas para comprobar el paquete de solución generado por Visual Studio. Puede realizar la validación completa en una característica en su totalidad o paquete seleccionando **validar** en el menú contextual de un paquete o una característica en el **PackagingExplorer**. Al agregar nuevas características o elementos de proyecto de SharePonit al proyecto para determinar si el paquete o la característica encontraría en un estado válido, se realiza una validación parcial.  
  
### <a name="to-create-a-custom-package-validation-rule"></a>Para crear una regla de validación de paquetes personalizada  
  
1.  Cree un proyecto de biblioteca de clases.  
  
2.  Agregue referencias a los siguientes ensamblados:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  Cree una clase que implementa una de las interfaces siguientes:  
  
    -   Para crear una regla de validación de paquetes, implemente el <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> interfaz.  
  
    -   Para crear una regla de validación de características, implemente el <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> interfaz.  
  
4.  Agregue el <xref:System.ComponentModel.Composition.ExportAttribute> a la clase. Este atributo permite que Visual Studio detecte y cargue la regla de validación. Pasar el <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> o <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> tipo al constructor de atributo.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra cómo crear una regla de validación de características personalizada.  
  
 [!code-vb[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/VisualBasic/featurevalidation/extension/customvalidationrule.vb#1)]
 [!code-csharp[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/CSharp/featurevalidation/extension/customfeaturevalidationrule.cs#1)]  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Este ejemplo requiere referencias a los siguientes ensamblados:  
  
-   Microsoft.VisualStudio.SharePoint.  
  
-   System.ComponentModel.Composition.  
  
## <a name="deploying-the-extension"></a>Implementar la extensión  
 Para implementar la extensión, cree un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] paquete de extensión (VSIX) para el ensamblado y cualquier otro archivo que desee distribuir con la extensión. Para obtener más información, consulte [extensiones de implementación para las herramientas de SharePoint en Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Vea también  
 [Extender el empaquetado y la implementación de SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  
  