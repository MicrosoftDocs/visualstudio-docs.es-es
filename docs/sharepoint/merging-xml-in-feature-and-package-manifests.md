---
title: "Combinar XML en manifiestos de la caracter&#237;stica y el paquete"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "desarrollo de SharePoint en Visual Studio, empaquetar"
ms.assetid: fc1cbd2a-0166-4f2f-a81b-4dac2fa7b0f3
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# Combinar XML en manifiestos de la caracter&#237;stica y el paquete
  Las características y los paquetes se definen en los archivos de manifiesto [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)].  Estos manifiestos empaquetados son una combinación de datos generada a partir de los diseñadores y el código [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] personalizado que los usuarios insertan en la plantilla de manifiesto.  Durante el empaquetado, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] combina las instrucciones [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] personalizadas con el código [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] proporcionado por el diseñador para formar el archivo de manifiesto [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] empaquetado.  Los elementos similares \(salvo las excepciones que se mencionan más adelante en Excepciones de combinación\) se combinan para evitar que se produzcan errores de validación de [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] después de implementar los archivos en SharePoint y para hacer que los archivos de manifiesto sean más pequeño y más eficaces.  
  
## Modificar los manifiestos  
 Los archivos de manifiesto empaquetados no se pueden modificar directamente hasta que los diseñadores de características o paquetes estén deshabilitados.  Sin embargo, pueden agregarse manualmente elementos [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] personalizados a la plantilla de manifiesto a través de los diseñadores de características y paquetes o del editor [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)].  Para obtener más información, vea [Cómo: Personalizar una característica de SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md) y [Cómo: Personalizar un paquete de solución de SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
## Proceso de combinación de manifiestos de características y paquetes  
 Cuando se combina un conjunto de elementos personalizados con elementos proporcionados por el diseñador, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sigue el proceso que se describe a continuación.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] comprueba si cada elemento tiene un valor de clave única.  Si un elemento no tiene ningún valor de clave única, se anexa al archivo de manifiesto empaquetado.  De igual forma, los elementos que tienen varias claves no se pueden combinar.  Por tanto, se anexan al archivo de manifiesto.  
  
 Si un elemento tiene una clave única, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] compara los valores del diseñador y de las claves personalizadas.  Si los valores coinciden, se combinan en un valor único.  Si los valores son diferentes, se descarta el valor de la clave del diseñador y se usa el valor de la clave personalizada.  Las colecciones también se combinan.  Por ejemplo, si el código [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] generado por el diseñador y el código [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] personalizado contienen una colección Assemblies, el manifiesto empaquetado contiene exclusivamente una única colección Assemblies.  
  
## Excepciones de combinación  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] combina la mayor parte de los elementos [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] del diseñador con elementos [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] personalizados similares siempre y cuando tengan un atributo único de identificación.  Sin embargo, algunos elementos no tienen el identificador único necesario para la combinación [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)].  Estos elementos se conocen como *excepciones de combinación*.  En estos casos, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] no combina los elementos [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] personalizados junto con los elementos [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] proporcionados por el diseñador; en su lugar, los anexa al archivo de manifiesto empaquetado.  
  
 A continuación se muestra una lista de excepciones de combinación de archivos de manifiesto [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] de características y paquetes.  
  
|Diseñador de|Elemento XML|  
|------------------|------------------|  
|Diseñador de características|ActivationDependency|  
|Diseñador de características|UpgradeAction|  
|Diseñador de paquetes|SafeControl|  
|Diseñador de paquetes|CodeAccessSecurity|  
  
## Elementos del manifiesto de la característica  
 En la tabla siguiente se muestra una lista de todos los elementos del manifiesto de la característica que se pueden combinar y la clave única que se usa para establecer la correspondencia.  
  
|Nombre del elemento|Clave única|  
|-------------------------|-----------------|  
|Característica \(todos los atributos\)|*Attribute Name* \(el nombre de atributo de Cada elemento de la característica es una clave única\).|  
|ElementFile|Ubicación|  
|ElementManifests\/ElementManifest|Ubicación|  
|Properties\/Property|Key|  
|CustomUpgradeAction|Name|  
|CustomUpgradeActionParameter|Name|  
  
> [!NOTE]  
>  Como el único modo de modificar el elemento CustomUpgradeAction es a través del editor [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] personalizado, los efectos que se producen al no efectuarse la combinación son mínimos.  
  
## Elementos del manifiesto del paquete  
 En la tabla siguiente se muestra una lista de todos los elementos del manifiesto del paquete que se pueden combinar y la clave única que se usa para establecer la correspondencia.  
  
|Nombre del elemento|Clave única|  
|-------------------------|-----------------|  
|Solución \(todos los atributos\)|*Attribute Name* \(el nombre de atributo de Cada elemento de la solución es una clave única\).|  
|ApplicationResourceFiles\/ApplicationResourceFile|Ubicación|  
|Assemblies\/Assembly|Ubicación|  
|ClassResources\/ClassResource|Ubicación|  
|DwpFiles\/DwpFile|Ubicación|  
|FeatureManifests\/FeatureManifest|Ubicación|  
|Resources\/Resource|Ubicación|  
|RootFiles\/RootFile|Ubicación|  
|SiteDefinitionManifests\/SiteDefinitionManifest|Ubicación|  
|WebTempFile|Ubicación|  
|TemplateFiles\/TemplateFile|Ubicación|  
|SolutionDependency|SolutionID|  
  
## Agregar archivos implementados manualmente  
 Algunos elementos del manifiesto, como ApplicationResourceFile y DwpFiles, especifican una ubicación que contiene un nombre de archivo.  Sin embargo, al agregar una entrada del nombre de archivo a la plantilla de manifiesto, no se agrega el archivo subyacente al paquete.  Este archivo debe agregarse al proyecto para incluirlo en el paquete y establecer su propiedad Deployment Type como corresponda.  
  
## Vea también  
 [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Compilar y depurar soluciones de SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
  