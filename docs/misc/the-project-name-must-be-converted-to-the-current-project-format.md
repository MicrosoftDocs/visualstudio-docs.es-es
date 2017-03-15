---
title: "El proyecto &lt;name&gt; se debe convertir al formato de proyecto actual. | Microsoft Docs"
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
  - "VC.Project.Conversion7"
  - "vs.UpgradeWarningDlg"
ms.assetid: e27d58e5-c270-468b-bb98-3163d40900bc
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# El proyecto &lt;name&gt; se debe convertir al formato de proyecto actual.
Ha abierto un proyecto que se creó en una versión anterior de Visual Studio. Para poder abrir un proyecto y editarlo en la versión de Visual Studio instalada en el equipo, hay que convertir los archivos de proyecto a los formatos actuales. Puede decidir si quiere convertir este proyecto ahora o no. Las conversiones de formato no se pueden deshacer.  
  
> [!CAUTION]
>  Si el proyecto está almacenado bajo control de código fuente e intenta volver a protegerlo, averigüe primero si alguna otra solución lo comparte. No proteja un proyecto recién convertido que todavía se esté usando en otras soluciones no convertidas. Esto rompería las dependencias entre esas soluciones y les impediría abrirse o compilarse correctamente.  
  
 Es posible que quiera realizar copias de seguridad de los archivos de proyecto antes de convertirlos.  
  
> [!NOTE]
>  A medida que determinados tipos de proyecto se convierten \(por ejemplo, los proyectos de Visual C\+\+\), los archivos de proyecto antiguos se marcan con la extensión de archivo ".old" y se guardan en el directorio del proyecto.  
  
 Los proyectos de solo lectura no se convierten. Solo los usuarios con permiso para editarlos pueden convertir estos proyectos. Para que un proyecto se pueda usar en una solución convertida, sus archivos de proyecto se deben convertir a los formatos actuales. Después de convertir un proyecto, ya no se puede editar, compilar ni ejecutar ninguna solución que incluya ese proyecto en las versiones anteriores de Visual Studio.  
  
### Para responder a este mensaje  
  
1.  Seleccione **Sí** o **No**.  
  
    -   **Sí:** si el proyecto es editable, se convierte al formato usado por la versión de Visual Studio instalada en el equipo. Si el proyecto convertido está almacenado bajo control de código fuente, se desprotege en la unidad local y se abre para poder editarlo.  
  
    -   **No:** el proyecto no se convierte, no se desprotege del control de código fuente y no se abre.  
  
 Si forma parte de un equipo de desarrollo, todos los usuarios que estén trabajando en un proyecto deben tener la misma versión de Visual Studio instalada en sus equipos locales. Para asegurarse de que el proyecto siga siendo accesible, comuníquese periódicamente con su equipo.  
  
## Vea también  
 [Project Dependencies Dialog Box](http://msdn.microsoft.com/es-es/d66e48c3-3722-40dd-99b4-53d93cac128e)   
 [Compilar aplicaciones en Visual Studio](../ide/compiling-and-building-in-visual-studio.md)