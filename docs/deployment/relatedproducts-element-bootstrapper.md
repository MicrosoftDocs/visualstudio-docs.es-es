---
title: '&lt;RelatedProducts&gt; (elemento, arranque) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c541a9775025183a3b3ffbf21ef5b72c3f00cc87
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2018
ms.locfileid: "39077815"
---
# <a name="ltrelatedproductsgt-element-bootstrapper"></a>&lt;RelatedProducts&gt; (elemento, arranque)
El `RelatedProducts` elemento define otros productos que dependen o se incluyen en el producto actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
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
  
## <a name="elements-and-attributes"></a>Los elementos y atributos  
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
 El ejemplo de código siguiente especifica que Microsoft Installer se instala con el [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]y por lo tanto, no necesitará una instalación independiente.  
  
```xml  
<RelatedProducts>  
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />  
</RelatedProducts>  
```  
  
## <a name="see-also"></a>Vea también  
 [\<Producto > elemento](../deployment/product-element-bootstrapper.md)