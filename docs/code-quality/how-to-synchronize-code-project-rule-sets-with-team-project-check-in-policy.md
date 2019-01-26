---
title: Procedimiento Sincronizar conjuntos de reglas del proyecto de código con la directiva de protección del proyecto de equipo
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.selecttfsruleset
ms.assetid: 9b02f934-2db6-41ec-aaff-9c31ceec2f04
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 275d4ff2eea093acc226b7e491b5d429a41f7a64
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55036750"
---
# <a name="how-to-synchronize-code-project-rule-sets-with-an-azure-devops-project-check-in-policy"></a>Procedimiento Sincronizar conjuntos de reglas del proyecto de código con una directiva de protección de Azure DevOps Projects

Sincronizar la configuración de análisis de código para proyectos de código a la directiva de protección para el proyecto de DevOps de Azure mediante la especificación de un conjunto de reglas que contenga al menos las reglas que se especifican en el conjunto de reglas para la directiva de protección. El responsable de desarrollo puede informar a los que el nombre y la ubicación de la regla establecida para la directiva de protección. Puede usar una de las opciones siguientes para asegurarse de que el análisis de código para el proyecto usa el conjunto correcto de reglas:

-   Si la directiva de protección usa uno de los conjuntos de reglas integrados de Microsoft, abra el cuadro de diálogo de propiedades para el proyecto de código, mostrar la página de análisis de código y seleccione la regla se establece en la página de análisis de código de la configuración del proyecto de código. Lo conjuntos de reglas estándar se instalan automáticamente con Visual Studio de Microsoft se establecen en solo lectura y no debe editarse. Si no se puede editar los conjuntos de reglas, se garantiza que las reglas de la directiva y los conjuntos de reglas local coinciden.

-   Si la directiva de protección usa un conjunto de reglas personalizado, realizar una operación get en el archivo de conjunto de reglas de control de versiones para crear una copia local. A continuación, especificar esa ubicación local en la configuración de análisis de código para el proyecto de código. Se garantiza que las reglas de coincidencia si el conjunto de reglas para la directiva de protección está actualizada.

     Si asigna la ubicación del control de versiones en una carpeta local que se encuentra en la misma relación con la raíz del proyecto de DevOps de Azure como el proyecto de código, la ubicación de la regla se establece mediante el uso de una ruta de acceso relativa. La ruta de acceso relativa, se garantiza que la configuración del proyecto para el análisis de código se puede mover a otros equipos.

-   Personalizar una copia de la regla establecida para la directiva de protección para un proyecto de código. Asegúrese de que el nuevo conjunto de reglas contiene todas las reglas de la directiva de protección y cualquier otra regla que se va a incluir. Debe asegurarse de que el conjunto de reglas incluye todas las reglas en el conjunto de reglas para la directiva de protección.

## <a name="to-specify-a-microsoft-standard-rule-set"></a>Para especificar una regla estándar de Microsoft del conjunto

1.  En **el Explorador de soluciones**, haga clic en el proyecto de código y, a continuación, haga clic en **propiedades**.

2.  Haga clic en **análisis de código**.

3.  En el **ejecutar este conjunto de reglas** lista, haga clic en el conjunto de reglas de directiva de protección.

## <a name="to-specify-a-custom-check-in-policy-rule-set"></a>Para especificar un conjunto de reglas de directiva de protección personalizada

1.  Si es necesario, realice una operación get en el archivo de conjunto de reglas que especifica la directiva de protección.

2.  En **el Explorador de soluciones**, haga clic en el proyecto de código y, a continuación, haga clic en **propiedades**.

3.  Haga clic en **análisis de código**.

4.  En el **ejecutar este conjunto de reglas** lista, haga clic en  **\<Examinar... >**.

5.  En el **abierto** diálogo cuadro, especifique el archivo de conjunto de la regla de directiva de protección.

## <a name="to-create-a-custom-rule-set-for-a-code-project"></a>Para crear una regla personalizada establecido para un proyecto de código

1.  Siga uno de los procedimientos anteriores de este tema para seleccionar la directiva de protección de Azure DevOps Projects en la página de análisis de código del cuadro de diálogo de configuración de proyecto.

2.  Haga clic en **Abrir**.

3.  Agregar o quitar reglas utilizando el [editor de conjunto de reglas](../code-quality/working-in-the-code-analysis-rule-set-editor.md).

4.  Guardar la regla modificada establecida en un archivo .ruleset en el equipo local o en una ruta de acceso UNC.

5.  Abra el cuadro de diálogo de propiedades para el proyecto de código y mostrar el **análisis de código** página.

6.  En el **ejecutar este conjunto de reglas** lista, haga clic en  **\<Examinar... >**.

7.  En el **abierto** diálogo cuadro, especifique el archivo de conjunto de la regla.