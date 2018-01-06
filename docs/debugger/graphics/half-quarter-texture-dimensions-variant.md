---
title: Mitad Quarter Texture Dimensions variante | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 282e9bbb-51aa-4cd0-8e5c-0901268c29e5
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 93431c8863e2b30fb98d00bec5112257e54496f1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="halfquarter-texture-dimensions-variant"></a>MItad/cuarto (Variante de dimensiones de textura)
Reduce las dimensiones de la textura en texturas que no son objetivos de presentación.  
  
## <a name="interpretation"></a>Interpretación  
 Las texturas más pequeñas ocupan menos memoria y, por lo tanto, consumen menos ancho de banda de memoria y reducen la presión en la caché de la textura de la GPU. Sin embargo, como tienen menos detalles la calidad de la imagen puede disminuir, especialmente cuando se miran de cerca en una escena 3D o se ven ampliadas.  
  
 Si esta variante muestra un gran aumento del rendimiento, puede indicar que la aplicación consume demasiado ancho de memoria, utiliza una caché de textura ineficaz o ambas cosas. También puede indicar que las texturas ocupan más memoria de GPU de la que está disponible, lo que provoca que las texturas se paginen a la memoria del sistema.  
  
 Si la aplicación consume demasiado ancho de banda de memoria o utiliza la caché de textura ineficazmente, considere reducir el tamaño de las texturas, pero solo después de habilitar la asignación de MIP para las texturas adecuadas. Como las texturas más pequeñas, las texturas con asignación de MIP consumen menos ancho de banda de memoria, aunque ocupan más memoria de GPU, y aumentan el uso de la caché, pero no reducen los detalles de la textura. Recomendamos las asignaciones de MIP siempre que el aumento del uso de la memoria no provoque que las texturas se paginen a la memoria del sistema.  
  
 Si las texturas ocupan más memoria de GPU de la que está disponible, considere reducir el tamaño de las texturas, pero solo después de comprimir las texturas adecuadas. Como las texturas más pequeñas, las texturas comprimidas ocupan menos memoria y reducen la necesidad de paginar a la memoria del sistema, pero se reduce la fidelidad del color. La compresión no es adecuada para todas las texturas, según su contenido, por ejemplo, las que tienen una variación del color significativa en un área pequeña, pero, para muchas texturas, la compresión puede conservar una mejor calidad de la imagen más que reducir su tamaño.  
  
## <a name="remarks"></a>Comentarios  
 Las dimensiones de la textura se reducen en todas las llamadas a `ID3D11Device::CreateTexture2D` que crean una textura de origen. En concreto, las dimensiones de la textura se reducen cuando el objeto D3D11_TEXTURE2D_DESC pasado en `pDesc` describe una textura que se utiliza en la presentación, que es:  
  
-   El miembro BindFlags solo tiene el conjunto de marcadores D3D11_BIND_SHADER_RESOURCE.  
  
-   El miembro MiscFlags no tiene el marcador D3D11_RESOURCE_MISC_TILE_POOL o el conjunto de marcadores D3D11_RESOURCE_MISC_TILED (no se cambia el tamaño de los recursos en mosaico).  
  
-   El formato de la textura se admite como objetivo de presentación, como determina D3D11_FORMAT_SUPPORT_RENDER_TARGET, que se requiere para reducir el tamaño de la textura. Los formatos BC1, BC2 y BC3 también se admiten, aunque no se admiten como objetivos de presentación.  
  
 Si la aplicación suministra los datos iniciales, esta variante escala los datos de la textura al tamaño adecuado antes de crear la textura. Si los datos iniciales se suministran en un formato de compresión de bloque, como BC1, BC2 o BC3, se descodifica, escala y vuelve a codificar antes de utilizarse para crear la textura más pequeña. (La naturaleza de la compresión basada en bloque significa que el proceso adicional de descodificar-escalar-codificar casi siempre disminuye más la calidad de la imagen que cuando una textura con compresión de bloque se genera a partir de una versión escalada de la textura que no se había codificado previamente.)  
  
 Si las asignaciones de MIP están habilitadas para la textura, la variante reduce el número de niveles de MIP como corresponda, uno menos cuando se escala a la mitad del tamaño y dos menos cuando se escala a un cuarto.  
  
## <a name="example"></a>Ejemplo  
 Esta variante modifica el tamaño de las texturas en el tiempo de ejecución antes de llamar a `CreateTexture2D`. No recomendamos este procedimiento para el código de producción, porque las texturas a tamaño completo consumen más espacio de disco y porque el paso adicional puede aumentar significativamente los tiempos de carga en la aplicación, especialmente para las texturas comprimidas, que requieren una gran cantidad de recursos técnicos para codificar. En su lugar, recomendamos que cambie el tamaño las texturas sin conexión utilizando un editor o un procesador de imágenes que forme parte de la canalización integrada. Estos procedimientos reducen los requisitos de espacio en disco, eliminan la sobrecarga del tiempo de ejecución en la aplicación y proporcionan más tiempo de procesamiento para que pueda mantener la mejor calidad de imagen al reducir o comprimir las texturas.  
  
## <a name="see-also"></a>Vea también  
 [Variante de generación de asignación de MIP](mip-map-generation-variant.md)   
 [Variante de compresión de textura BC](bc-texture-compression-variant.md)