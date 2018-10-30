---
title: Variante de formato de destino de representación de 16 BPP | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 24b22ad9-5ad0-4161-809a-9b518eb924bf
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f9c72abaaf1a799316686c77b127952f1fe4f689
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49832895"
---
# <a name="16-bpp-render-target-format-variant"></a>16 bpp representar variante del formato de destino
Establece el formato de píxeles en DXGI_FORMAT_B5G6R5_UNORM para todos los objetivos de presentación y búferes de reserva.  
  
## <a name="interpretation"></a>Interpretación  
 Un destino de representación o el búfer de reserva normalmente utiliza un formato de 32 bpp (32 bits por píxel), como B8G8R8A8_UNORM. los formatos 32 bpp pueden consumir una gran cantidad de ancho de banda de memoria. Dado que el formato B5G6R5_UNORM es un formato de 16 bpp que es la mitad del tamaño de los formatos 32 bpp, utilizarlo puede aliviar la presión en ancho de banda de memoria, pero a costa de fidelidad del color.  
  
 Si esta variante muestra un gran aumento del rendimiento, puede indicar que la aplicación consume demasiado ancho de memoria. Puede obtener mejora considerable del rendimiento, especialmente cuando el fotograma perfilado tenía una cantidad importante de sobredibujo o combinación alfa.

Un formato de destino de representación de 16 bpp puede reducir la banda de memoria con un uso cuando la aplicación tiene las siguientes condiciones:
- No se requiere la reproducción del color de alta fidelidad.
- No se requiere un canal alfa.
- ¿No tiene ofent degradados suaves (que son susceptibles a los artefactos de bandas en la fidelidad del color).

Otras estrategias para reducir el ancho de banda de memoria incluyen:
- Reducir la cantidad de sobredibujo o combinación alfa.
- Reduzca las dimensiones del búfer de fotogramas.
- Reduzca las dimensiones de recursos de textura.
- Reducir compresiones de recursos de textura.
 
Como es habitual, debe tener en cuenta cómo se verá afectada la calidad de la imagen con cualquiera de estas optimizaciones.  

Las aplicaciones que forman parte de una cadena de intercambio tienen un formato de búfer de reserva (DXGI_FORMAT_B5G6R5_UNORM) que no es compatible con 16 bpp. Estas cadenas de intercambio se crean mediante `D3D11CreateDeviceAndSwapChain` o `IDXGIFactory::CreateSwapChain`. Para solucionar esta limitación, realice los pasos siguientes:
1. Crear un destino de representación formato B5G6R5_UNORM mediante `CreateTexture2D` y representar a dicho destino. 
2. Copie el destino de representación en el búfer de reserva de la cadena de intercambio dibujando un cuadrado de pantalla completa y el destino de representación como textura de origen.
3. Llamar a presente en la cadena de intercambio.

   Si esta estrategia ahorra más ancho de banda que se consume copiando el destino de representación en el búfer de reserva de la cadena de intercambio, se mejora el rendimiento de la representación.

   Las arquitecturas GPU que usan técnicas de presentación en mosaico pueden ver las ventajas de rendimiento significativas mediante el uso de un formato de búfer de fotograma de 16 bpp. Esta mejora es porque una parte más grande del búfer de fotogramas caben en la caché del búfer de fotogramas local de cada mosaico. Las arquitecturas de presentación en mosaico a veces se encuentran en GPU de auriculares móviles y tablet PC, y raramente aparecen fuera de este nicho.  
  
## <a name="remarks"></a>Comentarios  
 El formato de objetivo de presentación se restablece a DXGI_FORMAT_B5G6R5_UNORM en cada llamada a `ID3D11Device::CreateTexture2D` que crea un objetivo de presentación. En concreto, el formato se reemplaza cuando el objeto D3D11_TEXTURE2D_DESC pasado a pDesc describe un objetivo de presentación, que es:  
  
-   El miembro BindFlags tiene el conjunto de marcadores D3D11_BIND_REDNER_TARGET.  
  
-   El miembro BindFlags tiene el conjunto de marcadores D3D11_BIND_DEPTH_STENCIL borrado.  
  
-   El miembro Usage está establecido en D3D11_USAGE_DEFAULT.  
  
## <a name="restrictions-and-limitations"></a>Restricciones y limitaciones  
 Como el formato B5G6R5 no tiene ningún canal alfa, el contenido alfa no se conserva con esta variante. Si la presentación de su aplicación requiere un canal alfa en el objetivo de presentación, no puede simplemente cambiar al formato B5G6R5.  
  
## <a name="example"></a>Ejemplo  
 El **16 bpp Render Target Format** variante se puede reproducir para objetivos de presentación creados utilizando `CreateTexture2D` mediante código similar al siguiente:  
  
```cpp
D3D11_TEXTURE2D_DESC target_description;  
  
target_description.BindFlags = D3D11_BIND_RENDER_TARGET;  
target_description.Format = DXGI_FORMAT_B5G6R5_UNORM;  
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);  
```
