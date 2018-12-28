---
title: '&lt;descripción&gt; elemento (desarrollo de Office en Visual Studio)'
titleSuffix: ''
ms.custom: secdec18
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- description element
- <description> element
- application manifests [Office development in Visual Studio], <description> element
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: da75844d8c0aa1f39a639de77f916c948e64ea35
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/27/2018
ms.locfileid: "53803940"
---
# <a name="ltdescriptiongt-element-office-development-in-visual-studio"></a>&lt;descripción&gt; elemento (desarrollo de Office en Visual Studio)
  El elemento `description` del espacio de nombres `vstov4` almacena la descripción de la solución de Office que aparece en el cuadro de diálogo de complementos COM de aplicaciones de Microsoft Office.

## <a name="syntax"></a>Sintaxis

```xml
<description>
</description>
```

## <a name="elements-and-attributes"></a>Los elementos y atributos
 Opcional. El elemento `description` está en el espacio de nombres `vstov4` . Contiene la descripción del complemento que se muestra en el cuadro de diálogo Complementos COM de las aplicaciones de Microsoft Office.

 El elemento `description` no tiene atributos ni elementos secundarios.

## <a name="vsto-add-in-example"></a>Ejemplo de complemento de VSTO

### <a name="description"></a>Descripción
 En el siguiente ejemplo de código se muestra el elemento `description` en una solución de nivel de aplicación implementada mediante [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Código

```xml
<vstov4:description>
  ContosoOutlookAddIn - Outlook add-in
  created with Visual Studio Tools for Office
</vstov4:description>
```

## <a name="see-also"></a>Vea también

- [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)