---
title: '&lt;Description &gt; (elemento, desarrollo de Office en Visual Studio)'
titleSuffix: ''
ms.custom: secdec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- description element
- <description> element
- application manifests [Office development in Visual Studio], <description> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4c8b54f8ccf2181a053ae5d2fe221b49840cd72c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85520272"
---
# <a name="ltdescriptiongt-element-office-development-in-visual-studio"></a>&lt;Description &gt; (elemento, desarrollo de Office en Visual Studio)
  El elemento `description` del espacio de nombres `vstov4` almacena la descripción de la solución de Office que aparece en el cuadro de diálogo de complementos COM de aplicaciones de Microsoft Office.

## <a name="syntax"></a>Sintaxis

```xml
<description>
</description>
```

## <a name="elements-and-attributes"></a>Elementos y atributos
 Opcional. El elemento `description` está en el espacio de nombres `vstov4` . Contiene la descripción del complemento que se muestra en el cuadro de diálogo Complementos COM de las aplicaciones de Microsoft Office.

 El elemento `description` no tiene atributos ni elementos secundarios.

## <a name="vsto-add-in-example"></a>Ejemplo de complemento de VSTO

### <a name="description"></a>Descripción
 En el siguiente ejemplo de código se muestra el elemento `description` en una solución de nivel de aplicación implementada mediante [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este ejemplo de código forma parte de un ejemplo más grande proporcionado en los [manifiestos de aplicación para las soluciones de Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Código

```xml
<vstov4:description>
  ContosoOutlookAddIn - Outlook add-in
  created with Visual Studio Tools for Office
</vstov4:description>
```

## <a name="see-also"></a>Consulte también

- [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)