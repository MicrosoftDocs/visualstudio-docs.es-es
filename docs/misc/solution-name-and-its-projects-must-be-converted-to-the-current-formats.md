---
title: "La soluci&#243;n &lt;nombre&gt; y sus proyectos deben convertirse a los formatos actuales | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.querymigratesolution"
ms.assetid: 1ecb09ab-1283-4ba5-874c-f675905a3b7b
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# La soluci&#243;n &lt;nombre&gt; y sus proyectos deben convertirse a los formatos actuales
Ha abierto una solución que se creó en una versión anterior de Visual Studio. Para poder abrir una solución y editarla en la versión de Visual Studio instalada en el equipo, hay que convertir los archivos de solución y proyecto a los formatos actuales. Puede decidir si quiere convertir esta solución ahora o no. Las conversiones de formato no se pueden deshacer.  
  
> [!CAUTION]
>  Si la solución está almacenada bajo control de código fuente e intenta volver a protegerla, primero determine si alguna otra solución comparte alguno de sus proyectos. No proteja una solución que incluya proyectos convertidos que todavía se estén usando en otras soluciones no convertidas. Esto rompería las dependencias entre esas soluciones y les impediría abrirse o compilarse correctamente.  
  
 Es posible que quiera realizar copias de seguridad de los archivos de solución y proyecto antes de convertirlos.  
  
> [!NOTE]
>  A medida que las soluciones de Visual Studio se convierten, los archivos de solución anteriores se marcan con la extensión de archivo ".old" y se guardan en el directorio de la solución de nivel superior. A medida que determinados tipos de proyecto se convierten, por ejemplo los proyectos de Visual C\+\+, los archivos de proyecto antiguos se marcan igualmente con la extensión de archivo ".old" y se guardan en el directorio del proyecto.  
  
 Los proyectos de solo lectura no se convierten. Solo los usuarios con permiso para editarlos pueden convertir estos proyectos. Para que un proyecto pueda usarse en una solución convertida, sus archivos de proyecto se deben convertir a los formatos actuales. Después de convertir una solución o cualquiera de sus proyectos, ya no se puede editar, compilar ni ejecutar la solución en las versiones anteriores de Visual Studio.  
  
### Para responder a este mensaje  
  
1.  Seleccione **Sí** o **No**.  
  
    -   **Sí**: el archivo de solución y los archivos de sus proyectos modificables se convierten a los formatos usados por la versión de Visual Studio instalada en el equipo. Si la solución convertida está almacenada bajo control de código fuente, se desprotege en la unidad local y se abre para su edición.  
  
    -   **No**: la solución y sus proyectos no se convierten, no se desprotegen del control de código fuente y no se abren.  
  
 Si forma parte de un equipo de desarrollo, todos los usuarios que estén trabajando en una solución deben tener la misma versión de Visual Studio instalada en sus máquinas locales. Para asegurarse de que las soluciones y los proyectos sean accesibles, comuníquese periódicamente con su equipo.  
  
## Vea también  
 [Project Dependencies Dialog Box](http://msdn.microsoft.com/es-es/d66e48c3-3722-40dd-99b4-53d93cac128e)   
 [Compilar aplicaciones en Visual Studio](../ide/compiling-and-building-in-visual-studio.md)