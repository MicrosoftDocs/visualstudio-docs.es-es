---
title: Filtrar Crear característica personalizada y las reglas de validación de paquete para las soluciones de SharePoint | Documentos de Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
- SharePoint development in Visual Studio, validation rules
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 57ea15d8f0a92d28d8687f3b3513a6610683da11
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56633605"
---
# <a name="how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions"></a>Procedimiento Crear paquetes y características personalizado reglas de validación para las soluciones de SharePoint
  Puede crear reglas de validación personalizadas para comprobar el paquete de solución generado por Visual Studio. Puede realizar la validación completa en una característica completa o el paquete seleccionando **validar** en el menú contextual de un paquete o una característica en el **PackagingExplorer**. Al agregar nuevos elementos de proyecto SharePonit o características al proyecto para determinar si el paquete o la característica sería un estado válido, se realiza una validación parcial.

### <a name="to-create-a-custom-package-validation-rule"></a>Para crear una regla de validación de paquete personalizado

1.  Cree un proyecto de biblioteca de clases.

2.  Agregue referencias a los siguientes ensamblados:

    -   Microsoft.VisualStudio.SharePoint

    -   System.ComponentModel.Composition

3.  Cree una clase que implementa una de las interfaces siguientes:

    -   Para crear una regla de validación del paquete, implemente el <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> interfaz.

    -   Para crear una regla de validación de características, implemente el <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> interfaz.

4.  Agregue el <xref:System.ComponentModel.Composition.ExportAttribute> a la clase. Este atributo permite que Visual Studio detecte y cargue su regla de validación. Pase el <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> o <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> tipo al constructor del atributo.

## <a name="example"></a>Ejemplo
 En el ejemplo de código siguiente se muestra cómo crear una regla de validación de característica personalizada.

 [!code-vb[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/VisualBasic/featurevalidation/extension/customvalidationrule.vb#1)]
 [!code-csharp[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/CSharp/featurevalidation/extension/customfeaturevalidationrule.cs#1)]

## <a name="compile-the-code"></a>Compilar el código
 Este ejemplo requiere referencias a los ensamblados siguientes:

-   Microsoft.VisualStudio.SharePoint.

-   System.ComponentModel.Composition.

## <a name="deploy-the-extension"></a>Implementar la extensión
 Para implementar la extensión, cree un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] paquete de extensión (VSIX) para el ensamblado y otros archivos que desea distribuir con la extensión. Para obtener más información, consulte [herramientas de implementación de extensiones de SharePoint en Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vea también
- [Ampliar la implementación y empaquetado de SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
