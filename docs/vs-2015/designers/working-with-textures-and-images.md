---
title: Trabajar con texturas e imágenes | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b9fbc8fa-66d1-4055-8460-24d8b8fbe43e
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ff5125ce46abe993f35551a0ce46a0d211af99bb
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49250502"
---
# <a name="working-with-textures-and-images"></a>Trabajar con texturas e imágenes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede usar el editor de imágenes de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para crear y modificar texturas e imágenes. El editor de imágenes admite formatos de imagen y textura enriquecidos, como los que se usan en el desarrollo de aplicaciones de DirectX.  
  
> [!NOTE]
>  El editor de imágenes no es compatible con las imágenes de poco color, como los iconos o los cursores. Para crear o modificar esos tipos de imágenes, use el [editor de imágenes para iconos](http://msdn.microsoft.com/library/586d2b8b-0348-4883-a85d-1ff0ddbf14dd).  
  
## <a name="textures-and-images"></a>Texturas e imágenes  
 Las texturas e imágenes son, en un nivel básico, simplemente tablas de datos que se usan para proporcionar detalle visual en las aplicaciones de gráficos. El tipo de detalle que una textura o una imagen proporciona depende de cómo se use, pero las muestras de colores, los valores alfa (transparencia), las normales de superficie y los valores de altura son ejemplos comunes. La principal diferencia entre una textura y una imagen es que una textura está diseñada para usarse junto con una representación de la forma (normalmente un modelo 3D) para expresar un objeto o una escena completos, pero una imagen es normalmente una representación independiente del objeto o de la escena.  
  
 Los tipos comunes de textura incluyen:  
  
 Mapas de textura  
 Los mapas de textura contienen los valores de color que se organizan como una matriz de una, dos o tres dimensiones. Se usan para proporcionar el detalle de color en el objeto afectado. Los colores se codifican normalmente mediante los canales de color RGB (rojo, verde, azul) y pueden incluir un cuarto canal, el canal alfa, que representa la transparencia. Con menos frecuencia, los colores se pueden codificar en otro esquema de color, o bien el cuarto canal podría contener datos que no fueran alfa, por ejemplo, de altura.  
  
 Mapas normales  
 Los mapas normales contienen las normales de superficie. Se usan para proporcionar detalles de iluminación en el objeto en cuestión. Normalmente, las normales se codifican mediante los componentes de color rojo, verde y azul para almacenar las dimensiones de X, Y y Z del vector. Sin embargo, existen otras codificaciones, por ejemplo, codificaciones basadas en coordenadas polares.  
  
 Mapas de altura  
 Los mapas de altura contienen datos del campo de altura. Se usan para proporcionar una forma de detalle geométrico en el objeto mediante código del sombreador para calcular el efecto deseado, o bien para proporcionar los puntos de datos en usos como puede ser la generación del terreno. Los valores de altura se codifican normalmente con un canal en una textura.  
  
 Mapas de cubo  
 Los mapas de cubo pueden contener diferentes tipos de datos, por ejemplo, colores o normales, pero se organizan como seis texturas en las caras de un cubo. Por eso mismo, los mapas de cubo no se muestrean mediante coordenadas de textura, sino suministrando un vector cuyo origen es el centro del cubo. El ejemplo se toma en el punto donde el vector forma una intersección con el cubo. Los mapas de cubo se usan para proporcionar una aproximación del entorno que se puede usar para calcular reflexiones, lo cual recibe el nombre de *asignación de entornos*, o para proporcionar texturas a los objetos esféricos con menos distorsión que lo que proporcionan las texturas básicas bidimensionales.  
  
 Cualquier textura se puede codificar y comprimir de varias maneras que son ortogonales en relación con tipo de datos que contiene una textura o con la dimensión o "forma" de la textura. Sin embargo, los diferentes métodos de codificación y compresión producen mejores resultados para los diferentes tipos de datos.  
  
 Puede usar el editor de imágenes para crear y modificar texturas e imágenes de forma parecida a otros editores de imágenes. El editor de imágenes también permite generar mapas MIP y otras características para su uso con gráficos 3D y admite muchos de los formatos de texturas muy comprimidos y acelerados por hardware que son compatibles con DirectX.  
  
## <a name="related-topics"></a>Temas relacionados  
  
|Título|Descripción|  
|-----------|-----------------|  
|[Image Editor](../designers/image-editor.md)|Se describe el uso del editor de imágenes para trabajar con texturas e imágenes.|  
|[Ejemplos del Editor de imágenes](../designers/image-editor-examples.md)|Se ofrecen vínculos a temas que muestran cómo usar el editor de imágenes para realizar tareas comunes de procesamiento de imágenes.|



