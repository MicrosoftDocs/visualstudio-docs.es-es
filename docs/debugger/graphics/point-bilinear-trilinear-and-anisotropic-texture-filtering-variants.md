---
title: Puntual, bilineal, trilineal y anisotrópico de textura variantes de filtrado | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 57d14fc9-b5f7-45ee-9717-48086886742d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4958436e7b67872648c94c8aa65137a1297461c3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49863118"
---
# <a name="point-bilinear-trilinear-and-anisotropic-texture-filtering-variants"></a>Variantes de filtrado puntual, bilineal, trilineal y anisotrópico de textura
Reemplaza el modo de filtrado en las muestras de textura adecuadas.  
  
## <a name="interpretation"></a>Interpretación  
 Cada método de muestreo de textura tiene diferentes costes de rendimiento y calidad de la imagen. Para aumentar los costes, y aumentar la calidad visual, los modos de filtro son:  
  
1. Filtrado de punto (el menos caro, la peor calidad visual)  
  
2. Filtrado bilineal  
  
3. Filtrado trilineal  
  
4. Filtrado anisotrópico (el más caro, la mejor calidad visual)  
  
   Si el coste de rendimiento de cada variante es significativo o aumenta con modos de filtrado que consumen más, puede comparar su coste con la mejora en la calidad de la imagen. Según su evaluación, puede aceptar costes de rendimiento adicionales para aumentar la calidad visual o puede aceptar una peor calidad visual para conseguir una velocidad de fotogramas superior o recuperar un rendimiento que puede utilizar de otras maneras.  
  
   Si cree que el coste de rendimiento es insignificante o constante independientemente del modo de filtrado, por ejemplo, cuando la GPU de destino tiene un rendimiento de sombreador y un ancho de banda de memoria abundantes, considere utilizar el filtrado anisotrópico para conseguir la mejor calidad de imagen en la aplicación.  
  
## <a name="remarks"></a>Comentarios  
 Estas variantes reemplazan los estados de la muestra en llamadas a `ID3D11DeviceContext::PSSetSamplers` en las que el modo de filtrado de la muestra proporcionado por la aplicación es uno de los siguientes:  
  
- `D3D11_FILTER_MIN_MAG_MIP_POINT`  
  
- `D3D11_FILTER_MIN_MAG_POINT_MIP_LINEAR`  
  
- `D3D11_FILTER_MIN_POINT_MAG_LINEAR_MIP_POINT`  
  
- `D3D11_FILTER_MIN_POINT_MAG_MIP_LINEAR`  
  
- `D3D11_FILTER_MIN_LINEAR_MAG_MIP_POINT`  
  
- `D3D11_FILTER_MIN_LINEAR_MAG_POINT_MIP_LINEAR`  
  
- `D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT`  
  
- `D3D11_FILTER_MIN_MAG_MIP_LINEAR`  
  
- `D3D11_FILTER_ANISOTROPIC`  
  
  En el **Point Texture Filtering** variant, el modo de filtro proporcionada por la aplicación se reemplaza por `D3D11_FILTER_MIN_MAG_MIP_POINT`; en el **Bilinear Texture Filtering** variante, se reemplaza por `D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT`; y, en el **Trilinear Texture Filtering** variante, se reemplaza por `D3D11_FILTER_MIN_MAG_MIP_LINEAR`.  
  
  En el **Anisotropic Texture Filtering** variant, el modo de filtro proporcionada por la aplicación se reemplaza por `D3D11_FILTER_ANISOTROPIC`, y Max Anisotropy se establece en 16.  
  
## <a name="restrictions-and-limitations"></a>Restricciones y limitaciones  
 En Direct3D, el nivel de características 9.1 especifica una anisotropía máxima de 2x. Dado que el **Anisotropic Texture Filtering** variante intenta utilizar únicamente la anisotropía 16 x exclusivamente, la reproducción se produce un error cuando se ejecuta el análisis de fotogramas en un dispositivo de nivel de características 9.1. Entre los dispositivos actuales que están afectados por esta limitación se incluyen las tabletas de Microsoft basadas en ARM Surface RT y Surface 2. También pueden verse afectadas otras GPU que todavía pueden encontrarse en algunos ordenadores, pero en general se considera que están obsoletas y de cada vez son menos habituales.  
  
## <a name="example"></a>Ejemplo  
 El **Point Texture Filtering** variante se puede reproducir con código similar al siguiente:  
  
```cpp
D3D11_SAMPLER_DESC sampler_description;  
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_MIN_MAG_MIP_POINT;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```  
  
## <a name="example"></a>Ejemplo  
 El **Bilinear Texture Filtering** variante se puede reproducir con código similar al siguiente:  
  
```cpp
D3D11_SAMPLER_DESC sampler_description;   
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```  
  
## <a name="example"></a>Ejemplo  
 El **Trilinear Texture Filtering** variante se puede reproducir con código similar al siguiente:  
  
```cpp
D3D11_SAMPLER_DESC sampler_description;   
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_MIN_MAG_MIP_LINEAR;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```  
  
## <a name="example"></a>Ejemplo  
 El **Anisotropic Texture Filtering** variante se puede reproducir con código similar al siguiente:  
  
```cpp
D3D11_SAMPLER_DESC sampler_description;   
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_ANISOTROPIC;  
sampler_description.MaxAnisotropy = 16;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```
