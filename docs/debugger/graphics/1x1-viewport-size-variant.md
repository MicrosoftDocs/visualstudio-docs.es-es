---
title: Variante de tamaño de la ventanilla 1x1 | Microsoft Docs
description: Aplique la variante de tamaño de ventanilla 1x1 para reducir las dimensiones de la ventanilla en todos los destinos de representación a 1x1 píxeles.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3dbc3247-00f5-4644-8ff9-72e9febcf09a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d1041f3a8016500a6e1f217849654d9710a508d8
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2020
ms.locfileid: "97726493"
---
# <a name="1x1-viewport-size-variant"></a>1x1 Viewport (Variante de tamaño)
Reduce las dimensiones de la ventanilla de todos los objetivos de representación a 1x1 píxeles.

## <a name="interpretation"></a>Interpretación
 Una ventanilla más pequeña reduce el número de píxeles que se deben sombrear. Sin embargo, no reduce el número de vértices que se deben procesar. Establecer las dimensiones de la ventanilla a 1x1 píxeles elimina eficazmente el sombreado de píxeles de la aplicación.

 Si esta variante muestra un gran aumento del rendimiento, puede indicar que la aplicación consume demasiada tasa de relleno. Además, la resolución podría ser demasiado alta para la plataforma de destino o la aplicación podría dedicar demasiado tiempo a sombrear píxeles que más tarde se sobrescribirán, lo que se conoce también como *sobredibujo*. Un búfer de fotogramas más pequeño o la reducción de la cantidad de sobredibujo mejorará el rendimiento de la aplicación.

## <a name="remarks"></a>Comentarios
 Las dimensiones de la ventanilla se restablecen a 1x1 píxeles después de todas las llamadas a `ID3D11DeviceContext::OMSetRenderTargets` o `ID3D11DeviceContext::RSSetViewports`.

## <a name="example"></a>Ejemplo
 Esta variante se puede reproducir con el código siguiente:

```cpp
D3D11_VIEWPORT viewport;
viewport.TopLeftX = 0;
viewport.TopLeftY = 0;
viewport.Width = 1;
viewport.Height = 1;
d3d_context->RSSetViewports(1, &viewport);
```
