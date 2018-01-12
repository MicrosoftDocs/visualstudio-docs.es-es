---
title: "Combinar XML en paquetes y características manifiestos | Documentos de Microsoft"
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
helpviewer_keywords: SharePoint development in Visual Studio, packaging
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 81e6f83dd4fc825e885843a47d45485918f7dabe
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="merging-xml-in-feature-and-package-manifests"></a>Combinar XML en manifiestos de la característica y el paquete
  Paquetes y las características se definen mediante [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] los archivos de manifiesto. Estos manifiestos empaquetados son una combinación de datos generados a partir de los diseñadores y personaliza [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] especificados en la plantilla de manifiesto por los usuarios. Durante el empaquetado, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] combina personalizado [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] instrucciones con proporcionados por el diseñador [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] para formar el empaquetado [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] archivo de manifiesto. Elementos similares, con las excepciones que se mencionan más adelante en excepciones de combinación se combinan para evitar [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] errores de validación después de implementar los archivos en SharePoint y para realizar el manifiesto de archivos más pequeño y eficaz.  
  
## <a name="modifying-the-manifests"></a>Modificar los manifiestos  
 No se puede modificar directamente los archivos de manifiesto empaquetados hasta que se deshabiliten a los diseñadores de característica o paquete. Sin embargo, puede agregar manualmente personalizado [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] elementos a la plantilla de manifiesto ya sea a través de los diseñadores de características y paquetes o [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] editor. Para obtener más información, consulte [Cómo: personalizar una característica de SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md) y [Cómo: personalizar un paquete de solución de SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
## <a name="feature-and-package-manifest-merge-process"></a>Proceso de mezcla de manifiesto de características y paquetes  
 Al combinar los elementos personalizados junto con los elementos proporcionados por el diseñador, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] utiliza el siguiente proceso. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]comprueba si cada elemento tiene un valor de clave única. Si un elemento no tiene ningún valor de clave única, se anexa al archivo de manifiesto empaquetado. De forma similar, no se pueden combinar los elementos que tienen varias claves. Por lo tanto, se anexan al archivo de manifiesto.  
  
 Si un elemento tiene una clave única, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] compara los valores del diseñador y claves personalizadas. Si los valores coinciden, combinan en un solo valor. Si los valores son distintos, se descarta el valor de clave de diseñador y se utiliza el valor de clave personalizado. También se combinan las colecciones. Por ejemplo, si el generado por el diseñador [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] y personalizado [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] tanto contiene una colección de ensamblados, el manifiesto empaquetado contiene solo una colección de ensamblados.  
  
## <a name="merge-exceptions"></a>Mezcla de excepciones  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]combina la mayoría de diseñador [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] elementos junto con personalizado similar [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] elementos siempre que tengan un atributo de identificación única. Sin embargo, algunos elementos no tienen el identificador único necesario para [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] combinar. Estos elementos se conocen como *mezcla excepciones*. En estos casos, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] no combina personalizado [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] elementos junto con los proporcionados por el diseñador [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] elementos, pero en su lugar los anexa al archivo de manifiesto empaquetado.  
  
 Aquí te mostramos una lista de excepciones de combinación de características y paquetes [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] los archivos de manifiesto.  
  
|Diseñador|Elemento XML|  
|--------------|-----------------|  
|Diseñador de características|ActivationDependency|  
|Diseñador de características|UpgradeAction|  
|Diseñador de paquetes|SafeControl|  
|Diseñador de paquetes|CodeAccessSecurity|  
  
## <a name="feature-manifest-elements"></a>Elementos de manifiesto de características  
 En la tabla siguiente es una lista de todos los elementos de manifiesto de características que se pueden combinar y la clave única que se utiliza para la coincidencia.  
  
|Nombre del elemento|Clave única|  
|------------------|----------------|  
|Característica (todos los atributos)|*Nombre de atributo* (cada nombre de atributo del elemento de característica es una clave única).|  
|ElementFile|Ubicación|  
|ElementManifests/ElementManifest|Ubicación|  
|Propiedad/propiedades|Key|  
|CustomUpgradeAction|nombre|  
|CustomUpgradeActionParameter|nombre|  
  
> [!NOTE]  
>  Dado que es la única manera de modificar el elemento CustomUpgradeAction personalizado [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] editor, el efecto de combinar no es bajo.  
  
## <a name="package-manifest-elements"></a>Elementos del manifiesto del paquete  
 En la tabla siguiente es una lista de todos los elementos de manifiesto de paquete que se pueden combinar y la clave única que se utiliza para la coincidencia.  
  
|Nombre del elemento|Clave única|  
|------------------|----------------|  
|Solución (todos los atributos)|*Nombre de atributo* (cada nombre de atributo del elemento de solución es una clave única).|  
|ApplicationResourceFiles/ApplicationResourceFile|Ubicación|  
|Ensamblados y ensamblado|Ubicación|  
|ClassResources/ClassResource|Ubicación|  
|DwpFiles/DwpFile|Ubicación|  
|FeatureManifests/FeatureManifest|Ubicación|  
|Recurso|Ubicación|  
|RootFiles/RootFile|Ubicación|  
|SiteDefinitionManifests/SiteDefinitionManifest|Ubicación|  
|WebTempFile|Ubicación|  
|Plantillasarchivos/TemplateFile|Ubicación|  
|SolutionDependency|SolutionID|  
  
## <a name="manually-add-deployed-files"></a>Agregar archivos implementados manualmente  
 Algunos elementos del manifiesto, como ApplicationResourceFile y DwpFiles, especifican una ubicación que incluye un nombre de archivo. Sin embargo, al agregar una entrada de nombre de archivo a la plantilla de manifiesto no agrega el archivo subyacente al paquete. Debe agregar el archivo al proyecto para incluir en el paquete y establezca su propiedad de tipo de implementación en consecuencia.  
  
## <a name="see-also"></a>Vea también  
 [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Compilar y depurar soluciones de SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
  