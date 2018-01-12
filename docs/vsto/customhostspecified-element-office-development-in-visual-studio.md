---
title: '&lt;customHostSpecified&gt; elemento (desarrollo de Office en Visual Studio) | Documentos de Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <customHostSpecified> element
- <customHostSpecified> element
- customHostSpecified element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 80007310f5556bcc8c67b61e7ff41953cc7c900e
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="ltcustomhostspecifiedgt-element-office-development-in-visual-studio"></a>&lt;customHostSpecified&gt; elemento (desarrollo de Office en Visual Studio)
  El `customHostSpecified` elemento indica que esta solución no es una aplicación independiente. Las soluciones de Office contienen componentes que están alojados en aplicaciones de Microsoft Office.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<customHostSpecified />  
```  
  
## <a name="elements-and-attributes"></a>Elementos y atributos  
 El `customHostSpecified` elemento es necesario para las soluciones de Office. Este elemento está en la `co.v1` espacio de nombres y especifica que esta implementación contiene un componente que se va a implementar dentro de un host personalizado, y no es una aplicación independiente.  
  
 Este elemento es un elemento secundario de la primera `<entrypoint>` elemento en el manifiesto de aplicación. No puede haber ningún otro elemento secundario que `<entrypoint>` elemento o [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] , se producirá un error de validación durante la instalación.  
  
 Este elemento no tiene atributos y ningún elemento secundario.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra el `customHostSpecified` elemento en un manifiesto de aplicación para una solución de Office. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
```  
<entryPoint>  
    <co.v1:customHostSpecified />  
</entryPoint>  
```  
  
## <a name="see-also"></a>Vea también  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifiesto de aplicación ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  