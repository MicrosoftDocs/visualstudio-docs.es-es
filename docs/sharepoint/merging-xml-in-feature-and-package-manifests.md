---
title: Manifiestos de la combinación de XML en paquetes y características | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packaging
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e3697fe85d13e1131c58f28d572e443affa77a81
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54875568"
---
# <a name="merge-xml-in-feature-and-package-manifests"></a>Combinar XML en manifiestos de características y paquetes
  Las características y los paquetes se definen mediante [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] los archivos de manifiesto. Estos manifiestos empaquetados son una combinación de datos generados a partir de los diseñadores y personalizado [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] especificados en la plantilla de manifiesto por los usuarios. Durante el empaquetado, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] combina personalizado [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] instrucciones con proporcionados por el diseñador [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] para formar el empaquetado [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] archivo de manifiesto. Elementos similares, con las excepciones que se indica más adelante en excepciones de combinación se combinan para evitar [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] errores de validación después de implementar los archivos en SharePoint y para realizar el manifiesto de archivos más pequeño y eficaz.  
  
## <a name="modify-the-manifests"></a>Modificar los manifiestos
 No se puede modificar directamente los archivos de manifiesto empaquetados hasta que deshabilite a los diseñadores de característica o paquete. Sin embargo, puede agregar manualmente personalizado [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] elementos a la plantilla de manifiesto ya sea a través de los diseñadores de paquetes y características o [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] editor. Para obtener más información, vea [Cómo: Personalizar una característica de SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md) y [Cómo: Personalizar un paquete de solución SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
## <a name="feature-and-package-manifest-merge-process"></a>Proceso de mezcla de manifiesto de características y paquetes
 Al combinar los elementos personalizados junto con los elementos proporcionados por el diseñador, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] utiliza el siguiente proceso. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] comprueba si cada elemento tiene un valor de clave única. Si un elemento no tiene ningún valor de clave única, se anexa al archivo de manifiesto empaquetado. De forma similar, no se pueden combinar los elementos que tienen varias claves. Por lo tanto, se anexan al archivo de manifiesto.  
  
 Si un elemento tiene una clave única, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] compara los valores del diseñador y de las claves personalizadas. Si los valores coinciden, se combinan en un solo valor. Si los valores difieren, se descarta el valor de clave de diseñador y se usa el valor de clave personalizado. También se combinan las colecciones. Por ejemplo, si el diseñador genera [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] y personalizado [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] ambas contienen una colección de ensamblados, el manifiesto empaquetado contiene sólo una colección de ensamblados.  
  
## <a name="merge-exceptions"></a>Combinar excepciones
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] combina la mayoría de diseñador [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] elementos junto con personalizado similar [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] elementos siempre y cuando tengan un atributo de identificación único. Sin embargo, algunos elementos no tienen el identificador único necesario para [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] combinación. Estos elementos se conocen como *mezcla excepciones*. En estos casos, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] no combina personalizado [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] elementos junto con los proporcionados por el diseñador [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] elementos, pero en su lugar, se anexa al archivo de manifiesto empaquetado.  
  
 La siguiente es una lista de excepciones de la combinación de características y paquetes [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] los archivos de manifiesto.  
  
|Diseñador|Elemento XML|  
|--------------|-----------------|  
|Diseñador de características|ActivationDependency|  
|Diseñador de características|UpgradeAction|  
|Diseñador de paquetes|SafeControl|  
|Diseñador de paquetes|CodeAccessSecurity|  
  
## <a name="feature-manifest-elements"></a>Elementos del manifiesto de característica
 En la tabla siguiente es una lista de todos los elementos de manifiesto de característica que se pueden combinar y la clave única que se usa para la coincidencia.  
  
|Nombre del elemento|Clave única|  
|------------------|----------------|  
|Característica (todos los atributos)|*Nombre del atributo* (cada nombre de atributo del elemento de característica es una clave única).|  
|ElementFile|Ubicación|  
|ElementManifests/ElementManifest|Ubicación|  
|Las propiedades o propiedad|Key|  
|CustomUpgradeAction|nombre|  
|CustomUpgradeActionParameter|nombre|  
  
> [!NOTE]  
>  Dado que es la única manera de modificar el elemento CustomUpgradeAction en personalizado [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] editor, el efecto de combinar no es bajo.  
  
## <a name="package-manifest-elements"></a>Elementos del manifiesto del paquete
 En la tabla siguiente es una lista de todos los elementos de manifiesto de paquete que se pueden combinar y la clave única que se usa para la coincidencia.  
  
|Nombre del elemento|Clave única|  
|------------------|----------------|  
|Solución (todos los atributos)|*Nombre del atributo* (cada nombre de atributo del elemento de solución es una clave única).|  
|ApplicationResourceFiles/ApplicationResourceFile|Ubicación|  
|Ensamblados y ensamblado|Ubicación|  
|ClassResources/ClassResource|Ubicación|  
|DwpFiles/DwpFile|Ubicación|  
|FeatureManifests/FeatureManifest|Ubicación|  
|Los recursos o recurso|Ubicación|  
|RootFiles/RootFile|Ubicación|  
|SiteDefinitionManifests/SiteDefinitionManifest|Ubicación|  
|WebTempFile|Ubicación|  
|TemplateFiles/TemplateFile|Ubicación|  
|SolutionDependency|SolutionID|  
  
## <a name="manually-add-deployed-files"></a>Agregar manualmente los archivos implementados
 Algunos elementos del manifiesto, como ApplicationResourceFile y DwpFiles, especifican una ubicación que incluye un nombre de archivo. Sin embargo, agregar una entrada de nombre de archivo a la plantilla de manifiesto no agrega el archivo subyacente al paquete. Debe agregar el archivo al proyecto para incluirlo en el paquete y establezca su propiedad de tipo de implementación en consecuencia.  
  
## <a name="see-also"></a>Vea también
 [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Build and debug SharePoint solutions](../sharepoint/building-and-debugging-sharepoint-solutions.md) (Compilar y depurar las soluciones de SharePoint)  
