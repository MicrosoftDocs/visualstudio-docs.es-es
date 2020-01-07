---
title: Análisis de código para código administrado
ms.date: 06/12/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f32cf357cadafd6d5dd8166c23de15a16a8e502c
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587764"
---
# <a name="overview-of-code-analysis-for-managed-code-in-visual-studio"></a>Información general sobre el análisis de código para código administrado en Visual Studio

Visual Studio puede realizar análisis de código de código administrado de dos maneras: con el [análisis heredado](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), también conocido como análisis estático de FxCop de ensamblados administrados, y con los [analizadores de código](../code-quality/roslyn-analyzers-overview.md)más modernos basados en .net Compiler Platform. Los analizadores de código basados en .NET Compiler Platform, que analizan el código en directo a medida que escribe, reemplazan el análisis de código estático de FxCop heredado, que solo analiza el código compilado.

## <a name="see-also"></a>Vea también

- [Información general de los analizadores basados en .NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md)
