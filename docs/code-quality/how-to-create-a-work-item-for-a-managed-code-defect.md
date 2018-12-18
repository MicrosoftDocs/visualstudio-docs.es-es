---
title: 'Cómo: Crear un elemento de trabajo para defectos de código administrado'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- managed code, creating work items for code defects
- code analysis, creating work items
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: b251970bfd57b31842e1573e2e156e11a517c81a
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44279482"
---
# <a name="how-to-create-a-work-item-for-a-managed-code-defect"></a>Cómo: Crear un elemento de trabajo para defectos de código administrado

Puede usar la característica de seguimiento de elemento de trabajo para registrar el elemento de trabajo de Visual Studio. Para usar esta característica, el proyecto debe formar parte de un proyecto de DevOps de Azure en [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)].

## <a name="to-create-a-work-item-for-managed-code-defect"></a>Para crear un elemento de trabajo para defectos de código administrado

1. En el **análisis de código** ventana, seleccione la advertencia.

2. Elija **acciones**, a continuación, elija **crear elemento de trabajo** y elija el tipo de elemento de trabajo que se creará.

     Se crea un nuevo elemento de trabajo para que especificar la información de defectos.

## <a name="to-create-a-work-item-for-multiple-managed-code-defects"></a>Para crear un elemento de trabajo para varios defectos de código administrado

1. En el **lista de errores**, seleccione varias advertencias y, a continuación, haga clic en las advertencias.

2. Seleccione **crear elemento de trabajo** y haga clic en el tipo de elemento de trabajo que se creará.

     Se crea un elemento de trabajo único para todas las advertencias seleccionadas para especificar la información del error.