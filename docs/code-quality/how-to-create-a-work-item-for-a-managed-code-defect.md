---
title: 'Cómo: crear un elemento de trabajo para defectos de código administrado | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- managed code, creating work items for code defects
- code analysis, creating work items
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: a1af08ea7f76f275e17c6f99305b1189fe639291
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
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