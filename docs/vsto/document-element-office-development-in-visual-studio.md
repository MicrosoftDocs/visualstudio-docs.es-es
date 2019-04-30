---
title: '&lt;documento&gt; elemento (desarrollo de Office en Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document element
- application manifests [Office development in Visual Studio], <document> element
- <document> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 36d822d60d1a28d48f660f6d358b75bf4a913048
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63000024"
---
# <a name="ltdocumentgt-element-office-development-in-visual-studio"></a>&lt;documento&gt; elemento (desarrollo de Office en Visual Studio)
  El `document` elemento de la `vstov4` espacio de nombres almacena información específica de la personalización para las personalizaciones de nivel de documento.

## <a name="syntax"></a>Sintaxis

```xml
<document solutionId />
```

## <a name="elements-and-attributes"></a>Elementos y atributos
 Solo es necesario para las personalizaciones de nivel de documento. El elemento `document` está en el espacio de nombres `vstov4` . El elemento `document` tiene los atributos siguientes:

|Atributo|Descripción|
|---------------|-----------------|
|`solutionId`|Obligatorio. El GUID que usa Visual Studio Tools para Office runtime para identificar de forma única una solución de nivel de documento. Este valor se almacena como la propiedad de documento personalizada _AssemblyLocation. Para obtener más información, consulte [información general de las propiedades de documento personalizada](../vsto/custom-document-properties-overview.md).|

 `document` no tiene elementos secundarios.

## <a name="document-level-customization-example"></a>Ejemplo de personalización de nivel de documento

### <a name="description"></a>Descripción
 En el ejemplo de código siguiente se ilustra la `document` elemento en una solución de Office de nivel de documento implementada mediante el uso de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Código

```xml
<vstov4:document
  solutionId="73e" />
```

## <a name="see-also"></a>Vea también

- [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)