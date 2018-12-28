---
title: '&lt;customHostSpecified&gt; elemento (desarrollo de Office en Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <customHostSpecified> element
- <customHostSpecified> element
- customHostSpecified element
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: f1209460448b02cfb05329c8c3f487f6ef444649
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/27/2018
ms.locfileid: "53802616"
---
# <a name="ltcustomhostspecifiedgt-element-office-development-in-visual-studio"></a>&lt;customHostSpecified&gt; elemento (desarrollo de Office en Visual Studio)
  El `customHostSpecified` elemento indica que esta solución no es una aplicación independiente. Soluciones de Office contienen componentes que están alojados en aplicaciones de Microsoft Office.

## <a name="syntax"></a>Sintaxis

```xml
<customHostSpecified />
```

## <a name="elements-and-attributes"></a>Los elementos y atributos
 El `customHostSpecified` elemento es necesario para soluciones de Office. Este elemento está en el `co.v1` espacio de nombres y especifica que esta implementación contiene un componente que se va a implementar dentro de un host personalizado y no es una aplicación independiente.

 Este es un elemento secundario de la primera `<entrypoint>` elemento en el manifiesto de aplicación. No puede haber ningún otro elemento secundario en el que `<entrypoint>` elemento o [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] , se producirá un error de validación durante la instalación.

 Este elemento no tiene atributos y ningún elemento secundario.

## <a name="example"></a>Ejemplo
 En el ejemplo de código siguiente se ilustra la `customHostSpecified` elemento en un manifiesto de aplicación para una solución de Office. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md).

```xml
<entryPoint>
    <co.v1:customHostSpecified />
</entryPoint>
```

## <a name="see-also"></a>Vea también

- [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)