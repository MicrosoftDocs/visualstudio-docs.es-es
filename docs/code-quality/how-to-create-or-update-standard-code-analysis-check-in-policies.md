---
title: Crear o actualizar directivas de protección de análisis de código estándar
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.policyeditor
helpviewer_keywords:
- code analysis, migrating check-in policy
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9c4a7405dd94837d5e373470cd9181c18d913191
ms.sourcegitcommit: 159ed9d4f56cdc1dff2fd19d9dffafe77e46cd4e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2018
ms.locfileid: "53740080"
---
# <a name="how-to-create-or-update-standard-code-analysis-check-in-policies"></a>Procedimiento Crear o actualizar directivas de protección de análisis de código estándar

Puede requerir que el análisis de código se ejecute en todos los proyectos de código en un proyecto de DevOps de Azure mediante el uso de la directiva de protección de análisis de código. Necesidad de análisis de código puede mejorar la calidad del código que está protegido en la base de código.

> [!NOTE]
> Esta característica está disponible solo si usa Team Foundation Server.

Directivas de protección de análisis de código se establecen en la configuración del proyecto y se aplican a cada proyecto de código. Ejecuciones de análisis de código se configuran para los proyectos de código en el archivo de proyecto (xxproj) para el proyecto de código. Ejecuciones de análisis de código se realizan en el equipo local. Cuando se habilita una directiva de protección de análisis de código, se deben compilar los archivos en un proyecto de código que se comprueben después de su última modificación y que ejecute un análisis de código contiene, como mínimo, las reglas de la configuración del proyecto deben realizarse en el equipo donde el cambio se han realizado s.

- Para código administrado, establezca la directiva de protección especificando un *conjunto de reglas* que contiene un subconjunto de las reglas de análisis de código.

- Para el código de C o C++, en Visual Studio 2017 versión 15.6 y versiones anterior, la directiva de protección requiere que se ejecuten todas las reglas de análisis de código. Puede agregar directivas de preprocesador para deshabilitar reglas específicas para los proyectos de código individuales en un proyecto de DevOps de Azure. En la versión 15.7 y versiones posteriores, puede usar **/ analyze: ruleset** para especificar qué reglas se deben ejecutar. Para obtener más información, consulte [utilizando conjuntos de reglas para especificar las reglas de C++ para ejecutar](using-rule-sets-to-specify-the-cpp-rules-to-run.md).

Después de especificar una directiva de protección para el código administrado, los miembros del equipo pueden sincronizar su configuración de análisis de código para proyectos de código para la configuración de directiva de Azure DevOps project.

## <a name="to-open-the-check-in-policy-editor"></a>Para abrir el editor de directivas de protección

1. En Team Explorer, haga clic en el nombre del proyecto, apunte a **configuración del proyecto**y, a continuación, haga clic en **Control de código fuente**.

1. En el **Control de código fuente** cuadro de diálogo, seleccione el **directiva de protección** ficha.

1. Realice una de las siguientes acciones:

    - Haga clic en **agregar** para crear una nueva directiva de protección.

    - Haga doble clic en las existentes **análisis de código** de elemento en el **tipo de directiva** lista para cambiar la directiva.

## <a name="to-set-policy-options"></a>Para establecer las opciones de directiva

Active o desactive las siguientes opciones:

|Opción|Descripción|
|------------|-----------------|
|**Exigir la protección para que solo contenga los archivos que forman parte de la solución actual.**|Puede ejecutar análisis de código solo en los archivos especificados en los archivos de configuración de solución y proyecto. Esta directiva garantiza que se analiza todo el código que forma parte de una solución.|
|**Aplicar análisis de código de C/C ++ (/analyze)**|Requiere que todos los proyectos de C o C++ se compilan con la / analyze para ejecutar el análisis de código antes de que se pueden comprobar la opción del compilador.|
|**Aplicar análisis de código para código administrado**|Requiere que todos los proyectos administrados, ejecutan análisis de código y compilación antes de que puedan protegerse.|

## <a name="to-specify-a-managed-rule-set"></a>Para especificar un conjunto de reglas administrado

Desde el **ejecutar este conjunto de reglas** enumerar, use uno de los métodos siguientes:

- Seleccione un conjunto de reglas estándar de Microsoft.

- Seleccione una regla personalizada si hace clic en  **\<Seleccionar conjunto de reglas de Control de código fuente... >**. A continuación, escriba la ruta de acceso de control de versiones de la regla especificada en el Explorador de control de código fuente. La sintaxis de una ruta de acceso de control de versiones es:

   **$/** `TeamProjectName` **/** `VersionControlPath`

Para obtener más información sobre cómo crear e implementar una regla de directiva de protección personalizadas conjunto, consulte [personalizado para implementar directivas de protección para código administrado](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md).

## <a name="see-also"></a>Vea también

- [Crear y usar directivas de protección de análisis de código](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)