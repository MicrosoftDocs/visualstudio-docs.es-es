---
title: '&lt;RelatedProducts&gt; elemento (arranque) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MSBuild.GenerateBootstrapper.MissingDependency
- MSBuild.GenerateBootstrapper.DuplicateItems
- MSBuild.GenerateBootstrapper.IncludedProductIncluded
- MSBuild.GenerateBootstrapper.DependencyNotFound
- MSBuild.GenerateBootstrapper.PackageFileNotFound
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords: <RelatedProducts> element [bootstrapper]
ms.assetid: bf152712-4c1e-48bd-9b7f-311cf0fdb832
caps.latest.revision: "12"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 4fa304f787c954b9ee89878e792e6f543f344f60
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="ltrelatedproductsgt-element-bootstrapper"></a>&lt;RelatedProducts&gt; elemento (arranque)
El `RelatedProducts` elemento define otros productos que dependen o que se incluyen en el producto actual.  
  
## <a name="syntax"></a>Sintaxis  
  
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
  
## <a name="elements-and-attributes"></a>Elementos y atributos  
 El `RelatedProducts` es un elemento secundario de la `Product` elemento. No tiene ningún atributo.  
  
## <a name="dependsonproduct"></a>DependsOnProduct  
 El `DependsOnProduct` elemento significa que el producto actual depende del producto con nombre, y que el producto designado debe instalarse antes que el actual. Es un elemento secundario de la `RelatedProducts` elemento. A `RelatedProducts` elemento puede tener uno o varios `DependsOnProduct` elementos.  
  
 `DependsOnProduct`tiene el siguiente atributo.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`Code`|El nombre de código del producto incluido, según lo especificado por el `ProductCode` atributo de la `Product` elemento. Para obtener más información, consulte [ \<producto > elemento](../deployment/product-element-bootstrapper.md).|  
  
## <a name="eitherproducts"></a>EitherProducts  
 El `EitherProducts` elemento define cero o más `DependsOnProduct` elementos, y no tiene atributos. Al menos un `DependsOnProduct` en este conjunto debe instalarse antes del producto actual. A `RelatedProducts` elemento puede tener cero o más `EitherProducts` elementos.  
  
## <a name="includesproduct"></a>IncludesProduct  
 El `IncludesProduct` elemento significa que un producto se incluye con la instalación actual y no requiere una instalación independiente. Es un elemento secundario de la `RelatedProducts` elemento. A `RelatedProducts` elemento puede tener uno o varios `IncludesProduct` elementos.  
  
 `IncludesProduct`tiene el siguiente atributo.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`Code`|El nombre de código del producto incluido, según lo especificado por el `ProductCode` atributo de la `Product` elemento. Para obtener más información, consulte [ \<producto > elemento](../deployment/product-element-bootstrapper.md).|  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se especifica que Microsoft Installer se instala con la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]y, por tanto, no necesitará una instalación independiente.  
  
```  
<RelatedProducts>  
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />  
</RelatedProducts>  
```  
  
## <a name="see-also"></a>Vea también  
 [\<Producto > elemento](../deployment/product-element-bootstrapper.md)