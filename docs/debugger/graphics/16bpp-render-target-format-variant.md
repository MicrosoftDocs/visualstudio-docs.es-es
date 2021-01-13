---
title: Variante de formato de destino de la presentación 16 bpp| Microsoft Docs
description: Aplique la variante de formato de destino de representación de 16 bits por píxel (bpp) estableciendo el formato de píxel en DXGI_FORMAT_B5G6R5_UNORM para todos los destinos de representación y los búferes de reserva.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 24b22ad9-5ad0-4161-809a-9b518eb924bf
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aa73637244469d781ac77acba362886b5656f8d8
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728049"
---
# <a name="16-bpp-render-target-format-variant"></a>Variante de formato de destino de la presentación 16 bpp
Establece el formato de píxeles en DXGI_FORMAT_B5G6R5_UNORM para todos los objetivos de presentación y búferes de reserva.

## <a name="interpretation"></a>Interpretación
 Un destino de presentación o búfer de reserva normalmente usa un formato de 32 bpp (32 bits por píxel), como B8G8R8A8_UNORM. Los formatos de 32 bpp pueden consumir una gran cantidad de ancho de banda de memoria. Como B5G6R5_UNORM es un formato de 16 bpp, que es la mitad del tamaño de los formatos 32 bpp, su uso puede reducir la presión en el ancho de banda de memoria, pero a costa de perder fidelidad del color.

 Si esta variante muestra un gran aumento del rendimiento, puede indicar que la aplicación consume demasiado ancho de memoria. Puede obtener una mejora significativa en el rendimiento, especialmente cuando el fotograma para el que se generan perfiles tenía una cantidad significativa de sobredibujo o combinación alfa.

Un formato de destino de representación de 16 bpp puede reducir la banda de memoria con uso cuando la aplicación tiene las condiciones siguientes:
- No requiere reproducción de color de alta fidelidad.
- No requiere un canal alfa.
- No suele tener degradados suaves (que son susceptibles a artefactos de bandas con fidelidad de color reducida).

Otras estrategias para reducir el ancho de banda de memoria incluyen las siguientes:
- Reducir la cantidad de sobredibujo o combinación alfa.
- Reducir las dimensiones del búfer de fotogramas.
- Reducir las dimensiones de los recursos de textura.
- Reducir las compresiones de los recursos de textura.

Como es habitual, debe tener en cuenta cómo se verá afectada la calidad de la imagen con cualquiera de estas optimizaciones.

Las aplicaciones que forman parte de una cadena de intercambio tienen un formato de búfer de reserva (DXGI_FORMAT_B5G6R5_UNORM) que no admite 16 bpp. Estas cadenas de intercambio se crean mediante `D3D11CreateDeviceAndSwapChain` o `IDXGIFactory::CreateSwapChain`. Para superar esta limitación, siga estos pasos:
1. Cree un destino de representación de formato B5G6R5_UNORM mediante `CreateTexture2D` y realice la presentación en ese destino.
2. Copie el destino de representación en el búfer de reserva de la cadena de intercambio dibujando un cuadrilátero a pantalla completa con el destino de representación como textura de origen.
3. Llame a Present en la cadena de intercambio.

   Si esta estrategia ahorra más ancho de banda que el que se consume al copiar el destino de representación en el búfer de reserva de la cadena de intercambio, se mejora el rendimiento de la representación.

   Las arquitecturas de GPU que usan técnicas de representación en mosaico pueden experimentar ventajas de rendimiento significativas si se usa un formato de búfer de fotogramas de 16 bpp. Esta mejora se debe a que una mayor parte del búfer de fotogramas puede caber en la caché del búfer de fotogramas local de cada icono. Las arquitecturas de presentación en mosaico a veces se encuentran en GPU de auriculares móviles y tablet PC, y raramente aparecen fuera de este nicho.

## <a name="remarks"></a>Comentarios
 El formato de objetivo de presentación se restablece a DXGI_FORMAT_B5G6R5_UNORM en cada llamada a `ID3D11Device::CreateTexture2D` que crea un objetivo de presentación. En concreto, el formato se reemplaza cuando el objeto D3D11_TEXTURE2D_DESC pasado a pDesc describe un objetivo de presentación, que es:

- El miembro BindFlags tiene el conjunto de marcadores D3D11_BIND_REDNER_TARGET.

- El miembro BindFlags tiene el conjunto de marcadores D3D11_BIND_DEPTH_STENCIL borrado.

- El miembro Usage está establecido en D3D11_USAGE_DEFAULT.

## <a name="restrictions-and-limitations"></a>Restricciones y limitaciones
 Como el formato B5G6R5 no tiene ningún canal alfa, el contenido alfa no se conserva con esta variante. Si la presentación de su aplicación requiere un canal alfa en el objetivo de presentación, no puede simplemente cambiar al formato B5G6R5.

## <a name="example"></a>Ejemplo
 La variante **Formato de destino de representación de 16 bpp** se puede reproducir para destinos de representación creados mediante `CreateTexture2D` con código como el siguiente:

```cpp
D3D11_TEXTURE2D_DESC target_description;

target_description.BindFlags = D3D11_BIND_RENDER_TARGET;
target_description.Format = DXGI_FORMAT_B5G6R5_UNORM;
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);
```
