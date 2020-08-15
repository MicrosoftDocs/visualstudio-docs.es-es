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
ms.openlocfilehash: 901c66a97a763345ee32b1a1540a7998934d0ff3
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2020
ms.locfileid: "88248983"
---
# <a name="overview-of-code-analysis-for-managed-code-in-visual-studio"></a>Información general sobre el análisis de código para código administrado en Visual Studio

Visual Studio puede realizar análisis de código de código administrado de dos maneras: con el [análisis heredado](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), también conocido como análisis estático de FxCop de ensamblados administrados, y con los [analizadores de código más modernos basados en .net Compiler Platform](../code-quality/roslyn-analyzers-overview.md). Los analizadores de código basados en .NET Compiler Platform, que analizan el código en directo a medida que escribe, reemplazan el análisis de código estático de FxCop heredado, que solo analiza el código compilado.
