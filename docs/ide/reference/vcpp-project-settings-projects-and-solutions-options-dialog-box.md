---
title: "Configuraci&#243;n de proyecto de VC++, Proyectos y soluciones, Opciones (Cuadro de di&#225;logo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Projects.VCBuild"
helpviewer_keywords: 
  - "compilaciones [Visual Studio], registros"
  - "proceso de compilación [C++]"
  - "archivos [Visual Studio], generados con el compilador de C/C++"
  - "extensiones de archivos, generados con el compilador de C/C++"
  - "compilador cl.exe, extensiones de archivo"
  - "extensiones, generados con el compilador de C o C++"
  - "BuildLog.htm"
ms.assetid: 56420efd-6a95-464e-b890-e2b38c48d66a
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Configuraci&#243;n de proyecto de VC++, Proyectos y soluciones, Opciones (Cuadro de di&#225;logo)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Este cuadro de diálogo permite definir la configuración del proyecto de [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] relacionada con el registro de compilación y los tipos de archivos auxiliares.  
  
### Para obtener acceso a este cuadro de diálogo  
  
1.  En el menú **Herramientas**, haga clic en **Opciones**.  
  
2.  Seleccione **Proyectos y soluciones** y, a continuación, seleccione **Configuración de proyecto de VC\+\+**.  
  
## Ruta de búsqueda de personalizaciones de compilación  
 Especifica la lista de directorios que contienen archivos .rules, que ayudan a definir reglas de compilación para los proyectos.  
  
## Registro de compilación  
 **Sí**  
 Habilita la generación del archivo de registro de compilación.  Esta opción genera BuildLog.htm, que se encuentra en el directorio de archivos intermedios del proyecto.  Cada compilación nueva sobrescribe el archivo BuildLog.htm anterior.  
  
 **No**  
 Desactiva la generación del archivo de registro de compilación.  
  
## Tiempo de compilación  
 **Sí**  
 Activa el registro de compilación.  Si se selecciona, se muestra en la ventana de salida el tiempo que se tarda en completar la compilación.  Para obtener más información, vea [Resultados \(Ventana\)](../../ide/reference/output-window.md).  
  
 **No**  
 Desactiva el registro de compilación.  
  
## Extensiones para ocultar  
 Especifica las extensiones de nombre de archivo de los archivos que no aparecerán en el **Explorador de soluciones** cuando esté habilitada la opción **Mostrar todos los archivos**.  
  
## Extensiones para incluir  
 Especifica las extensiones de nombre de archivo de los archivos que se pueden importar al proyecto.  
  
## Máximo de compilaciones de C\+\+ concurrentes  
 Especifica el número máximo de núcleos de CPU que se usarán para la compilación paralela de C\+\+.  
  
## Mostrar entorno en el registro  
 **Sí**  
 Muestra las variables de entorno en el archivo de registro de compilación.  Esta opción especifica que se muestren todas las variables de entorno en el archivo de registro de compilación durante las compilaciones de proyectos de [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].  
  
 **No**  
 Las variables de entorno se excluyen del archivo de registro de compilación.  
  
## Modo Explorador de soluciones  
 **Mostrar únicamente archivos del proyecto**  
 Configura el **Explorador de soluciones** de modo que solo muestre archivos del proyecto.  
  
 **Mostrar todos los archivos**  
 Configura el **Explorador de soluciones** de modo que muestre tanto archivos del proyecto como archivos del disco en la carpeta del proyecto.  
  
## Vea también  
 [Compilar programas de C\/C\+\+](/visual-cpp/build/building-c-cpp-programs)   
 [Referencia de compilación de C\/C\+\+](/visual-cpp/build/reference/c-cpp-building-reference)