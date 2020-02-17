---
title: 'Cómo: establecer propiedades de análisis de código paraC++ proyectos de C | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.native
- VC.Project.VCCLCompilerTool.EnablePrefast
- VC.Project.VCFxCopTool.EnablePREfast
- VC.Project.VCFxCopTool.IgnoreGeneratedCode
helpviewer_keywords:
- properties, C/C++ Code Analysis
- properties, Code Analysis
- code analysis properties
- C/C++ code analysis properties
ms.assetid: 7af52097-6d44-4785-9b9f-43b7a7d447d7
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: b2fb3cb81b49fd4b8cc83e0548110d2025c7488d
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2020
ms.locfileid: "77277986"
---
# <a name="how-to-set-code-analysis-properties-for-cc-projects"></a>Cómo: Establecer propiedades de análisis de código para proyectos de C/C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede configurar las reglas que utiliza la herramienta de análisis de código para analizar el código en cada configuración del proyecto. Además, puede dirigir el análisis de código para suprimir las advertencias del código generado y agregado al proyecto mediante una herramienta de terceros.  
  
## <a name="code-analysis-property-page"></a>Página de propiedades análisis de código  
 La página de propiedades **análisis de código** contiene todas las opciones de configuración de análisis de código para un proyecto. Para abrir la página de propiedades análisis de código de un proyecto de **Explorador de soluciones**, haga clic con el botón secundario en el proyecto y, a continuación, haga clic en **propiedades**. A continuación, expanda **propiedades de configuración** y seleccione la pestaña **análisis de código** .  
  
## <a name="project-configuration-and-platform"></a>Configuración y plataforma del proyecto  
 La lista de **configuración** y la lista de **plataformas** le permiten aplicar una configuración de análisis de código diferente a distintas combinaciones de plataforma y configuración de proyecto. Por ejemplo, puede dirigir el análisis de código para aplicar un conjunto de reglas al proyecto para las compilaciones de depuración y un conjunto diferente para las compilaciones de versión.  
  
## <a name="enabling-code-analysis"></a>Habilitar el análisis de código  
 Puede decidir si desea habilitar el análisis de código para el proyecto seleccionando **Habilitar análisis de código paraC++ C/en la compilación**. En combinación con la lista de **configuración** , puede, por ejemplo, decidir deshabilitar el análisis de código para las compilaciones de depuración y habilitarlo para las compilaciones de versión.  
  
 Si el proyecto contiene código administrado, puede decidir si desea habilitar o deshabilitar el análisis de código seleccionando **Habilitar análisis de código al compilar**.  
  
 El análisis de código está diseñado para ayudarle a mejorar la calidad del código y evitar errores comunes. Por lo tanto, considere detenidamente si desea deshabilitar el análisis de código. Normalmente, es mejor deshabilitar los conjuntos de reglas o las reglas individuales que no desea que se apliquen al proyecto.  
  
## <a name="generated-code"></a>Código generado  
 Los desarrolladores suelen usar herramientas para ayudar a desarrollar aplicaciones rápidamente. Estas herramientas pueden generar código que se agrega al proyecto. Es posible que desee ver las infracciones de las reglas que el análisis de código detecta en el código generado. Sin embargo, es posible que no desee verlas si no desea mantener el código.  
  
 La casilla **suprimir resultados de código generado** en la página propiedades **generales** le permite seleccionar si desea ver las advertencias de análisis de código del código administrado generado por una herramienta de terceros.  
  
## <a name="rule-sets"></a>Conjuntos de reglas  
 Si el proyecto contiene código administrado, puede seleccionar las reglas que se aplicarán en un análisis de código seleccionando un conjunto de reglas en la lista **ejecutar este conjunto de reglas** .  
  
## <a name="see-also"></a>Consulte también  
 [Analizar la calidad del código administrado](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [Análisis de código para advertencias de C/C++](../code-quality/code-analysis-for-c-cpp-warnings.md)
