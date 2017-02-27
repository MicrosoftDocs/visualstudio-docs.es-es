---
title: "&lt;RelatedProducts&gt; (Elemento, Arranque) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.MissingDependency"
  - "MSBuild.GenerateBootstrapper.DuplicateItems"
  - "MSBuild.GenerateBootstrapper.IncludedProductIncluded"
  - "MSBuild.GenerateBootstrapper.DependencyNotFound"
  - "MSBuild.GenerateBootstrapper.PackageFileNotFound"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<RelatedProducts> (elemento) [arranque]"
ms.assetid: bf152712-4c1e-48bd-9b7f-311cf0fdb832
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# &lt;RelatedProducts&gt; (Elemento, Arranque)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El elemento `RelatedProducts` define otros productos que dependen o están incluidos en el producto actual.  
  
## Sintaxis  
  
```  
<RelatedProducts>  
    <DependsOnProduct  
        Code  
    />  
    <EitherProducts>  
        <DependsOnProduct  
            Code  
        />  
    </EitherProducts>  
    <IncludesProduct  
        Code  
    />  
</RelatedProducts>  
```  
  
## Elementos y atributos  
 El elemento `RelatedProducts` es un elemento secundario del elemento `Product`.  No tiene atributos.  
  
## DependsOnProduct  
 El elemento `DependsOnProduct` significa que el producto actual depende del producto nombrado y que el producto nombrado debe instalarse antes del producto actual.  Es un elemento secundario del elemento `RelatedProducts`.  Un elemento `RelatedProducts` puede tener uno o varios elementos `DependsOnProduct`.  
  
 `DependsOnProduct` tiene el atributo siguiente.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`Code`|El nombre clave del producto incluido, como se especifica en el atributo `ProductCode` del elemento `Product`.  Para obtener más información, vea [\<Product\> \(Elemento\)](../deployment/product-element-bootstrapper.md).|  
  
## EitherProducts  
 El elemento `EitherProducts` define cero o más elementos `DependsOnProduct` y no tiene ningún atributo.  Al menos un elemento `DependsOnProduct` de este conjunto debe instalarse antes del producto actual.  Un elemento `RelatedProducts` puede tener cero o más elementos `EitherProducts`.  
  
## IncludesProduct  
 El elemento `IncludesProduct` significa que un producto está incluido con la instalación actual, y no requiere una instalación independiente.  Es un elemento secundario del elemento `RelatedProducts`.  Un elemento `RelatedProducts` puede tener uno o varios elementos `IncludesProduct`.  
  
 `IncludesProduct` tiene el atributo siguiente.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`Code`|El nombre clave del producto incluido, como se especifica en el atributo `ProductCode` del elemento `Product`.  Para obtener más información, vea [\<Product\> \(Elemento\)](../deployment/product-element-bootstrapper.md).|  
  
## Ejemplo  
 En el siguiente ejemplo de código se especifica que Microsoft Installer se instala con [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] y, por consiguiente, no necesitará una instalación independiente.  
  
```  
<RelatedProducts>  
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />  
</RelatedProducts>  
```  
  
## Vea también  
 [\<Product\> \(Elemento\)](../deployment/product-element-bootstrapper.md)