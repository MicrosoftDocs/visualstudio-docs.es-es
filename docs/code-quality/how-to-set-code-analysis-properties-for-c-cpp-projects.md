---
title: "Cómo: establecer propiedades de análisis de código para proyectos de C/C ++ | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b2ad22eccb561bf58ee845d58268620aad778a20
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2017
---
# <a name="how-to-set-code-analysis-properties-for-cc-projects"></a>Cómo: Establecer propiedades de análisis de código para proyectos de C/C++
Puede configurar las reglas que usa la herramienta de análisis de código para analizar el código en cada configuración del proyecto. Además, puede dirigir el análisis de código para suprimir las advertencias de código que se ha generado y agregado al proyecto una herramienta de terceros.  
  
## <a name="code-analysis-property-page"></a>Página de propiedades de análisis de código  
 El **análisis de código** página de propiedades contiene todos los valores de configuración de análisis de código para un proyecto. Para abrir la página de propiedades de análisis de código para un proyecto en **el Explorador de soluciones**, haga clic en el proyecto y, a continuación, haga clic en **propiedades**. A continuación, expanda **propiedades de configuración** y seleccione la **análisis de código** ficha.  
  
## <a name="project-configuration-and-platform"></a>Plataforma y la configuración de proyecto  
 El **configuración** lista y **plataforma** lista le permite aplicar la configuración de análisis de código diferentes a las combinaciones de configuración y plataforma de proyecto diferente. Por ejemplo, puede dirigir compilaciones de análisis de código para un conjunto de reglas se aplican a su proyecto para la depuración y compila un conjunto diferente de la versión.  
  
## <a name="enabling-code-analysis"></a>Habilitar análisis de código  
 Puede decidir si desea habilitar análisis de código para el proyecto seleccionando **Habilitar análisis de código de C ++ en la compilación**. En combinación con la **configuración** lista, por ejemplo, podría decidir deshabilitar el análisis de código para compilaciones de depuración y habilitar para la versión compilaciones.  
  
 Si el proyecto contiene código administrado, puede decidir si desea habilitar o deshabilitar el análisis de código seleccionando **Habilitar análisis de código al compilar**.  
  
 Análisis de código está diseñado para ayudarle a mejorar la calidad del código y evitar errores habituales. Por lo tanto, considere detenidamente si desea deshabilitar el análisis de código. Es mejor deshabilitar conjuntos de reglas o reglas individuales que no desea que se aplican a su proyecto.  
  
## <a name="generated-code"></a>Código generado  
 Los desarrolladores utilizan a menudo herramientas para ayudar a desarrollar aplicaciones rápidamente. Estas herramientas pueden generar código que se agrega al proyecto. Puede ver las infracciones de reglas que el análisis de código detecta en el código generado. Sin embargo, no puede verlos si no desea mantener el código.  
  
 El **Suprimir resultados del código generado** casilla de verificación en la **General** permite seleccionar si desea ver las advertencias de análisis de código desde el código administrado que se genera mediante una herramienta de terceros de la página de propiedades .  
  
## <a name="rule-sets"></a>Conjuntos de reglas  
 Si el proyecto contiene código administrado, puede seleccionar las reglas que se aplicará en un análisis de código seleccionando un conjunto de reglas de la **ejecutar este conjunto de reglas** lista.  
  
## <a name="see-also"></a>Vea también  
 [Analizar la calidad del código administrado](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [Análisis de código para advertencias de C/C++](../code-quality/code-analysis-for-c-cpp-warnings.md)