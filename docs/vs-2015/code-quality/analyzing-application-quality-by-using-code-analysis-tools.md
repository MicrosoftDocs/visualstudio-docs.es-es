---
title: Analyzing Application Quality by Using Code Analysis Tools | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.analysisresults
helpviewer_keywords:
- application quality, analyzing
- code analysis
- team-based development, analyzing application quality
ms.assetid: 21680516-ddb5-446d-90d4-19d94f6ec699
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8b85bbad909a05bacab361a49cc7e029482ad606
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74291199"
---
# <a name="analyzing-application-quality-by-using-code-analysis-tools"></a>Analizar la calidad de la aplicación mediante herramientas de análisis del código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In This Section [Analyzing Managed Code Quality](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md) Visual Studio code analysis for managed code provides information about managed assemblies, such as violations of the programming and design rules set forth in the Microsoft .NET Framework Design Guidelines. Los mensajes de advertencia identifican cualquier problema pertinente de programación y diseño y, cuando es posible, proporcionan información sobre la solución del problema.

 [Analyzing C/C++ Code Quality by Using Code Analysis](../code-quality/analyzing-c-cpp-code-quality-by-using-code-analysis.md) The C/C++ Code Analysis tool provides information to developers about possible defects in their C/C++ source code. Entre los errores de codificación más comunes detectados por esta herramienta, destacan las saturaciones de búfer, los casos de memoria no inicializada, la desreferenciación del puntero NULL, así como las pérdidas de memoria y recursos.

 [Using Rule Sets to Group Code Analysis Rules](../code-quality/using-rule-sets-to-group-code-analysis-rules.md) Select and create *rule sets* to apply to your project.

 [Code Analysis Application Errors](../code-quality/code-analysis-application-errors.md) Fix errors in the code analysis functionality.

 [Enhancing Code Quality with Team Project Check-in Policies](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md) When you use Team Foundation Version Control (TFVC), you can create check-in policies for your team projects that enforce practices that lead to better code and more efficient group development. Las directivas de protección son reglas que se establecen en el nivel del proyecto de equipo y cuya implantación es obligatoria en los equipos de los desarrolladores antes de que el código pueda protegerse.

### <a name="code-analysis-for-drivers"></a>Análisis de código para controladores
 Las herramientas de análisis de código pueden ayudar a mejorar la estabilidad y confiabilidad del controlador analizando sistemáticamente el código fuente del controlador.

 [Analyzing Driver Quality by Using Code Analysis Tools](/windows-hardware/drivers/devtest/tools-for-verifying-drivers) Code Analysis for Drivers is a compile-time static verification tool that detects basic coding errors in C and C++ programs and includes a specialized module that is designed to detect errors in (primarily) kernel-mode driver code. El comprobador de controladores estático (Static Driver Verifier, SDV) es una herramienta de comprobación estática que analiza sistemáticamente el código fuente de los controladores en modo kernel de Windows. El SDV determina si el controlador interactúa correctamente con el kernel del sistema operativo de Windows.

 [Code Analysis for Drivers Warnings](https://go.microsoft.com/fwlink/?LinkId=225920) Describes the warnings that the Code Analysis for Drivers reports when it detects a possible error in driver code.

## <a name="related-tasks"></a>Tareas relacionadas
 [Measuring Complexity and Maintainability of Managed Code](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md) Insert description here.

 [Unit Test Your Code](../test/unit-test-your-code.md) Insert description here.
