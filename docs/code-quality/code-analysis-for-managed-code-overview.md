---
title: Análisis de código para código administrado
ms.date: 08/27/2020
description: Obtenga información sobre los analizadores de código basados en .NET Compiler Platform en Visual Studio. Comprenda por qué estos analizadores reemplazan el análisis estático de FxCop de los ensamblados administrados.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 643e8457dbbe838d593a7bad38064537b6cbe57d
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2020
ms.locfileid: "94348533"
---
# <a name="overview-of-code-analysis-for-net-in-visual-studio"></a>Información general sobre el análisis de código para .NET en Visual Studio

Visual Studio puede realizar análisis de código de código administrado de dos maneras: con el [análisis heredado](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), también conocido como análisis estático de FxCop de ensamblados administrados, y con los [analizadores de código más modernos basados en .net Compiler Platform](../code-quality/roslyn-analyzers-overview.md). Los analizadores de código basados en .NET Compiler Platform, que analizan el código en directo a medida que escribe, reemplazan el análisis de código estático de FxCop heredado, que solo analiza el código compilado.
