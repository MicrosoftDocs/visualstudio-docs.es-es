---
title: Procedimiento Exportar una textura para usarla con aplicaciones de Direct2D o Javascipt
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 241c25fe-764e-4e1b-ad32-b1377dcbb605
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f7f094d08403b4410aa3075f90b8ff7c5e5491cf
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55018493"
---
# <a name="how-to-export-a-texture-for-use-with-direct2d-or-javascipt-apps"></a>Procedimiento Exportar una textura para usarla con aplicaciones de Direct2D o Javascipt

La canalización de contenido de la imagen puede generar texturas compatibles con las convenciones de representación internas de Direct2D. Las texturas de esta clase son adecuadas para su uso en aplicaciones que usan Direct2D y en aplicaciones para UWP creadas mediante JavaScript.

Este documento muestra estas actividades:

-   Configurar la imagen de origen para que se procese mediante la canalización de contenido de la imagen.

-   Configurar la canalización de contenido de la imagen para generar una textura que se pueda usar en una aplicación de Direct2D o JavaScript.

    -   Generar un archivo *.dds* comprimido en bloques.

    -   Generar valores alfa premultiplicados.

    -   Deshabilitar la generación de mapa MIP.

## <a name="rendering-conventions-in-direct2d"></a>Representación de convenciones en Direct2D

Las texturas que se usan en el contexto de Direct2D deben cumplir estas convenciones de representación internas de Direct2D:

-   Direct2D implementa transparencia y translucidez mediante valores alfa premultiplicados. Las texturas usadas con Direct2D deben contener alfa premultiplicado, aunque la textura no use transparencia o translucidez. Para obtener más información sobre el valor alfa previamente multiplicado, vea [Cómo: Exportar una textura que tiene valores alfa previamente multiplicados](../designers/how-to-export-a-texture-that-has-premultiplied-alpha.md).

-   La textura se debe proporcionar en formato *.dds*, usando uno de estos formatos de compresión de bloques:

    -   Compresión BC1_UNORM

    -   Compresión BC2_UNORM

    -   Compresión BC3_UNORM

-   No se admiten los mapas MIP.

### <a name="to-create-a-texture-thats-compatible-with-direct2d-rendering-conventions"></a>Para crear una textura compatible con las convenciones de representación de Direct2D

1. Comience con una textura básica. Cargue una imagen existente o cree una como se explica en [Cómo: Crear una textura básica](../designers/how-to-create-a-basic-texture.md). Para admitir la compresión de bloques en formato de *.dds*, especifique una textura con un ancho y un alto que sean múltiplos de cuatro de tamaño, por ejemplo, 100x100, 128x128 o 256x192. Dado que los mapas MIP no se admiten, la textura no tiene que ser cuadrada y no tiene que ser potencia de dos de tamaño.

2. Configure el archivo de textura para que sea procesado por la canalización de contenido de imagen. En el **Explorador de soluciones**, abra el menú contextual del archivo de textura que acaba de crear y seleccione **Propiedades**. En la página **Propiedades de configuración** > **General**, establezca la propiedad **Tipo de elemento** en **Canalización de contenido de la imagen**. Asegúrese de que la propiedad **Contenido** esté establecida en **Sí** y **Excluir de la compilación** esté establecido en **No**, y, después, seleccione el botón **Aplicar**. Aparece la página de propiedades de configuración de **Canalización de contenido de la imagen**.

3. Establezca el formato de salida en uno de los formatos comprimidos en bloques. En **Propiedades de configuración** > **Canalización de contenido de la imagen** > , en la página **General**, establezca la propiedad **Compress** en **Compresión BC3_UNORM (/compress: BC3_UNORM)**. Podría elegir cualquiera de los otros formatos BC1, BC2 o BC3, según sus requisitos. Direct2D no admite actualmente las texturas BC4, BC5, BC6 o BC7. Para obtener más información sobre los diferentes formatos BC, vea la página web sobre la [compresión de bloques (Direct3D 10)](/windows/desktop/direct3d10/d3d10-graphics-programming-guide-resources-block-compression).

   > [!NOTE]
   > El formato de compresión especificado determina el formato del archivo generado por la canalización de contenido de la imagen. Esto es diferente de la propiedad **Formato** de la imagen de origen en el Editor de imágenes, que determina el formato del archivo de imagen de origen tal como está almacenado en disco, es decir, el *formato de trabajo*. Normalmente, no quiere un formato de trabajo comprimido.

4. Configure la canalización de contenido de imagen para producir una salida que use alfa premultiplicado. En **Propiedades de configuración** > **Canalización de contenido de la imagen** >  en la página **General**, establezca la propiedad **Convertir en formato alfa premultiplicado** en **Sí (/generatepremultipliedalpha)**.

5. Configure la canalización de contenido de la imagen para que no genere mapas MIP. En la página **Propiedades de configuración** > **Canalización de contenido de la imagen** > **General**, establezca la propiedad **Generar Mips** en **No**.

6. Elija el botón **Aceptar** .

   Al compilar el proyecto, la canalización de contenido de la imagen convierte la imagen de origen del formato de trabajo al formato de salida especificado (la conversión incluye la generación de alfa multiplicado previamente) y el resultado se copia en el directorio de resultados del proyecto.