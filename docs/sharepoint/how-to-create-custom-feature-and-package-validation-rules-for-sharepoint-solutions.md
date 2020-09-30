---
title: Crear validaciones de características y paquetes para soluciones de SharePoint
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 7ac718d16383448ea13f01ad367d97f917bb42ed
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585828"
---
# <a name="create-feature-and-package-validations-for-sharepoint-solutions"></a>Crear validaciones de características y paquetes para soluciones de SharePoint

  Puede crear reglas de validación personalizadas para comprobar el paquete de soluciones generado por Visual Studio. Puede realizar la validación completa de una característica o paquete completo seleccionando **validar** en el menú contextual de un paquete o característica en el **PackagingExplorer**. La validación parcial se realiza al agregar nuevas características o elementos de proyecto de SharePoint al proyecto para determinar si el paquete o la característica se encontrarían en un estado válido.

### <a name="to-create-a-custom-package-validation-rule"></a>Para crear una regla de validación de paquetes personalizada

1. Cree un proyecto de biblioteca de clases.

2. Agregue referencias a los siguientes ensamblados:

    - Microsoft.VisualStudio.SharePoint

    - System.ComponentModel.Composition

3. Cree una clase que implemente una de las interfaces siguientes:

    - Para crear una regla de validación de paquetes, implemente la <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> interfaz.

    - Para crear una regla de validación de características, implemente la <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> interfaz.

4. Agregue <xref:System.ComponentModel.Composition.ExportAttribute> a la clase. Este atributo permite a Visual Studio detectar y cargar la regla de validación. Pase el <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> tipo o al constructor de atributos.

## <a name="example"></a>Ejemplo
 En el ejemplo de código siguiente se muestra cómo crear una regla de validación de características personalizada.

 [!code-vb[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/VisualBasic/featurevalidation/extension/customvalidationrule.vb#1)]
 [!code-csharp[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/CSharp/featurevalidation/extension/customfeaturevalidationrule.cs#1)]

## <a name="compile-the-code"></a>Compilar el código
 Este ejemplo requiere referencias a los ensamblados siguientes:

- Microsoft. VisualStudio. SharePoint.

- System. ComponentModel. Composition.

## <a name="deploy-the-extension"></a>Implementar la extensión
 Para implementar la extensión, cree un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] paquete de extensión (VSIX) para el ensamblado y cualquier otro archivo que desee distribuir con la extensión. Para obtener más información, vea [deploy Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vea también
- [Extender el empaquetado e implementación de SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
