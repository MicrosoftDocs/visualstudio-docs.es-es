---
title: '&lt;&gt;Elemento productosrelacionados (arranque) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 70afe724be5b782bc90e162fd65f83ad1b0d0d23
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202538"
---
# <a name="ltrelatedproductsgt-element-bootstrapper"></a>&lt;&gt;Elemento productosrelacionados (arranque)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El `RelatedProducts` elemento define otros productos que dependen o que están incluidos en el producto actual.  
  
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
  
## <a name="elements-and-attributes"></a>Atributos y elementos  
 El `RelatedProducts` elemento es un elemento secundario del `Product` elemento. No tiene atributos.  
  
## <a name="dependsonproduct"></a>DependsOnProduct  
 El `DependsOnProduct` elemento significa que el producto actual depende del producto con nombre y que el producto nombrado debe instalarse antes que el actual. Es un elemento secundario del `RelatedProducts` elemento. Un `RelatedProducts` elemento puede tener uno o más `DependsOnProduct` elementos.  
  
 `DependsOnProduct` tiene el siguiente atributo.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`Code`|Nombre de código del producto incluido, tal y como lo especifica el `ProductCode` atributo del `Product` elemento. Para obtener más información, consulte [Elemento \<Product>](../deployment/product-element-bootstrapper.md).|  
  
## <a name="eitherproducts"></a>EitherProducts  
 El `EitherProducts` elemento define cero o más `DependsOnProduct` elementos y no tiene atributos. Al menos un `DependsOnProduct` de este conjunto debe instalarse antes que el producto actual. Un `RelatedProducts` elemento puede tener cero o más `EitherProducts` elementos.  
  
## <a name="includesproduct"></a>IncludesProduct  
 El `IncludesProduct` elemento significa que un producto está incluido en la instalación actual y no requiere una instalación independiente. Es un elemento secundario del `RelatedProducts` elemento. Un `RelatedProducts` elemento puede tener uno o más `IncludesProduct` elementos.  
  
 `IncludesProduct` tiene el siguiente atributo.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`Code`|Nombre de código del producto incluido, tal y como lo especifica el `ProductCode` atributo del `Product` elemento. Para obtener más información, consulte [Elemento \<Product>](../deployment/product-element-bootstrapper.md).|  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se especifica que Microsoft Installer se instala con [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] y, por lo tanto, no necesitará una instalación independiente.  
  
```  
<RelatedProducts>  
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />  
</RelatedProducts>  
```  
  
## <a name="see-also"></a>Consulte también  
 [Elemento \<Product>](../deployment/product-element-bootstrapper.md)
