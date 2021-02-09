---
title: Combinar XML en manifiestos de características y paquetes | Microsoft Docs
description: Código XML generado por el diseñador de mezcla y agregado por el usuario en los manifiestos de características y paquetes de SharePoint. Obtenga información sobre los elementos de manifiesto de paquetes y características, y las excepciones de combinación.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packaging
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8be6adfedeabaea236e4dcb2cd969e6023a7f3ec
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889569"
---
# <a name="merge-xml-in-feature-and-package-manifests"></a>Combinar XML en manifiestos de características y paquetes
  Las características y los paquetes se definen mediante [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] archivos de manifiesto. Estos manifiestos empaquetados son una combinación de datos generada a partir de diseñadores y [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] que los usuarios han escrito en la plantilla de manifiesto. En el tiempo de empaquetado, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] combina las [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] instrucciones personalizadas con el diseñador proporcionado [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] para formar el archivo de [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] manifiesto empaquetado. Los elementos similares, con las excepciones que se indican más adelante en las excepciones de combinación, se combinan para evitar [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] errores de validación después de implementar los archivos en SharePoint y para que los archivos de manifiesto sean más pequeños y eficientes.

## <a name="modify-the-manifests"></a>Modificar los manifiestos
 No se pueden modificar directamente los archivos de manifiesto empaquetado hasta que se deshabiliten los diseñadores de características o paquetes. Sin embargo, puede Agregar manualmente [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] elementos personalizados a la plantilla de manifiesto a través de los diseñadores de características y paquetes o el [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] Editor. Para obtener más información, vea [Cómo: personalizar una característica de SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md) y [Cómo: personalizar un paquete de solución de SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

## <a name="feature-and-package-manifest-merge-process"></a>Proceso de combinación del manifiesto de la característica y el paquete
 Cuando se combinan elementos personalizados junto con elementos proporcionados por el diseñador, se [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] utiliza el siguiente proceso. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] comprueba si cada elemento tiene un valor de clave único. Si un elemento no tiene ningún valor de clave única, se anexa al archivo de manifiesto empaquetado. De igual forma, los elementos que tienen varias claves no se pueden combinar. Por lo tanto, se anexan al archivo de manifiesto.

 Si un elemento tiene una clave única, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] compara los valores del diseñador y las claves personalizadas. Si los valores coinciden, se combinan en un único valor. Si los valores difieren, se descarta el valor de clave del diseñador y se usa el valor de clave personalizada. También se combinan las colecciones. Por ejemplo, si el diseñador generado [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] y el personalizado [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] contienen una colección de ensamblados, el manifiesto empaquetado contiene solo una colección de ensamblados.

## <a name="merge-exceptions"></a>Excepciones de combinación
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] combina la mayoría de [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] los elementos del diseñador junto con elementos personalizados similares siempre que [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] tengan un único atributo de identificación único. Sin embargo, algunos elementos no tienen el identificador único necesario para la [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] combinación. Estos elementos se conocen como *excepciones de combinación*. En estos casos, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] no combina los elementos personalizados [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] junto con los elementos proporcionados por el diseñador [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] , sino que los anexa al archivo de manifiesto empaquetado.

 A continuación se muestra una lista de excepciones de combinación para los archivos de manifiesto de características y paquetes [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] .

|Diseñador|Elemento XML|
|--------------|-----------------|
|Diseñador de características|ActivationDependency|
|Diseñador de características|UpgradeAction|
|Diseñador de paquetes|SafeControl|
|Diseñador de paquetes|CodeAccessSecurity|

## <a name="feature-manifest-elements"></a>Elementos del manifiesto de características
 En la tabla siguiente se muestra una lista de todos los elementos de manifiesto de características que se pueden combinar y su clave única que se utiliza para buscar coincidencias.

|Nombre del elemento|Clave única|
|------------------|----------------|
|Característica (todos los atributos)|*Nombre del atributo* (cada nombre de atributo del elemento de característica es una clave única).|
|ElementFile|Location|
|ElementManifests/ElementManifest|Location|
|Propiedades/propiedad|Key|
|CustomUpgradeAction|Nombre|
|CustomUpgradeActionParameter|Nombre|

> [!NOTE]
> Dado que la única manera de modificar el elemento CustomUpgradeAction es en el [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] editor personalizado, el efecto de no combinar es bajo.

## <a name="package-manifest-elements"></a>Elementos del manifiesto del paquete
 En la tabla siguiente se muestra una lista de todos los elementos de manifiesto de paquete que se pueden combinar y su clave única que se utiliza para la búsqueda de coincidencias.

|Nombre del elemento|Clave única|
|------------------|----------------|
|Solución (todos los atributos)|*Nombre del atributo* (cada nombre de atributo del elemento de solución es una clave única).|
|ApplicationResourceFiles/ApplicationResourceFile|Location|
|Ensamblados/ensamblado|Location|
|ClassResources/ClassResource|Location|
|DwpFiles/DwpFile|Location|
|FeatureManifests/FeatureManifest|Location|
|Recursos/recurso|Location|
|RootFiles/RootFile|Location|
|SiteDefinitionManifests/SiteDefinitionManifest|Location|
|WebTempFile|Location|
|TemplateFiles/TemplateFile|Location|
|SolutionDependency|SolutionID|

## <a name="manually-add-deployed-files"></a>Agregar manualmente los archivos implementados
 Algunos elementos del manifiesto, como ApplicationResourceFile y DwpFiles, especifican una ubicación que incluye un nombre de archivo. Sin embargo, si se agrega una entrada de nombre de archivo a la plantilla de manifiesto, no se agrega el archivo subyacente al paquete. Debe agregar el archivo al proyecto para incluirlo en el paquete y establecer su propiedad tipo de implementación en consecuencia.

## <a name="see-also"></a>Vea también
- [Empaquetado e implementación de soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
- [Build and debug SharePoint solutions](../sharepoint/building-and-debugging-sharepoint-solutions.md) (Compilar y depurar las soluciones de SharePoint)
