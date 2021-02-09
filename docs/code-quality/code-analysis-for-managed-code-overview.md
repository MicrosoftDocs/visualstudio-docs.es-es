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
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 542747f650888b384a9f9c4910b0d9caea93e948
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860573"
---
# <a name="overview-of-code-analysis-for-net-in-visual-studio"></a>Información general sobre el análisis de código para .NET en Visual Studio

Visual Studio puede realizar análisis de código de código administrado de dos maneras: con el [análisis heredado](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), también conocido como análisis estático de FxCop de ensamblados administrados, y con los [analizadores de código más modernos basados en .net Compiler Platform](../code-quality/roslyn-analyzers-overview.md). Los analizadores de código basados en .NET Compiler Platform, que analizan el código en directo a medida que escribe, reemplazan el análisis de código estático de FxCop heredado, que solo analiza el código compilado.
