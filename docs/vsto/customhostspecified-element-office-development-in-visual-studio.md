---
title: '&lt;customHostSpecified&gt; elemento (desarrollo de Office en Visual Studio)'
ms.custom: ''
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d4eaf874a259251c35a6b01c08f544993092ff4d
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
ms.locfileid: "34264040"
---
# <a name="ltcustomhostspecifiedgt-element-office-development-in-visual-studio"></a>&lt;customHostSpecified&gt; elemento (desarrollo de Office en Visual Studio)
  El `customHostSpecified` elemento indica que esta solución no es una aplicación independiente. Las soluciones de Office contienen componentes que están alojados en aplicaciones de Microsoft Office.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml
<customHostSpecified />  
```  
  
## <a name="elements-and-attributes"></a>Elementos y atributos  
 El `customHostSpecified` elemento es necesario para las soluciones de Office. Este elemento está en la `co.v1` espacio de nombres y especifica que esta implementación contiene un componente que se va a implementar dentro de un host personalizado, y no es una aplicación independiente.  
  
 Este elemento es un elemento secundario de la primera `<entrypoint>` elemento en el manifiesto de aplicación. No puede haber ningún otro elemento secundario que `<entrypoint>` elemento o [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] , se producirá un error de validación durante la instalación.  
  
 Este elemento no tiene atributos y ningún elemento secundario.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra el `customHostSpecified` elemento en un manifiesto de aplicación para una solución de Office. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md).  
  
```xml
<entryPoint>  
    <co.v1:customHostSpecified />  
</entryPoint>  
```  
  
## <a name="see-also"></a>Vea también  
 [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifiesto de aplicación ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  