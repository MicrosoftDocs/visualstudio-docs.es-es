---
title: Análisis de código para código administrado
ms.date: 06/12/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a44465b5f3daf89e915a5f6f5e7abe6c856598e5
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69546923"
---
# <a name="overview-of-code-analysis-for-managed-code-in-visual-studio"></a>Información general sobre el análisis de código para código administrado en Visual Studio

Visual Studio puede realizar análisis de código de código administrado de dos maneras: con el [análisis heredado](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), también conocido como análisis estático de FxCop de ensamblados administrados, y con los analizadores de [código](../code-quality/roslyn-analyzers-overview.md)más modernos basados en .net Compiler Platform. Los analizadores de código basados en .NET Compiler Platform, que analizan el código en directo a medida que escribe, reemplazan el análisis de código estático de FxCop heredado, que solo analiza el código compilado.

## <a name="see-also"></a>Vea también

- [Información general de los analizadores basados en .NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md)
