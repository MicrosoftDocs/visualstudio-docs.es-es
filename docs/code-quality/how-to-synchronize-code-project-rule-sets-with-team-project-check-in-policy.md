---
title: 'Cómo: Sincronizar conjuntos de reglas del proyecto de código con la directiva de protección del proyecto de equipo'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.selecttfsruleset
ms.assetid: 9b02f934-2db6-41ec-aaff-9c31ceec2f04
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1bb6f97495eec73e52751f79d92e2f078bd13b24
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy"></a>Cómo: Sincronizar conjuntos de reglas del proyecto de código con la directiva de protección del proyecto de equipo

Sincronizar la configuración de análisis de código para los proyectos de código a la directiva de protección del proyecto de equipo mediante la especificación de un conjunto de reglas que contenga al menos las reglas que se especifican en el conjunto de reglas para la directiva de protección. Su jefa de desarrollador puede informar sobre el nombre y la ubicación de la regla establecida para la directiva de protección. Puede usar una de las opciones siguientes para asegurarse de que el análisis de código para el proyecto utiliza el conjunto correcto de reglas:

-   Si la directiva de protección usa uno de los conjuntos de reglas integradas de Microsoft, abra el cuadro de diálogo de propiedades para el proyecto de código, muestre la página de análisis de código y seleccione el conjunto en la página de análisis de código de la configuración del proyecto de código de reglas. Microsoft conjuntos de reglas estándar se instalan automáticamente con Visual Studio se establece en solo lectura y no debe editarse. Si no se editan los conjuntos de reglas, se garantiza que las reglas de la directiva y los conjuntos de reglas local para que coincida con.

-   Si la directiva de protección usa un conjunto de reglas personalizado, realice una operación get en el archivo de conjunto de reglas de control de versiones para crear una copia local. A continuación, especificar esa ubicación local en la configuración de análisis de código para el proyecto de código. Se garantiza que las reglas de coincidencia si el conjunto de reglas para la directiva de protección están actualizado.

     Si asigna la ubicación del control de versiones en una carpeta local que se encuentra en la misma relación con la raíz del proyecto de equipo como su proyecto de código, la ubicación de la regla se establece mediante una ruta de acceso relativa. La ruta de acceso relativa garantiza que la configuración del proyecto de código para el análisis de código se puede mover a otros equipos.

-   Personalizar una copia de la regla establecida para la directiva de protección para un proyecto de código. Asegúrese de que el nuevo conjunto de reglas contiene todas las reglas de la directiva de protección y cualquier otra regla que se va a incluir. Debe asegurarse de que el conjunto de reglas incluye todas las reglas en el conjunto de reglas para la directiva de protección.

## <a name="to-specify-a-microsoft-standard-rule-set"></a>Para especificar una regla estándar de Microsoft del conjunto

1.  En **el Explorador de soluciones**, haga clic en el proyecto de código y, a continuación, haga clic en **propiedades**.

2.  Haga clic en **de análisis de código**.

3.  En el **ejecutar este conjunto de reglas** lista, haga clic en el conjunto de reglas de directiva de protección.

## <a name="to-specify-a-custom-check-in-policy-rule-set"></a>Para especificar un conjunto de reglas de directiva de protección personalizada

1.  Si es necesario, realizar una operación get en el archivo de conjunto de reglas que especifica la directiva de protección.

2.  En **el Explorador de soluciones**, haga clic en el proyecto de código y, a continuación, haga clic en **propiedades**.

3.  Haga clic en **de análisis de código**.

4.  En el **ejecutar este conjunto de reglas** lista, haga clic en  **\<Examinar... >**.

5.  En el **abiertos** diálogo cuadro, especifica la regla de directiva de protección para el archivo de conjunto.

## <a name="to-create-a-custom-rule-set-for-a-code-project"></a>Para crear una regla personalizada establecido para un proyecto de código

1.  Siga uno de los procedimientos anteriores de este tema para seleccionar la directiva de protección del proyecto de equipo en la página de análisis de código del cuadro de diálogo de configuración de proyecto.

2.  Haga clic en **abiertos**.

3.  Agregar o quitar reglas mediante el uso de la [editor de conjunto de reglas](../code-quality/working-in-the-code-analysis-rule-set-editor.md).

4.  Guardar la regla modificada establecida en un archivo .ruleset en el equipo local o en una ruta de acceso UNC.

5.  Abrir el cuadro de diálogo de propiedades para el proyecto de código y mostrar la **análisis de código** página.

6.  En el **ejecutar este conjunto de reglas** lista, haga clic en  **\<Examinar... >**.

7.  En el **abiertos** diálogo cuadro, especifique el conjunto de reglas archivo.