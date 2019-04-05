---
title: Variante de generación MIP-map | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 3b4b3583-0b01-4f5d-aacb-3f96d19111d9
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c063235d69a59caf2c41c0db0ddc566c97cc95be
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58999674"
---
# <a name="mip-map-generation-variant"></a>Mip-map (Variante de generación)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Habilita la asignación de MIP en las texturas que no son objetivos de presentación.  
  
## <a name="interpretation"></a>Interpretación  
 La asignación de MIP se utiliza principalmente para eliminar los artefactos de alias en texturas en minificación precalculando versiones más pequeñas de la textura. Aunque estas texturas adicionales consumen memoria de GPU, alrededor de un 33 por ciento más que la textura original, también son más eficaces, porque una mayor parte de su área de superficie encaja en la caché de textura de GPU y sus contenidos logran un mayor uso.  
  
 Para escenas 3D recomendamos la asignación de MIP cuando la memoria está disponible para guardar estas texturas adicionales, ya que aumentan tanto el rendimiento de la presentación como la calidad de la imagen.  
  
 Si esta variante muestra un aumento significativo del rendimiento, indica que está utilizando texturas sin habilitar la asignación de MIP y, por lo tanto, no saca todo el partido de la caché de la textura.  
  
## <a name="remarks"></a>Comentarios  
 La generación de asignación de MIP se fuerza en todas las llamadas a `ID3D11Device::CreateTexture2D` que crean una textura de origen. En concreto, la generación de asignación de MIP se fuerza cuando el objeto D3D11_TEXTUR2D_DESC pasado en `pDesc` describe un recurso de sombreador invariable, que es:  
  
- El miembro BindFlags solo tiene el conjunto de marcadores D3D11_BIND_SHADER_RESOURCE.  
  
- El miembro Usage se establece en D3D11_USAGE_DEFUALT o D3D11_USAGE_IMMUTABLE.  
  
- El miembro CPUAccessFlags se establece en 0 (sin acceso a la CPU).  
  
- El miembro SampleDesc tiene su miembro Count establecido en 1 (sin Suavizado de contorno de muestras múltiples [MSAA]).  
  
- El miembro MipLevels está establecido en 1 (sin asignación de MIP).  
  
  Cuando la aplicación proporciona los datos iniciales, el formato de la textura debe ser compatible con la generación de asignación de MIP automática, como determina D3D11_FORMAT_SUPPORT_MIP_AUTOGEN, a menos que el formato sea BC1, BC2 o BC3. De lo contrario, la textura no se modifica y no se generan asignaciones de MIP cuando se proporcionan los datos iniciales.  
  
  Si las asignaciones de MIP se han generado automáticamente para una textura, las llamadas a `ID3D11Device::CreateShaderResourceView` se modifican durante la reproducción para utilizar la cadena de MIP durante el muestreo de la textura.  
  
## <a name="example"></a>Ejemplo  
 La variante **Mip-map Generation** se puede reproducir con un código como el siguiente:  
  
```  
D3D11_TEXTURE2D_DESC texture_description;  
  
// ...  
  
texture_description.MipLevels = 0; // generate a full mipchain  
  
std::vector<D3D11_SUBRESOURCE_DATA> initial_data(num_mips);  
  
for (auto&& mip_level : initial_data)  
{  
    // fill mip_level with the application-supplied initial data  
}  
  
d3d_device->CreateTexture2D(&texture_description, initial_data.data(), &texture)  
```  
  
 Para crear una textura que tenga una cadena de MIP completa, establezca `D3D11_TEXTURE2D_DESC::MipLevels` en 0. El número de niveles de mip en una cadena de mip completa es floor(log2(n) + 1), donde n es la mayor dimensión de la textura.  
  
 Recuerde que cuando proporciona datos iniciales de `CreateTexture2D`, debe proporcionar un objeto D3D11_SUBRESOURCE_DATA para cada nivel de MIP.  
  
> [!NOTE]
>  Si desea proporcionar sus propios contenidos de nivel de MIP en lugar de generarlos automáticamente, debe crear sus texturas utilizando un editor de imágenes que sea compatible con las texturas con asignación de MIP, cargar el archivo y pasar los niveles de MIP a `CreateTexture2D`.  
  
## <a name="see-also"></a>Vea también  
 [Variante de dimensiones de textura Mitad/cuarto](../debugger/half-quarter-texture-dimensions-variant.md)
