---
title: "No se pudieron convertir uno o m&#225;s proyectos. Estos proyectos est&#225;n marcados como no cargados y no disponibles en el explorador de soluciones. Vuelva a cargar estos proyectos para determinar la causa del error. | Microsoft Docs"
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
  - "vs.projectmigrationsfailed"
ms.assetid: c2fd3bbd-15f0-4b30-97f5-59abeae02141
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# No se pudieron convertir uno o m&#225;s proyectos. Estos proyectos est&#225;n marcados como no cargados y no disponibles en el explorador de soluciones. Vuelva a cargar estos proyectos para determinar la causa del error.
Ha intentado abrir una solución que contiene uno o varios proyectos que se crearon en una versión anterior de Visual Studio. Algunos proyectos no se pudieron convertir y se marcarán como \(no disponibles\) en el Explorador de soluciones. Para poder abrir la solución y editarla, y para poder usar los proyectos reparados en la versión de Visual Studio instalada en el equipo, hay que convertir los proyectos a los formatos actuales.  
  
### Para responder a este mensaje  
  
1.  Seleccione **Sí** para cerrar el cuadro de diálogo.  
  
     Los proyectos que no se pudieron convertir se marcan como **\(no disponibles\)** en el Explorador de soluciones.  
  
2.  Vuelva a cargar los proyectos que no se pudieron convertir.  
  
    1.  En el Explorador de soluciones, seleccione cada proyecto de la solución activa que esté marcado como **\(no disponible\)**.  
  
    2.  En el menú **Proyecto**, elija **Volver a cargar el proyecto**.  
  
3.  Revise cuidadosamente los mensajes de error que muestren información sobre problemas de los proyectos. Entre los posibles problemas se incluyen los siguientes:  
  
    1.  El proyecto es de solo lectura. Los proyectos de solo lectura no se convierten. Solo los usuarios con permiso para editarlos pueden convertir estos proyectos.  
  
    2.  El proyecto ya está desprotegido exclusivamente para otro usuario. Ese usuario debe proteger el proyecto de nuevo antes de que se pueda desproteger.  
  
    3.  El proyecto no se pudo desproteger desde un servidor de red. Confirme las condiciones de red y vuelva a intentarlo.  
  
    4.  El proyecto está dañado y debe volver a compilarse.  
  
4.  Aborde los problemas indicados cuando intente volver a cargar los proyectos que se han marcado como **\(no disponibles\)**.  
  
5.  Vuelva a abrir y convierta estos proyectos. Es posible que quiera realizar copias de seguridad de los archivos de proyecto antes de convertirlos.  
  
    > [!NOTE]
    >  A medida que determinados tipos de proyecto se convierten, por ejemplo los proyectos de Visual C\+\+, los archivos de proyecto antiguos se marcan con la extensión de archivo .old y se guardan en el directorio del proyecto.  
  
 Si forma parte de un equipo de desarrollo, todos los usuarios que estén trabajando en un proyecto deben tener la misma versión de Visual Studio instalada en sus equipos locales. Para asegurarse de que el proyecto siga siendo accesible, comuníquese periódicamente con su equipo.  
  
> [!CAUTION]
>  Si los proyectos de la solución están almacenados bajo control de código fuente e intenta volver a proteger los proyectos convertidos, primero determine si alguna otra solución comparte alguno de estos proyectos. No proteja proyectos convertidos que todavía se estén usando en soluciones no convertidas. Esto rompería las dependencias entre esas soluciones y les impediría abrirse o compilarse correctamente.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Cómo descargar y volver a cargar proyectos](http://msdn.microsoft.com/es-es/abc0155b-8fcb-4ffc-95b6-698518a7100b)   
 [Project Dependencies Dialog Box](http://msdn.microsoft.com/es-es/d66e48c3-3722-40dd-99b4-53d93cac128e)   
 [Compilar aplicaciones en Visual Studio](../ide/compiling-and-building-in-visual-studio.md)