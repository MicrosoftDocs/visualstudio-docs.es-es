---
title: "C&#243;mo: Ver, guardar y configurar archivos de registro de compilaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 75d38b76-26d6-4f43-bbe7-cbacd7cc81e7
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# C&#243;mo: Ver, guardar y configurar archivos de registro de compilaci&#243;n
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Después de compilar un proyecto en el IDE de Visual Studio, puede ver información sobre esa compilación en la ventana **Resultado**.  Con esta información, puede, por ejemplo, solucionar un error de compilación.  Para los proyectos de C\+\+, también puede ver la misma información en un archivo de .txt crear y se guarda automáticamente.  Para los proyectos de código administrado, puede copiar y pegar la información de la ventana **Resultado** en un archivo de .txt y guardarla personalmente.  También puede utilizar el IDE para especificar qué tipo de información desea ver sobre cada compilación.  
  
 Si compila cualquier tipo de proyecto mediante MSBuild, puede crear un archivo de .txt para almacenar información sobre la compilación.  Para obtener más información, vea [Obtener registros de compilación](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
### Para ver el archivo de registro de compilación para el proyecto de c\+\+.  
  
1.  En **Explorador de Windows** o **Explorador de archivos**, abra el archivo siguiente: \\…  \\visual \\Visual Studio *Versión*\\Projects \\*ProjectName*\\*ProjectName*\\Debug \\*ProjectName*.txt  
  
### Para crear un archivo de registro de compilación de un proyecto de código administrado  
  
1.  En la barra de menú, elija **Compilar**, **Compilar solución**.  
  
2.  En la ventana **Resultado**, resalte la información de compilación y, a continuación cópiela en el portapapeles.  
  
3.  Abra un editor de texto, como Bloc de notas, pegar la información en el archivo y, a continuación guardar.  
  
### Para cambiar la cantidad de información se incluye en el registro de compilación  
  
1.  En la barra de menú, elija **herramientas**, **opciones**.  
  
2.  En la página **Proyectos y soluciones**, elija la página **Generar y ejecutar**.  
  
3.  En la lista **Contenido de los resultados de compilación del proyecto de MSBuild**, elija uno de los valores siguientes, y elija el botón **Aceptar**.  
  
    |Nivel de detalle|Descripción|  
    |----------------------|-----------------|  
    |No interactivo|Muestra un resumen de la compilación solo.|  
    |Minimal|Muestra un resumen de la compilación y errores, las advertencias, los mensajes que se clasifican como muy importantes.|  
    |Normal|Muestra un resumen de la compilación; errores, advertencias, y mensajes que se clasifican como muy importantes; y los principales pasos de compilación.  Utilizará este nivel de detalle con más frecuencia.|  
    |Detailed|Muestra un resumen de la compilación; errores, advertencias, y mensajes que se clasifican como muy importantes; todos los pasos de compilación; y mensajes que se clasifican a partir de importancia normal.|  
    |Diagnóstico|Muestra todos los datos que esté disponible para la compilación.  Puede utilizar este nivel de detalle para ayudar a depurar los problemas con los scripts y otro de compilación personalizada los problemas de compilación.|  
  
     Para obtener más información, vea [Cuadro de diálogo Opciones, Proyectos y soluciones, Compilar y ejecutar](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md) y <xref:Microsoft.Build.Framework.LoggerVerbosity>.  
  
    > [!IMPORTANT]
    >  Debe recompilar el proyecto para que los cambios surtan efecto en la ventana **Resultado** \(todos los proyectos\) y el archivo de *ProjectName*.txt \(proyectos de C\+\+ solo\).  
  
## Vea también  
 [Obtener registros de compilación](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Compilar y limpiar proyectos y soluciones en Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)   
 [Compilar aplicaciones en Visual Studio](../ide/compiling-and-building-in-visual-studio.md)