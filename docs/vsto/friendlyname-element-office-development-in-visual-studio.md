---
description: El elemento friendlyName del espacio de nombres vstov4 almacena el nombre que aparece en la lista de programas instalados.
title: '&lt;&gt;elemento friendlyName (desarrollo de Office en Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <friendlyName> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: adcf46a2c232176026181283549c0c59fc713603
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223451"
---
# <a name="ltfriendlynamegt-element-office-development-in-visual-studio"></a>&lt;&gt;elemento friendlyName (desarrollo de Office en Visual Studio)
  El elemento `friendlyName` del espacio de nombres `vstov4` almacena el nombre que aparece en la lista de programas instalados.

## <a name="syntax"></a>Sintaxis

```xml
<friendlyName>
</friendlyName>
```

## <a name="elements-and-attributes"></a>Elementos y atributos
 El elemento `friendlyName` está en el espacio de nombres `vstov4` . El valor se muestra en la lista de programas instalados en el equipo y en el cuadro de diálogo de complementos de VSTO COM de las aplicaciones de Microsoft Office.

 El elemento `friendlyName` no tiene atributos ni elementos secundarios.

## <a name="vsto-add-in-example"></a>Ejemplo de complemento de VSTO

### <a name="description"></a>Descripción
 En el siguiente ejemplo de código se muestra el elemento `friendlyName` en una solución de nivel de aplicación implementada mediante [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este ejemplo de código forma parte de un ejemplo más grande proporcionado en los [manifiestos de aplicación para las soluciones de Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Código

```xml
<vstov4:friendlyName>
  ContosoOutlookAddIn
</vstov4:friendlyName>
```

## <a name="see-also"></a>Consulte también

- [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)
