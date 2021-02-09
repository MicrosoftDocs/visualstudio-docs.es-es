---
title: '&lt;elemento Customizations &gt; (desarrollo de Office en Visual Studio)'
description: Obtenga información sobre cómo el elemento Customizations del espacio de nombres vstov4 contiene toda la información sobre la instalación y carga de cada solución de Office.
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- <customizations> element
- customizations element
- application manifests [Office development in Visual Studio], <customizations> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 27b20a13d96b8fc23fcde2dbb8f14d1f1f27ceea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99849936"
---
# <a name="ltcustomizationsgt-element-office-development-in-visual-studio"></a>&lt;elemento Customizations &gt; (desarrollo de Office en Visual Studio)
  El elemento `customizations` del espacio de nombres `vstov4` contiene toda la información sobre la instalación y carga de cada solución de Office.

## <a name="syntax-for-document-level-customizations"></a>Sintaxis para las personalizaciones de nivel de documento

```xml
<customizations>
  <customization
    id
    <document
      solutionId
    />
  </customization>
</customizations>
```

## <a name="syntax-for-vsto-add-ins"></a>Sintaxis de los complementos de VSTO

```xml
<customizations>
  <customization
    id
    <appAddin
      application
      loadBehavior
      keyName>
    <friendlyName></friendlyName>
    <description></description>
    <formRegions></formRegions>
  </customization>
</customizations>
```

## <a name="elements-and-attributes"></a>Elementos y atributos
 El elemento `customizations` contiene información específica sobre cada solución de Office. Este elemento debe estar en el espacio de nombres siguiente: `vstov4=urn:schemas-microsoft-com:vsto.v4`. Los elementos secundarios del ensamblado también deben estar en este espacio de nombres.

 El elemento `customizations` no tiene atributos.

 El elemento `customizations` tiene el siguiente elemento secundario:

### <a name="customization"></a>Personalización
 Necesario. El `customization` elemento del `vstov4` espacio de nombres se define en el [ elemento&#62; de personalización de&#60;&#40;el desarrollo de Office en Visual Studio&#41;](../vsto/customization-element-office-development-in-visual-studio.md).

## <a name="example-of-a-document-level-customization"></a>Ejemplo de una personalización de nivel de documento

### <a name="description"></a>Descripción
 En el ejemplo de código siguiente se muestra el elemento `customizations` para una personalización de nivel de documento.

> [!NOTE]
> Este ejemplo de código forma parte de un ejemplo más grande proporcionado en los [manifiestos de aplicación para las soluciones de Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Código

```xml
<vstov4:customizations
  xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">
  <vstov4:customization>
    <vstov4:document
      solutionId="73e" />
  </vstov4:customization>
</vstov4:customizations>
```

## <a name="example-of-a-vsto-add-in"></a>Ejemplo de un complemento de VSTO

### <a name="description"></a>Descripción
 En el ejemplo de código siguiente se muestra el `customizations` elemento para un complemento de VSTO. Este es un complemento de VSTO para Outlook que incluye áreas de formulario. Este ejemplo de código forma parte de un ejemplo más grande proporcionado en los [manifiestos de aplicación para las soluciones de Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Código

```xml
<vstov4:customizations
  xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">
  <vstov4:customization>
    <vstov4:appAddIn
      application="Outlook"
      loadBehavior="3"
      keyName="ContosoOutlookAddIn">
      <vstov4:friendlyName>
        ContosoOutlookAddIn
      </vstov4:friendlyName>
      <vstov4:description>
        ContosoOutlookAddIn - Outlook VSTO Add-in
        created with Visual Studio Tools for Office
      </vstov4:description>
      <vstov4:formRegions>
        <vstov4:formRegion
            name="OutlookAddIn1.FormRegion1">
          <vstov4:messageClass name="IPM.Note" />
          <vstov4:messageClass name="IPM.Contact" />
          <vstov4:messageClass name="IPM.Appointment" />
        </vstov4:formRegion>
      </vstov4:formRegions>
    </vstov4:appAddIn>
  </vstov4:customization>
</vstov4:customizations>
```

## <a name="see-also"></a>Consulte también

- [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)