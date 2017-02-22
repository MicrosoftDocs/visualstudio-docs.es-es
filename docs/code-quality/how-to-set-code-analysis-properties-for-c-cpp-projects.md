---
title: "C&#243;mo: Establecer propiedades de an&#225;lisis de c&#243;digo para proyectos de C/C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.propertypages.native"
  - "VC.Project.VCCLCompilerTool.EnablePrefast"
  - "VC.Project.VCFxCopTool.EnablePREfast"
  - "VC.Project.VCFxCopTool.IgnoreGeneratedCode"
helpviewer_keywords: 
  - "propiedades de análisis de código C/C++"
  - "propiedades de análisis de código"
  - "propiedades, análisis de código C/C++"
  - "propiedades, análisis de código"
ms.assetid: 7af52097-6d44-4785-9b9f-43b7a7d447d7
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# C&#243;mo: Establecer propiedades de an&#225;lisis de c&#243;digo para proyectos de C/C++
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Pueden configurarse las reglas que utiliza la herramienta de análisis de código para analizar el código en cada configuración de un proyecto.  Además, el análisis de código puede dirigirse para suprimir las advertencias de código generado y agregado al proyecto por una herramienta de otro fabricante.  
  
## Página de propiedades del análisis de código  
 La página de propiedades de **Análisis de código** contiene la configuración completa de análisis de código para un proyecto.  Para abrir la página de propiedades del análisis de código para un proyecto en el **Explorador de soluciones**, haga clic con el botón secundario del mouse en el proyecto y después haga clic en **Propiedades**.  A continuación, expanda **Propiedades de configuración** y seleccione la ficha **Análisis de código**.  
  
## Configuración y plataforma del proyecto  
 La lista **Configuración** y la lista **Plataforma** permiten aplicar diferentes valores de análisis de código a diferentes combinaciones de configuración y plataformas del proyecto.  Por ejemplo, puede dirigir el análisis de código con el fin de aplicar un conjunto de reglas al proyecto para las compilaciones de depuración y un conjunto diferente para las compilaciones de versión.  
  
## Habilitar el análisis de código  
 Para decidir si habilita el análisis de código para un proyecto, seleccione **Habilitar análisis de código para C\/C\+\+ al compilar**.  En combinación con la lista **Configuración**, puede, por ejemplo, optar por deshabilitar el análisis de código para las versiones de depuración y habilitarlo para las versiones de lanzamiento.  
  
 Si su proyecto contiene código administrado, para habilitar o deshabilitar el análisis de código, seleccione **Habilitar análisis de código al compilar**.  
  
 El análisis de código se ha diseñado para mejorar la calidad del código y evitar los errores comunes.  Por consiguiente, considere cuidadosamente si desea deshabilitarlo.  Normalmente es mejor deshabilitar conjuntos de reglas o reglas individuales que no desea aplicar al proyecto.  
  
## Código generado  
 Los desarrolladores utilizan a menudo herramientas como ayuda para desarrollar rápidamente las aplicaciones.  Estas herramientas pueden generar código que se agrega al proyecto.  Quizá desee ver las infracciones de reglas que el análisis de código detecta en el código generado.  Sin embargo, es posible que no le interese verlas si no desea mantener el código.  
  
 La casilla **Suprimir resultados del código generado** en la página de propiedades **General** le permite seleccionar si desea ver las advertencias del análisis de código referentes al código administrador que genera una herramienta de otro fabricante.  
  
## Conjuntos de reglas  
 Si el proyecto contiene el código administrado, puede seleccionar las reglas que desea aplicar en un análisis de código seleccionando un conjunto de reglas en la lista **Ejecutar este conjunto de reglas**.  
  
## Vea también  
 [Analizar la calidad del código administrado](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [Advertencias de análisis de código de C\/C\+\+](../code-quality/code-analysis-for-c-cpp-warnings.md)