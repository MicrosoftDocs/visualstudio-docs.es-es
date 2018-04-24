---
title: 'Cómo: Crear un elemento de trabajo para defectos de código administrado'
ms.date: 11/04/2016
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
ms.openlocfilehash: 41e4a507015a630eb31c86048e785ea179899ccf
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-create-a-work-item-for-a-managed-code-defect"></a>Cómo: Crear un elemento de trabajo para defectos de código administrado

Puede usar la característica de seguimiento de elemento de trabajo para registrar el elemento de trabajo de Visual Studio. Para usar esta característica, el proyecto debe formar parte del proyecto de equipo [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)].

## <a name="to-create-a-work-item-for-managed-code-defect"></a>Para crear un elemento de trabajo para defectos de código administrado

1. En el **análisis de código** ventana, seleccione la advertencia.

2. Elija **acciones**, a continuación, elija **crear elemento de trabajo** y elija el tipo de elemento de trabajo para crear.

     Se crea un nuevo elemento de trabajo para que especificar la información de defecto.

## <a name="to-create-a-work-item-for-multiple-managed-code-defects"></a>Para crear un elemento de trabajo para varios defectos de código administrado

1. En el **lista de errores**, seleccione varias advertencias y, a continuación, haga clic en las advertencias.

2. Seleccione **crear elemento de trabajo** y haga clic en el tipo de elemento de trabajo para crear.

     Se crea un elemento de trabajo único para todas las advertencias seleccionadas para especificar la información de error.