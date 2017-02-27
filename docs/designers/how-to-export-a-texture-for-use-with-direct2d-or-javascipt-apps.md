---
title: "C&#243;mo: Exportar una textura para usarla con aplicaciones de Direct2D o Javascipt | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 241c25fe-764e-4e1b-ad32-b1377dcbb605
caps.latest.revision: 11
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 11
---
# C&#243;mo: Exportar una textura para usarla con aplicaciones de Direct2D o Javascipt
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La canalización de contenido de la imagen puede generar texturas compatibles con las convenciones de representación internas de Direct2D.  Las texturas de esta clase son adecuadas para su uso en aplicaciones que utilizan Direct2D y en aplicaciones de la Tienda Windows creadas mediante JavaScript.  
  
 En este documento se muestran estas actividades:  
  
-   Configurar la imagen de origen para que se procese mediante Canalización de contenido de la imagen.  
  
-   Configurar Canalización de contenido de la imagen para generar una textura que se pueda usar en una aplicación de Direct2D o JavaScript.  
  
    -   Generar un archivo .dds comprimido en bloques.  
  
    -   Generar valores alfa premultiplicados.  
  
    -   Deshabilitar la generación de mapa MIP.  
  
## Representación de convenciones en Direct2D  
 Las texturas que se utilizan en el contexto de Direct2D deben cumplir estas convenciones de representación internas de Direct2D:  
  
-   Direct2D implementa transparencia y translucidez mediante valores alfa premultiplicados.  Las texturas utilizadas con Direct2D deben contener alfa premultiplicado, aunque la textura no use transparencia o translucidez.  Para obtener más información sobre el alfa premultiplicado, vea [Cómo: Exportar una textura que tiene valores alfa previamente multiplicados](../designers/how-to-export-a-texture-that-has-premultiplied-alpha.md).  
  
-   La textura se debe proporcionar en formato .dds, utilizando uno de estos formatos de compresión de bloques:  
  
    -   Compresión BC1\_UNORM  
  
    -   Compresión BC2\_UNORM  
  
    -   Compresión BC3\_UNORM  
  
-   No se admiten mapas MIP.  
  
#### Para crear una textura compatible con las convenciones de representación de Direct2D  
  
1.  Comience con una textura básica.  Cargue una imagen existente o cree una nueva como se describe en [Cómo: Crear una textura básica](../designers/how-to-create-a-basic-texture.md).  Para admitir la compresión de bloques en formato de .dds, especifique una textura con un ancho y un alto que sean múltiplos de cuatro de tamaño, por ejemplo, 100x100, 128x128 o 256x192.  Dado que el mipmapping no se admite, la textura no tiene que ser cuadrada y no tiene que ser potencia de dos de tamaño.  
  
2.  Configure el archivo de textura para que sea procesado por la canalización de contenido de imagen.  En **Explorador de soluciones**, abra el menú contextual del archivo de textura que acaba de crear y elija **Propiedades**.  En **Propiedades de configuración**, la página **General**, establezca la propiedad **Tipo de elemento** en **Canalización de contenido de la imagen**.  Asegúrese de que la propiedad **Contenido** esté establecida en **Sí** y **Excluir de la compilación** esté establecido en **No**, y, a continuación, elija el botón **Aplicar**.  Aparece la página de propiedades de configuración de **Canalización de contenido de la imagen**.  
  
3.  Establezca el formato de salida en uno de los formatos comprimidos en bloques.  En **Propiedades de configuración**, **Canalización de contenido de la imagen**, la página **General**, establezca la propiedad **Compress** en **Compresión BC3\_UNORM \(\/compress: BC3\_UNORM\)**.  Podría elegir cualquiera de los otros formatos BC1, BC2 o BC3, según sus requisitos.  Direct2D no admite actualmente las texturas BC4, BC5, BC6 o BC7.  Para obtener más información sobre los diferentes formatos BC, vea la página web sobre la [compresión de bloques \(Direct3D 10\)](http://msdn.microsoft.com/library/windows/desktop/bb694531.aspx).  
  
    > [!NOTE]
    >  El formato de compresión especificado determina el formato del archivo generado por la canalización de contenido de la imagen.  Esto es diferente de la propiedad **Formato** de la imagen de origen en el Editor de imágenes, que determina el formato del archivo de imagen de origen tal como está almacenado en disco, es decir, el *formato de trabajo*.  Normalmente, no desea un formato de trabajo comprimido.  
  
4.  Configure la canalización de contenido de imagen para producir una salida que utilice alfa premultiplicada.  En **Propiedades de configuración**, **Canalización de contenido de la imagen**, la página **General**, establezca la propiedad de **convertir en formato alfa premultiplicado** en **Sí \(\/generatepremultipliedalpha\)**.  
  
5.  Configure la canalización de contenido de la imagen para que no genere mipmaps.  En **Propiedades de configuración**, **Canalización de contenido de la imagen**, la página **General**, establezca la propiedad **Generar Mips** en **No**.  
  
6.  Elija el botón **Aceptar**.  
  
 Al compilar el proyecto, la Canalización de contenido de la imagen convierte la imagen de origen del formato de trabajo al formato de salida especificado \(la conversión incluye la generación de alfa multiplicado previamente\) y el resultado se copia en el directorio de resultados del proyecto.