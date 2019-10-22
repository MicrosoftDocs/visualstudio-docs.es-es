---
title: Exportar y guardar mapas de código
ms.date: 05/16/2018
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 991773953338e38331bad45bfa1149aeb27c748b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670804"
---
# <a name="share-code-maps"></a>Compartir mapas de código

Puede guardar los mapas de código como parte de un proyecto de Visual Studio, como una imagen o como un archivo XPS.

## <a name="share-a-code-map-with-other-visual-studio-users"></a>Compartir un mapa de código con otros usuarios de Visual Studio

Guarde el mapa desde el menú **Archivo** .

o bien

Para guardar el mapa como parte de un proyecto específico, en la barra de herramientas del mapa, elija **compartir**  > **mueva \<CodeMapName >. DGML a**y, a continuación, elija el proyecto donde desea guardar el mapa.

![Mover un mapa a otro proyecto](../modeling/media/codemapsmovemapmenu.png)

Visual Studio guarda el mapa como un archivo *. DGML* que puede compartir con otros usuarios de Visual Studio Enterprise y Visual Studio Professional.

> [!NOTE]
> Antes de compartir un mapa con usuarios de Visual Studio Professional, asegúrese de expandir los grupos, de mostrar los nodos ocultos y los vínculos entre grupos, y de recuperar los nodos eliminados que desea que los demás vean en el mapa. De lo contrario, los otros usuarios no podrán ver estos elementos.
>
> El error siguiente podría producirse al guardar un mapa que está en un proyecto de modelado o que se copió desde un proyecto de modelado en otra ubicación:
>
> "No se puede guardar *nombreDeArchivo* fuera del directorio del proyecto. No se admiten elementos vinculados".
>
> Visual Studio muestra el error pero crea la versión guardada de todas maneras. Para evitar el error, cree el mapa fuera del proyecto de modelado. Después puede guardarlo en la ubicación que desee. Copiar el archivo en otra ubicación de la solución e intentar guardarlo después no dará resultado.

## <a name="export-a-code-map-as-an-image"></a>Exportar un mapa de código como una imagen

Al exportar un mapa de código como una imagen, puede copiarlo en otras aplicaciones, como Microsoft Word o PowerPoint.

1. En la barra de herramientas del mapa de código, elija **compartir**  > **correo electrónico como imagen** o **Copiar imagen**.

2. Pegue la imagen en otra aplicación.

## <a name="export-the-map-as-an-xps-file"></a>Exportar el mapa como un archivo XPS

Al exportar un mapa de código como un archivo XPS, puede verlo en visores XML o XAML como Internet Explorer.

1. En la barra de herramientas del mapa de código, elija **compartir**  > **correo electrónico como XPS portable** o **Guardar como XPS portátil**.

2. Vaya adonde desea guardar el archivo.

3. Póngale un nombre al mapa de código. Asegúrese de que la casilla **Guardar como tipo** esté establecida en **archivos XPS (\*. XPS)** . Elija **Guardar**.

## <a name="see-also"></a>Vea también

- [Asignación de dependencias con mapas de código](../modeling/map-dependencies-across-your-solutions.md)