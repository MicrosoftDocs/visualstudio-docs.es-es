---
title: Variante de formato de destino de representación 16 BPP | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 24b22ad9-5ad0-4161-809a-9b518eb924bf
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a63261a4ef8a6304bec8c2bdde1d9ec9113405e
ms.sourcegitcommit: 8530d15aa72fe058ee3a3b4714c36b8638f8b494
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2019
ms.locfileid: "74188593"
---
# <a name="16-bpp-render-target-format-variant"></a>Variante del formato de destino de representación de 16 BPP
Establece el formato de píxeles en DXGI_FORMAT_B5G6R5_UNORM para todos los objetivos de presentación y búferes de reserva.

## <a name="interpretation"></a>Interpretación
 Un destino de representación o búfer de reserva normalmente usa un formato 32 bpp (32 bits por píxel) como B8G8R8A8_UNORM. los formatos de 32-bpp pueden consumir una gran cantidad de ancho de banda de memoria. Dado que el formato de B5G6R5_UNORM es un formato de 16 BPP que es la mitad del tamaño de los formatos 32-bpp, el uso puede aliviar la presión del ancho de banda de memoria, pero a costa de una fidelidad de color reducida.

 Si esta variante muestra un gran aumento del rendimiento, puede indicar que la aplicación consume demasiado ancho de memoria. Puede obtener una mejora significativa en el rendimiento, especialmente cuando el fotograma de la que se generan perfiles tenía una cantidad significativa de sobredibujo o de mezcla alfa.

Un formato de destino de representación de 16 BPP puede reducir la banda de memoria con uso cuando la aplicación tiene las siguientes condiciones:
- No requiere reproducción de color de alta fidelidad.
- No requiere un canal alfa.
- A menudo, no tienen degradados suaves (que son susceptibles a los artefactos de bandas con fidelidad de color reducida).

Otras estrategias para reducir el ancho de banda de memoria incluyen:
- Reduzca la cantidad de sobredibujo o la combinación alfa.
- Reduzca las dimensiones del búfer de fotogramas.
- Reduce las dimensiones de los recursos de textura.
- Reduzca las compresiones de los recursos de textura.

Como es habitual, debe tener en cuenta cómo se verá afectada la calidad de la imagen con cualquiera de estas optimizaciones.

Las aplicaciones que forman parte de una cadena de intercambio tienen un formato de búfer de reserva (DXGI_FORMAT_B5G6R5_UNORM) que no es compatible con 16 BPP. Estas cadenas de intercambio se crean mediante `D3D11CreateDeviceAndSwapChain` o `IDXGIFactory::CreateSwapChain`. Para solucionar esta limitación, realice los pasos siguientes:
1. Cree un destino de representación de formato B5G6R5_UNORM mediante `CreateTexture2D` y represente en ese destino.
2. Copie el destino de representación en el búfer de reserva de la cadena de intercambio dibujando un cuádruple de pantalla completa con el destino de representación como textura de origen.
3. Llame a presente en la cadena de intercambio.

   Si esta estrategia guarda más ancho de banda que el consumido al copiar el destino de representación en el búfer de intercambio de cadena de intercambio, se mejora el rendimiento de la representación.

   Las arquitecturas de GPU que usan técnicas de representación en mosaico pueden ver ventajas de rendimiento significativas mediante el uso de un formato de búfer de marcos de 16 BPP. Esta mejora se debe a que una parte más grande del búfer de fotogramas puede caber en la memoria caché del búfer de fotogramas local de cada icono. Las arquitecturas de presentación en mosaico a veces se encuentran en GPU de auriculares móviles y tablet PC, y raramente aparecen fuera de este nicho.

## <a name="remarks"></a>Comentarios
 El formato de objetivo de presentación se restablece a DXGI_FORMAT_B5G6R5_UNORM en cada llamada a `ID3D11Device::CreateTexture2D` que crea un objetivo de presentación. En concreto, el formato se reemplaza cuando el objeto D3D11_TEXTURE2D_DESC pasado a pDesc describe un objetivo de presentación, que es:

- El miembro BindFlags tiene el conjunto de marcadores D3D11_BIND_REDNER_TARGET.

- El miembro BindFlags tiene el conjunto de marcadores D3D11_BIND_DEPTH_STENCIL borrado.

- El miembro Usage está establecido en D3D11_USAGE_DEFAULT.

## <a name="restrictions-and-limitations"></a>Restricciones y limitaciones
 Como el formato B5G6R5 no tiene ningún canal alfa, el contenido alfa no se conserva con esta variante. Si la presentación de su aplicación requiere un canal alfa en el objetivo de presentación, no puede simplemente cambiar al formato B5G6R5.

## <a name="example"></a>Ejemplo
 La variante de **formato de destino de representación de 16 BPP** se puede reproducir para los destinos de representación creados mediante el uso de `CreateTexture2D` mediante código como el siguiente:

```cpp
D3D11_TEXTURE2D_DESC target_description;

target_description.BindFlags = D3D11_BIND_RENDER_TARGET;
target_description.Format = DXGI_FORMAT_B5G6R5_UNORM;
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);
```
