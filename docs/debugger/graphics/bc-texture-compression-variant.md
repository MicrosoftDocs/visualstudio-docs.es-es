---
title: Variante de compresión de textura BC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2d0f5305-585b-4b01-bc9a-7a32d6e991da
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5faf19632d746105deed3a36af6943627594175
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736159"
---
# <a name="bc-texture-compression-variant"></a>BC (Variante de compresión de textura)
Habilita la compresión de bloque en todas las texturas que tengan una variante de formato de píxel de B8G8R8X8, B8G8R8A8 o R8G8B8A8.

## <a name="interpretation"></a>Interpretación
 Los formatos de compresión basados en bloque, como BC1, BC2 y BC3, ocupan mucha menos memoria que los formatos de imagen sin comprimir y, por lo tanto, consumen mucho menos ancho de banda de memoria. En comparación con un formato sin comprimir que utiliza 32 bits por píxel, BC1 (anteriormente denominado DXT1) alcanza una compresión de 8:1 y BC3 (anteriormente denominado DXT5), una de 4:1. La diferencia entre BC1 y BC3 es que BC1 no es compatible con un canal alfa, mientras que BC3 es compatible con un canal alfa con compresión de bloque. A pesar de las proporciones de alta compresión, solo hay una pequeña reducción en la calidad de la imagen para las texturas frecuentes. No obstante, la compresión de bloque de ciertos tipos de texturas, como, por ejemplo, las que tienen una gran variación del color en un área pequeña, pueden tener resultados inaceptables.

 Si las texturas son adecuadas para la compresión basada en bloque y no necesitan una fidelidad del color perfecta, considere utilizar un formato de compresión de bloque para reducir el uso de la memoria y consumir menos ancho de banda.

## <a name="remarks"></a>Comentarios
 Comprime texturas utilizando un formato de compresión basado en bloque en cada llamada de`ID3DDevice::CreateTexture2D` que crea una textura de origen. Específicamente, las texturas se comprimen cuando:

- El objeto `D3D11_TEXTURE2D_DESC` pasado en `pDesc` describe un recurso de sombreador invariable, que es:

  - El miembro BindFlags solo tiene el conjunto de marcadores D3D11_BIND_SHADER_RESOURCE.

  - El miembro Usage se establece en D3D11_USAGE_DEFAULT o D3D11_USAGE_IMMUTABLE.

  - El miembro CPUAccessFlags se establece en 0 (sin acceso a la CPU).

  - El miembro SamplerDesc tiene su miembro Count establecido en 1 (sin Suavizado de contorno de muestras múltiples [MSAA]).

- Los datos iniciales se proporcionan a la llamada a `CreateTexture2D`.

  A continuación se indican los formatos de origen compatibles y sus formatos de compresión de bloque.

|Formato original (de)|Formato comprimido (a)|
|------------------------------|------------------------------|
|`DXGI_FORMAT_B8G8R8X8_UNORM`|BC1 (anteriormente DXT1)|
|`DXGI_FORMAT_B8G8R8X8_UNORM_SRGB`|BC1|
|`DXGI_FORMAT_B8G8R8X8_TYPELESS`|BC1|
|`DXGI_FORMAT_B8G8R8A8_UNORM`|BC3 (anteriormente DXT5)|
|`DXGI_FORMAT_B8G8R8A8_UNORM_SRGB`|BC3|
|`DXGI_FORMAT_B8G8R8A8_TYPELESS`|BC3|
|`DXGI_FORMAT_R8G8B8A8_UNORM`|BC3|
|`DXGI_FORMAT_R8G8B8A8_UNORM_SRGB`|BC3|
|`DXGI_FORMAT_R8G8B8A8_TYPELESS`|BC3|

 Si su textura tiene un formato que no aparece en la lista, la textura no se modifica.

## <a name="restrictions-and-limitations"></a>Restricciones y limitaciones
 A veces, las texturas que están creadas con una variación de los formatos de imagen B8G8R8A8 o R8G8B8A8 realmente no utilizan el canal alfa, pero la variante no tiene forma alguna de saber si se utiliza o no. Para mantener la corrección en el caso que se utilice el canal alfa, la variante siempre codifica estos formatos en el formato BC3 menos eficaz. Puede ayudar a que el Análisis de Fotograma Gráficos entienda mejor el rendimiento de presentación potencial de la aplicación con esta variante utilizando una variación del formato de imagen B8G8R8X8 cuando no utiliza el canal alfa, para que la variante pueda utilizar el formato BC1 más eficaz.

## <a name="example"></a>Ejemplo
 Esta variante comprime las texturas en bloque en tiempo de ejecución antes de llamar a `CreateTexture2D`. No recomendamos este procedimiento para el código de producción, porque las texturas sin comprimir consumen más espacio de disco y porque el paso adicional puede aumentar significativamente los tiempos de carga en la aplicación, ya que la compresión basada en bloque requiere una gran cantidad de recursos técnicos para codificar. En su lugar, recomendamos que comprima las texturas sin conexión utilizando un editor o un procesador de imágenes que forme parte de la canalización integrada. Estos procedimientos reducen los requisitos de espacio en disco, eliminan la sobrecarga del tiempo de ejecución en la aplicación y proporcionan más tiempo de procesamiento para que pueda mantener la mejor calidad de imagen.

## <a name="see-also"></a>Vea también
- [Variante de dimensiones de textura Mitad/cuarto](half-quarter-texture-dimensions-variant.md)