---
title: '&lt;Document &gt; (elemento, desarrollo de Office en Visual Studio)'
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e92c17d71b1c0959cb1918ce6fbad0e2cd44d5ec
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949836"
---
# <a name="ltdocumentgt-element-office-development-in-visual-studio"></a>&lt;Document &gt; (elemento, desarrollo de Office en Visual Studio)
  El `document` elemento del `vstov4` espacio de nombres almacena información específica de la personalización para las personalizaciones de nivel de documento.

## <a name="syntax"></a>Sintaxis

```xml
<document solutionId />
```

## <a name="elements-and-attributes"></a>Elementos y atributos
 Solo es necesario para las personalizaciones de nivel de documento. El elemento `document` está en el espacio de nombres `vstov4` . El elemento `document` tiene los atributos siguientes:

|Atributo|Descripción|
|---------------|-----------------|
|`solutionId`|Necesario. GUID que usa el Visual Studio Tools para Office Runtime para identificar de forma única una solución de nivel de documento. Este valor se almacena como _AssemblyLocation propiedad de documento personalizada. Para obtener más información, vea [información general sobre las propiedades personalizadas del documento](../vsto/custom-document-properties-overview.md).|

 `document` no tiene elementos secundarios.

## <a name="document-level-customization-example"></a>Ejemplo de personalización de nivel de documento

### <a name="description"></a>Descripción
 En el ejemplo de código siguiente se muestra el `document` elemento en una solución de Office de nivel de documento implementada mediante [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Este ejemplo de código forma parte de un ejemplo más grande proporcionado en los [manifiestos de aplicación para las soluciones de Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Código

```xml
<vstov4:document
  solutionId="73e" />
```

## <a name="see-also"></a>Consulte también

- [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)