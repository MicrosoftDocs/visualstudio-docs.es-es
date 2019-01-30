---
title: Procedimiento Exportar una textura que contiene mapas MIP
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 3d1ad14b-44fb-4cf0-a995-5e2f60026524
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1eb303b29e3994f111aca7eb69740d44c9f3c010
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54979717"
---
# <a name="how-to-export-a-texture-that-contains-mipmaps"></a>Procedimiento Exportar una textura que contiene mapas MIP

La canalización de contenido de la imagen puede generar mapas MIP a partir de una imagen de origen como parte de la fase de compilación del proyecto. Para lograr determinados efectos, a veces hay que especificar manualmente el contenido de la imagen de cada nivel de MIP. Cuando no es necesario especificar manualmente el contenido de la imagen de cada nivel de MIP, generar asignaciones MIP en tiempo de compilación garantiza que el contenido de la asignación MIP se mantiene siempre sincronizado. También elimina el costo de rendimiento derivado de generar asignaciones MIP en tiempo de ejecución.

En este artículo se tratan los aspectos siguientes:

- Configurar la imagen de origen para que se procese mediante la canalización de contenido de la imagen.

- Configurar la canalización de contenido de la imagen para generar mapas MIP.

## <a name="export-mipmaps"></a>Exportar asignaciones MIP

Los mapas MIP proporcionan el nivel de detalle del espacio de pantalla automático para superficies con textura en un juego o aplicación 3D. Mejora el rendimiento de la representación de un juego o aplicación al calcular previamente versiones simplificadas de una textura. Calcular previamente las versiones simplificadas significa que no es necesario simplificar toda la textura en cada muestreo.

### <a name="to-export-a-texture-that-has-mipmaps"></a>Para exportar una textura que tiene mapas MIP

1. Comience con una textura básica. Cargue un archivo de imagen existente o cree uno como se explica en [Cómo: Crear una textura básica](../designers/how-to-create-a-basic-texture.md). Para admitir mapas MIP, especifique una textura con un ancho y un alto que sean ambos la misma potencia de dos de tamaño, por ejemplo, 64x64, 256x256 o 512x512.

2. Configure el archivo de textura que acaba de crear para que sea procesado por la canalización de contenido de imagen. En el **Explorador de soluciones**, abra el menú contextual del archivo de textura que ha creado y seleccione **Propiedades**. En la página **Propiedades de configuración** > **General**, establezca la propiedad **Tipo de elemento** en **Canalización de contenido de la imagen**. Asegúrese de que la propiedad **Contenido** esté establecida en **Sí** y **Excluir de la compilación** esté establecido en **No**. Seleccione **Aplicar**.

   Aparece la página de propiedades de configuración de **Canalización de contenido de la imagen**.

3. Configure la canalización de contenido de la imagen para generar mapas MIP. En la página **Propiedades de configuración** > **Canalización de contenido de la imagen** > **General**, establezca la propiedad **Generar Mips** en **Sí (/generatemips)**.

4. Seleccione **Aceptar**.

Al compilar el proyecto, la canalización de contenido de la imagen convierte la imagen de origen del formato de trabajo al formato de salida especificado, incluidos los niveles de MIP. El resultado se copia en el directorio de salida del proyecto.