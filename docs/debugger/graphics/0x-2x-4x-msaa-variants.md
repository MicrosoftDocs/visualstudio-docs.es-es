---
title: x-2 MSAA x-4 0 (variantes) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
ms.assetid: 668a6603-5082-4c78-98e6-f3dc871aa55b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 09ec8c25a076fd9f74690b3be92715aa62b60f65
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="0x2x4x-msaa-variants"></a>0x/2x/4x MSAA (Variantes)
Reemplaza el suavizado de contorno de muestras múltiples (MSAA) en todos los objetivos de presentación y cadenas de intercambio.  
  
## <a name="interpretation"></a>Interpretación  
 El suavizado de contorno de muestras múltiples aumenta la calidad visual tomando muestras en varias ubicaciones de cada píxel. Los mayores niveles de MSAA toman más muestras y, sin MSAA, solo se toma una muestra del centro del píxel. Habilitar el MSAA en la aplicación suele tener un coste modesto pero apreciable en el rendimiento de la presentación, aunque en ciertas cargas de trabajo o en determinadas GPU es posible que no tenga casi ningún impacto.  
  
 Si su aplicación ya tiene el MSAA habilitado, que haya menos variantes de MSAA indica el coste de rendimiento relativo que produce el MSAA de más alto nivel existente. En concreto, la variante 0x MSAA indica el rendimiento relativo de la aplicación sin MSAA.  
  
 Si la aplicación todavía no tiene MSAA habilitado, las variantes 2x MSAA y 4x MSAA indican el coste de rendimiento relativo de habilitarlas en su aplicación. Cuando el coste es aceptablemente bajo, considere activar MSAA para aumentar la calidad de la imagen en su aplicación.  
  
> [!NOTE]
>  Es posible que su hardware no sea compatible totalmente con MSAA para todos los formatos. Si alguna de estas variantes encuentra una limitación de hardware que no puede solucionarse, su columna en la tabla de resumen del rendimiento estará en blanco y se producirá un mensaje de error.  
  
## <a name="remarks"></a>Comentarios  
 Estas variantes reemplazan el recuento de muestra y los argumentos de calidad de la muestra en llamadas a `ID3DDevice::CreateTexture2D` que crean objetivos de presentación. En concreto, estos parámetros se sustituyen cuando:  
  
-   El objeto `D3D11_TEXTURE2D_DESC` pasado en `pDesc` describe un objetivo de presentación, que es:  
  
    -   El miembro BindFlags tiene el conjunto de marcadores marcador D3D11_BIND_TARGET o marcador D3D11_BIND_DEPTH_STENCIL.  
  
    -   El miembro Usage está establecido en D3D11_USAGE_DEFAULT.  
  
    -   El miembro CPUAccessFlags está establecido en 0.  
  
    -   El miembro MipLevels está establecido en 1.  
  
-   El dispositivo admite el recuento de muestra solicitado (0, 2 o 4) y la calidad de muestreo (0) para el formato de objetivo de presentación solicitado (miembro D3D11_TEXTURE2D_DESC::Format), como determina `ID3D11Device::CheckMultisampleQualityLevels`.  
  
 Si el miembro D3D11_TEXTURE2D_DESC::BindFlags tiene el conjunto de marcadores D3D_BIND_SHADER_RESOUCE o D3D11_BIND_UNORDERED_ACCESS, se crean dos versiones de la textura; la primera tiene los marcadores desactivados para utilizarse como objetivo de presentación y la otra es una textura sin MSAA que tiene estos marcadores intactos para que actúen como búfer de resolución para la primera versión. Esto es necesario porque es improbable que sea válido utilizar una textura de MSAA como recurso de sombreador o para acceso no ordenado, por ejemplo, un sombreador que actúe en ella generaría resultados incorrectos, porque esperaría una textura sin MSAA. Si la variante ha creado la textura sin MSAA secundaria, cuando el objetivo de presentación de MSAA no esté establecido en el contexto del dispositivo, sus contenidos se resuelven en la textura sin MSAA. De la misma forma, si el objetivo de presentación de MSAA debe limitarse un recurso de sombreador o se utiliza en una vista de acceso no ordenado, la textura de sin MSAA resuelta se limita.  
  
 Estas variantes también reemplazan la configuración de MSAA en todas las cadenas de intercambio utilizando `IDXGIFactory::CreateSwapChain`, `IDXGIFactory2::CreateSwapChainForHwnd`, `IDXGIFactory2::CreateSwapChainForCoreWindow`, `IDXGIFactory2::CreateSwapChainForComposition` y `ID3D11CreateDeviceAndSwapChain`.  
  
 El siguiente efecto de estos cambios es que todas las presentaciones se realizan en un objetivo de presentación de MSAA, pero si su aplicación utiliza uno de estos objetivos de presentación o búferes de cadena de intercambio como vista de recurso de sombreador o de acceso no ordenado, se realiza un muestreo de los datos a partir de la copia sin MSAA resuelta del objetivo de presentación.  
  
## <a name="restrictions-and-limitations"></a>Restricciones y limitaciones  
 En Direct3D 11, las texturas MSAA están más restringidas que las texturas sin MSAA. Por ejemplo, no puede llamar a `ID3D11DeviceContext::UpdateSubresource` en una textura MSAA y se produce un error en la llamada a `ID3D11DeviceContext::CopySubresourceRegion` si el recuento y la calidad de muestra del recurso y la destinación de origen no coinciden, lo que puede ocurrir cuando esta variante reemplaza la configuración de MSAA de un recurso pero no del otro.  
  
 Cuando la reproducción detecta este tipo de conflictos, hace todo lo que puede para replicar el comportamiento previsto, pero puede no ser posible que los resultados coincidan exactamente. Aunque no es habitual que esto afecte al rendimiento de estas variantes de tal manera que distorsione su impacto, es posible que suceda, por ejemplo, cuando el control de flujo de un sombreador de píxeles se determine por el contenido concreto de una textura, porque la textura replicada puede que no tenga contenidos idénticos.  
  
## <a name="example"></a>Ejemplo  
 Estas variantes se pueden reproducir para objetivos de presentación creados utilizando `ID3D11Device::CreateTexture2D` y código como el siguiente:  
  
```  
D3D11_TEXTURE2D_DESC target_description;  
target_description.BindFlags = D3D11_BIND_RENDER_TARGET;  
target_description.SampleDesc.Count = 4; // 4x MSAA, can be 2 or 0 instead  
target_description.SampleDesc.Quality = 0;  
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);  
```  
  
## <a name="example"></a>Ejemplo  
 O para cadenas de intercambio creadas utilizando IDXGISwapChain::CreateSwapChain o D3D11CreateDeviceAndSwapChain y código como el siguiente:  
  
```  
DXGI_SWAP_CHAIN_DESC chain_description;  
chain_description.SampleDesc.Count = 4; // 4x MSAA, can be 2 or 0 instead  
chain_description.SampleDesc.Quality = 0;  
  
// Call IDXGISwapChain::CreateSwapChain or D3D11CreateDeviceAndSwapChain, etc.  
```