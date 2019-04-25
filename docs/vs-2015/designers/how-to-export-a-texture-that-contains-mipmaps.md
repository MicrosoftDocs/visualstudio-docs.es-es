---
title: Procedimiento Exportar una textura que contiene mapas MIP | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 3d1ad14b-44fb-4cf0-a995-5e2f60026524
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f525f4b31a3535f6ea7b89d0443402240365cc7d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60088657"
---
# <a name="how-to-export-a-texture-that-contains-mipmaps"></a>Procedimiento Exportar una textura que contiene mapas MIP
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La canalización de contenido de la imagen puede generar mapas MIP a partir de una imagen de origen como parte de la fase de compilación del proyecto. Cuando no necesita especificar el contenido de la imagen de cada nivel de MIP manualmente (como podría hacer para lograr determinados efectos), generar mapas MIP en tiempo de compilación garantiza que el contenido del mapa MIP nunca dejará de estar sincronizado y elimina el costo de rendimiento de generar mapas MIP en tiempo de ejecución.  
  
 Este documento muestra estas actividades:  
  
- Configurar la imagen de origen para que se procese mediante la canalización de contenido de la imagen.  
  
- Configurar la canalización de contenido de la imagen para generar mapas MIP.  
  
## <a name="exporting-mipmaps"></a>Exportar mapas MIP  
 Los mapas MIP proporcionan el nivel de detalle del espacio de pantalla automático para superficies con textura en un juego o aplicación 3D. Mejoran el rendimiento de la representación de un juego o aplicación calculando previamente versiones de calidad reducida de una textura para que la calidad de la textura completa no tenga que reducirse cada vez que se muestree.  
  
#### <a name="to-export-a-texture-that-has-mipmaps"></a>Para exportar una textura que tiene mapas MIP  
  
1. Comience con una textura básica. Cargue un archivo de imagen existente o cree uno como se explica en [Cómo: Crear una textura básica](../designers/how-to-create-a-basic-texture.md). Para admitir mapas MIP, especifique una textura con un ancho y un alto que sean ambos la misma potencia de dos de tamaño, por ejemplo, 64x64, 256x256 o 512x512.  
  
2. Configure el archivo de textura que acaba de crear para que sea procesado por la canalización de contenido de imagen. En el **Explorador de soluciones**, abra el menú contextual del archivo de textura que acaba de crear y seleccione **Propiedades**. En **Propiedades de configuración**, la página **General**, establezca la propiedad **Tipo de elemento** en **Canalización de contenido de la imagen**. Asegúrese de que la propiedad **Contenido** esté establecida en **Sí** y **Excluir de la compilación** esté establecido en **No**, y, después, seleccione el botón **Aplicar**. Aparece la página de propiedades de configuración de **Canalización de contenido de la imagen**.  
  
3. Configure la canalización de contenido de la imagen para generar mapas MIP. En **Propiedades de configuración**, **Canalización de contenido de la imagen**, página **General**, establezca la propiedad **Generar Mips** en **Sí (/generatemips)**.  
  
4. Elija el botón **Aceptar** .  
  
   Al compilar el proyecto, la canalización de contenido de la imagen convierte la imagen de origen del formato de trabajo al formato de salida especificado, incluidos los niveles de MIP, y el resultado se copia en el directorio de salida del proyecto.
