---
title: '&lt;RelatedProducts&gt; (elemento, arranque) | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
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
helpviewer_keywords:
- <RelatedProducts> element [bootstrapper]
ms.assetid: bf152712-4c1e-48bd-9b7f-311cf0fdb832
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: ee65c4e4cacd4680256e34583559d74935a89e3b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47567115"
---
# <a name="ltrelatedproductsgt-element-bootstrapper"></a>&lt;RelatedProducts&gt; (elemento, arranque)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [ &lt;Productosrelacionados&gt; (elemento, arranque)](https://docs.microsoft.com/visualstudio/deployment/relatedproducts-element-bootstrapper).  
  
El `RelatedProducts` elemento define otros productos que dependen o se incluyen en el producto actual.  
  
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
 El `RelatedProducts` es un elemento secundario de la `Product` elemento. No tiene atributos.  
  
## <a name="dependsonproduct"></a>DependsOnProduct  
 El `DependsOnProduct` elemento significa que el producto actual depende el producto designado, y que el producto designado debe instalarse antes que el actual. Es un elemento secundario de la `RelatedProducts` elemento. Un `RelatedProducts` elemento puede tener uno o varios `DependsOnProduct` elementos.  
  
 `DependsOnProduct` tiene el siguiente atributo.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`Code`|El nombre de código del producto incluido, según lo especificado por el `ProductCode` atributo de la `Product` elemento. Para obtener más información, consulte [ \<producto > elemento](../deployment/product-element-bootstrapper.md).|  
  
## <a name="eitherproducts"></a>EitherProducts  
 El `EitherProducts` elemento define cero o más `DependsOnProduct` elementos, y no tiene atributos. Al menos un `DependsOnProduct` debe estar instalado en este conjunto antes del producto actual. Un `RelatedProducts` elemento puede tener cero o más `EitherProducts` elementos.  
  
## <a name="includesproduct"></a>IncludesProduct  
 El `IncludesProduct` elemento significa que un producto se incluye con la instalación actual y no requiere una instalación independiente. Es un elemento secundario de la `RelatedProducts` elemento. Un `RelatedProducts` elemento puede tener uno o varios `IncludesProduct` elementos.  
  
 `IncludesProduct` tiene el siguiente atributo.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`Code`|El nombre de código del producto incluido, según lo especificado por el `ProductCode` atributo de la `Product` elemento. Para obtener más información, consulte [ \<producto > elemento](../deployment/product-element-bootstrapper.md).|  
  
## <a name="example"></a>Ejemplo  
 El ejemplo de código siguiente especifica que Microsoft Installer se instala con el [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]y por lo tanto, no necesitará una instalación independiente.  
  
```  
<RelatedProducts>  
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />  
</RelatedProducts>  
```  
  
## <a name="see-also"></a>Vea también  
 [\<Producto > elemento](../deployment/product-element-bootstrapper.md)



