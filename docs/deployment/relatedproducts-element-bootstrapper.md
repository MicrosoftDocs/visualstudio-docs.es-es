---
title: '&lt;&gt;Elemento productosrelacionados (arranque) | Microsoft Docs'
description: El elemento Productosrelacionados define otros productos que dependen o que están incluidos en el producto actual.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a7987306d9f7fc25f9f9b783d5b0966ac5015ce0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949693"
---
# <a name="ltrelatedproductsgt-element-bootstrapper"></a>&lt;&gt;Elemento productosrelacionados (arranque)
El `RelatedProducts` elemento define otros productos que dependen o que están incluidos en el producto actual.

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

## <a name="elements-and-attributes"></a>Elementos y atributos
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
 En el ejemplo de código siguiente se especifica que Microsoft Installer está instalado con el .NET Framework y, por tanto, no necesitará una instalación independiente.

```xml
<RelatedProducts>
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />
</RelatedProducts>
```

## <a name="see-also"></a>Vea también
- [Elemento \<Product>](../deployment/product-element-bootstrapper.md)