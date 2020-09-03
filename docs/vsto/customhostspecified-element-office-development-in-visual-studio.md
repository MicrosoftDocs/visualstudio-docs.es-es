---
title: '&lt;&gt;elemento customHostSpecified (desarrollo de Office en Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <customHostSpecified> element
- <customHostSpecified> element
- customHostSpecified element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 689848f14b4540a54489b4ea5bbad67e493fe276
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544916"
---
# <a name="ltcustomhostspecifiedgt-element-office-development-in-visual-studio"></a>&lt;&gt;elemento customHostSpecified (desarrollo de Office en Visual Studio)
  El `customHostSpecified` elemento indica que esta solución no es una aplicación independiente. Las soluciones de Office contienen componentes que se hospedan en Microsoft Office aplicaciones.

## <a name="syntax"></a>Sintaxis

```xml
<customHostSpecified />
```

## <a name="elements-and-attributes"></a>Elementos y atributos
 El `customHostSpecified` elemento es necesario para las soluciones de Office. Este elemento está en el `co.v1` espacio de nombres y especifica que esta implementación contiene un componente que se implementará dentro de un host personalizado y no es una aplicación independiente.

 Este elemento es un elemento secundario del primer `<entrypoint>` elemento del manifiesto de aplicación. No puede haber otros elementos secundarios en ese `<entrypoint>` elemento o producirá [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] un error de validación durante la instalación.

 Este elemento no tiene atributos ni elementos secundarios.

## <a name="example"></a>Ejemplo
 En el ejemplo de código siguiente se muestra el `customHostSpecified` elemento en un manifiesto de aplicación para una solución de Office. Este ejemplo de código forma parte de un ejemplo más grande proporcionado en los [manifiestos de aplicación para las soluciones de Office](../vsto/application-manifests-for-office-solutions.md).

```xml
<entryPoint>
    <co.v1:customHostSpecified />
</entryPoint>
```

## <a name="see-also"></a>Consulte también

- [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)