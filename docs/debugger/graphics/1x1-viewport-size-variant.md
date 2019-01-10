---
title: Variante de tamaño de la ventanilla 1 x 1 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3dbc3247-00f5-4644-8ff9-72e9febcf09a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e27383fc51c6c49ddabc9be0d59f68aa5ec9c896
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53990823"
---
# <a name="1x1-viewport-size-variant"></a>1x1 Viewport (Variante de tamaño)
Reduce las dimensiones de la ventanilla de todos los objetivos de presentación a 1x1 píxeles.  
  
## <a name="interpretation"></a>Interpretación  
 Una ventanilla más pequeña reduce el número de píxeles que se deben sombrear. Sin embargo, una ventanilla más pequeña no reduce el número de vértices que se deben proceso. Establecer las dimensiones de la ventanilla a 1x1 píxeles elimina eficazmente el sombreado de píxeles de la aplicación.  
  
 Si esta variante muestra un gran aumento del rendimiento, podría indicar que la aplicación consume demasiada tasa de relleno. Además, la solución podría ser demasiado alto para la plataforma de destino o la aplicación podría dedicar mucho tiempo en sombrear píxeles que más adelante se sobrescriben, también conocidos como *sobredibujan*. Un búfer de fotogramas más pequeño o reducir la cantidad de sobredibujo mejorará el rendimiento de la aplicación.  
  
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
