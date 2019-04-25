---
title: Exportar y guardar los mapas de código
ms.date: 05/16/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70c4cd238b6e5d31eced6a35ff0c7d24ab85a280
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55907898"
---
# <a name="share-code-maps"></a>Compartir mapas de código

Puede guardar los mapas de código como parte de un proyecto de Visual Studio, como una imagen o como archivo XPS.

## <a name="share-a-code-map-with-other-visual-studio-users"></a>Compartir un mapa de código con otros usuarios de Visual Studio

Guarde el mapa desde el menú **Archivo** .

O bien

Para guardar el mapa como parte de un proyecto específico, en la barra de herramientas del mapa, elija **Share** > **mover \<CodeMapName > .dgml en**y, a continuación, elija el proyecto donde desea guardar el mapa.

![Mover un mapa a otro proyecto](../modeling/media/codemapsmovemapmenu.png)

Visual Studio guarda el mapa como una *.dgml* archivo que puede compartir con otros usuarios de Visual Studio Enterprise y Visual Studio Professional.

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

1. En la barra de herramientas del mapa de código, elija **Share** > **correo electrónico como imagen** o **Copiar imagen**.

2. Pegue la imagen en otra aplicación.

## <a name="export-the-map-as-an-xps-file"></a>Exportar el mapa como archivo XPS

Al exportar un mapa de código como archivo XPS, puede ver en visores XML o XAML como Internet Explorer.

1. En la barra de herramientas del mapa de código, elija **Share** > **correo electrónico como XPS Portable** o **Guardar como XPS Portable**.

2. Vaya adonde desea guardar el archivo.

3. Póngale un nombre al mapa de código. Asegúrese de que el **Guardar como tipo** cuadro se establece en **archivos XPS (\*.xps)**. Elija **Guardar**.

## <a name="see-also"></a>Vea también

- [Asignar dependencias con mapas de código](../modeling/map-dependencies-across-your-solutions.md)