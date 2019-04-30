---
title: Procedimiento Crear un elemento de trabajo para defectos de código administrado
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed code, creating work items for code defects
- code analysis, creating work items
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: e2e55ddf51e0c81f57c504e398c23c8e1d3f721a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62816679"
---
# <a name="how-to-create-a-work-item-for-a-managed-code-defect"></a>Procedimiento Crear un elemento de trabajo para defectos de código administrado

Puede usar la característica de seguimiento de elemento de trabajo para registrar el elemento de trabajo de Visual Studio. Para usar esta característica, el proyecto debe formar parte de un proyecto de DevOps de Azure en [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)].

## <a name="to-create-a-work-item-for-managed-code-defect"></a>Para crear un elemento de trabajo para defectos de código administrado

1. En el **análisis de código** ventana, seleccione la advertencia.

2. Elija **acciones**, a continuación, elija **crear elemento de trabajo** y elija el tipo de elemento de trabajo que se creará.

     Se crea un nuevo elemento de trabajo para que especificar la información de defectos.

## <a name="to-create-a-work-item-for-multiple-managed-code-defects"></a>Para crear un elemento de trabajo para varios defectos de código administrado

1. En el **lista de errores**, seleccione varias advertencias y, a continuación, haga clic en las advertencias.

2. Seleccione **crear elemento de trabajo** y haga clic en el tipo de elemento de trabajo que se creará.

     Se crea un elemento de trabajo único para todas las advertencias seleccionadas para especificar la información del error.