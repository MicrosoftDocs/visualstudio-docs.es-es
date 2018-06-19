---
title: Variante de formato de destino de representación de 16 BPP | Documentos de Microsoft
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
ms.openlocfilehash: e8f8328b180c398cab5ff7fa0f29dfc578414e3a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31474864"
---
# <a name="16bpp-render-target-format-variant"></a>16bpp (Representar variante de formato de destino)
Establece el formato de píxeles en DXGI_FORMAT_B5G6R5_UNORM para todos los objetivos de presentación y búferes de reserva.  
  
## <a name="interpretation"></a>Interpretación  
 Un objetivo de presentación o búfer de reserva normalmente utiliza un formato de 32 bpp (32 bits por píxel), como B8G8R8A8_UNORM. Los formatos de 32 bpp pueden consumir mucho ancho de banda de memoria. Como el formato B5G6R5_UNORM es un formato de 16 bpp, que es la mitad del tamaño de los formatos 32 bpp, utilizarlo puede reducir la presión en el ancho de banda de memoria, pero a costa de perder fidelidad del color.  
  
 Si esta variante muestra un gran aumento del rendimiento, puede indicar que la aplicación consume demasiado ancho de memoria. Los aumentos del rendimiento pueden ser especialmente pronunciados cuando el fotograma perfilado sufre una cantidad importante de sobredibujo o contiene mucha combinación alfa.  
  
 Si los tipos de escena que la aplicación presenta no requieren una alta fidelidad en la reproducción del color, ni que el objetivo de presentación tenga un canal alfa y a menudo contienen degradados suaves, que son susceptibles a los artefactos de banda en poca fidelidad del color, considere utilizar un formato de objetivo de presentación de 16 bpp para reducir el uso de ancho de banda de memoria.  
  
 Si las escenas que se presentan en su aplicación requieren la reproducción del color de alta fidelidad o un canal alfa, o los degradados suaves son habituales, considere otras estrategias para reducir el uso de ancho de banda de memoria, como, por ejemplo, reducir la cantidad de sobredibujo o combinación alfa, reducir las dimensiones del búfer de fotograma o modificar los recursos de textura para consumir menos ancho de banda de memoria habilitando la compresión o reduciendo sus dimensiones. Como es habitual, debe tener en cuenta cómo se verá afectada la calidad de la imagen con cualquiera de estas optimizaciones.  
  
 Si su aplicación se pudiese beneficiar de cambiar a un búfer de reserva de 16 bpp pero forma parte de su cadena de intercambio, debe tomar medidas adicionales, porque DXGI_FORMAT_B5G6R5_UNORM no es un formato de búfer de reserva admitido para cadenas de intercambio creadas mediante `D3D11CreateDeviceAndSwapChain` o `IDXGIFactory::CreateSwapChain`. En su lugar, debe crear un objetivo de presentación de formato B5G6R5_UNORM mediante `CreateTexture2D` y presentarlo a este. Entonces, antes de llamar a Presente en la cadena de intercambio, copie el objetivo de presentación en el búfer de reserva de la cadena de intercambio dibujando un cuadrilátero a pantalla completa con el objetivo de presentación como textura de origen. Aunque este es un paso adicional que consumirá algo de ancho de banda de memoria, la mayoría de las operaciones de presentación consumirán menos ancho de banda, porque afectan al objetivo de presentación de 16 bpp. Si esto ahorra más ancho de banda de la que se consume copiando el objetivo de presentación al búfer de reserva de cadena de intercambio, el rendimiento de la presentación mejora.  
  
 Las arquitecturas de GPU que utilizan técnicas de presentación en mosaico pueden obtener unos beneficios significativos en el rendimiento utilizando un formato de búfer de fotograma de 16 bpp, porque una parte más grande del búfer de fotograma puede encajar en cada caché de búfer de fotogramas local del mosaico. Las arquitecturas de presentación en mosaico a veces se encuentran en GPU de auriculares móviles y tablet PC, y raramente aparecen fuera de este nicho.  
  
## <a name="remarks"></a>Comentarios  
 El formato de objetivo de presentación se restablece a DXGI_FORMAT_B5G6R5_UNORM en cada llamada a `ID3D11Device::CreateTexture2D` que crea un objetivo de presentación. En concreto, el formato se reemplaza cuando el objeto D3D11_TEXTURE2D_DESC pasado a pDesc describe un objetivo de presentación, que es:  
  
-   El miembro BindFlags tiene el conjunto de marcadores D3D11_BIND_REDNER_TARGET.  
  
-   El miembro BindFlags tiene el conjunto de marcadores D3D11_BIND_DEPTH_STENCIL borrado.  
  
-   El miembro Usage está establecido en D3D11_USAGE_DEFAULT.  
  
## <a name="restrictions-and-limitations"></a>Restricciones y limitaciones  
 Como el formato B5G6R5 no tiene ningún canal alfa, el contenido alfa no se conserva con esta variante. Si la presentación de su aplicación requiere un canal alfa en el objetivo de presentación, no puede simplemente cambiar al formato B5G6R5.  
  
## <a name="example"></a>Ejemplo  
 El **16bpp Render Target Format** variante se puede reproducir para objetivos de presentación creados utilizando `CreateTexture2D` mediante código similar al siguiente:  
  
```  
D3D11_TEXTURE2D_DESC target_description;  
  
target_description.BindFlags = D3D11_BIND_RENDER_TARGET;  
target_description.Format = DXGI_FORMAT_B5G6R5_UNORM;  
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);  
```