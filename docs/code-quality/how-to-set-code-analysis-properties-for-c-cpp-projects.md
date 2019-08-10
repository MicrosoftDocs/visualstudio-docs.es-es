---
title: Procedimiento Establecer las propiedades de análisis de código de proyectos de C/C++
ms.date: 11/04/2016
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
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 72866618383382389ad5e5706ae2a0999c89c346
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923986"
---
# <a name="how-to-set-code-analysis-properties-for-cc-projects"></a>Procedimiento Establecer las propiedades de análisis de código de proyectos de C/C++
Puede configurar las reglas que utiliza la herramienta de análisis de código para analizar el código en cada configuración del proyecto. Además, puede dirigir el análisis de código para suprimir las advertencias del código generado y agregado al proyecto mediante una herramienta de terceros.

## <a name="code-analysis-property-page"></a>Página de propiedades análisis de código
La página de propiedades **análisis de código** contiene todas las opciones de configuración de análisis de código para un proyecto. Para abrir la página de propiedades análisis de código de un proyecto de **Explorador de soluciones**, haga clic con el botón secundario en el proyecto y, a continuación, haga clic en **propiedades**. A continuación, expanda **propiedades de configuración** y seleccione la pestaña **análisis de código** .

## <a name="project-configuration-and-platform"></a>Configuración y plataforma del proyecto
La lista de **configuración** y la lista de **plataformas** le permiten aplicar una configuración de análisis de código diferente a distintas combinaciones de plataforma y configuración de proyecto. Por ejemplo, puede dirigir el análisis de código para aplicar un conjunto de reglas al proyecto para las compilaciones de depuración y un conjunto diferente para las compilaciones de versión.

## <a name="enabling-code-analysis"></a>Habilitar el análisis de código
Puede decidir si desea habilitar el análisis de código para el proyecto seleccionando **Habilitar análisis de código paraC++ C/en la compilación**. En combinación con la lista de **configuración** , puede, por ejemplo, decidir deshabilitar el análisis de código para las compilaciones de depuración y habilitarlo para las compilaciones de versión.

Si el proyecto contiene código administrado, puede decidir si desea habilitar o deshabilitar el análisis de código seleccionando **Habilitar análisis de código**al compilar.

El análisis de código está diseñado para ayudarle a mejorar la calidad del código y evitar errores comunes. Por lo tanto, considere detenidamente si desea deshabilitar el análisis de código. Normalmente, es mejor deshabilitar los conjuntos de reglas o las reglas individuales que no desea que se apliquen al proyecto.

## <a name="generated-code"></a>Código generado
Los desarrolladores suelen usar herramientas para ayudar a desarrollar aplicaciones rápidamente. Estas herramientas pueden generar código que se agrega al proyecto. Es posible que desee ver las infracciones de las reglas que el análisis de código detecta en el código generado. Sin embargo, es posible que no desee verlas si no desea mantener el código.

La casilla **suprimir resultados de código generado** en la página propiedades **generales** le permite seleccionar si desea ver las advertencias de análisis de código del código administrado generado por una herramienta de terceros.

## <a name="rule-sets"></a>Conjuntos de reglas
Si el proyecto contiene código administrado, puede seleccionar las reglas que se aplicarán en un análisis de código seleccionando un conjunto de reglas en la lista **ejecutar este conjunto de reglas** .

## <a name="see-also"></a>Vea también

- [Analizar la calidad del código administrado](../code-quality/code-analysis-for-managed-code-overview.md)
- [Análisis de código para advertencias de C/C++](../code-quality/code-analysis-for-c-cpp-warnings.md)