---
title: Variante de tamaño de la ventanilla de 1 x 1 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 3dbc3247-00f5-4644-8ff9-72e9febcf09a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0c2f97793c838316d252aa56dcadd9fbb045decf
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31472063"
---
# <a name="1x1-viewport-size-variant"></a>1x1 Viewport (Variante de tamaño)
Reduce las dimensiones de la ventanilla de todos los objetivos de presentación a 1x1 píxeles.  
  
## <a name="interpretation"></a>Interpretación  
 Una ventanilla más pequeña reduce el número de píxeles que deben sombrearse, pero no reduce el número de vértices que deben procesarse. Establecer las dimensiones de la ventanilla a 1x1 píxeles elimina eficazmente el sombreado de píxeles de la aplicación.  
  
 Si esta variante muestra un gran aumento del rendimiento, puede indicar que la aplicación consume demasiada tasa de relleno. Esto puede indicar que la resolución que ha elegido es demasiado elevada para la plataforma de destino o que la aplicación invierte demasiado tiempo en sombrear píxeles que más adelante se sobrescriben (sobredibujan). Este resultado sugiere que disminuir el tamaño del búfer de fotogramas o reducir la cantidad de sobredibujo mejorará el rendimiento de la aplicación.  
  
## <a name="remarks"></a>Comentarios  
 Las dimensiones de la ventanilla se restablecen a 1x1 píxeles después de todas las llamadas a `ID3D11DeviceContext::OMSetRenderTargets` o `ID3D11DeviceContext::RSSetViewports`.  
  
## <a name="example"></a>Ejemplo  
 Esta variante se puede reproducir con código como el siguiente:  
  
```  
D3D11_VIEWPORT viewport;  
viewport.TopLeftX = 0;  
viewport.TopLeftY = 0;  
viewport.Width = 1;  
viewport.Height = 1;  
d3d_context->RSSetViewports(1, &viewport);  
```