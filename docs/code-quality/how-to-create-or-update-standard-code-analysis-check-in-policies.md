---
title: Crear o actualizar directivas de protección de análisis de código estándar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.policyeditor
helpviewer_keywords:
- code analysis, migrating check-in policy
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d034d65cd356ff44a42d10840ae064d81713457f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587542"
---
# <a name="how-to-create-or-update-standard-code-analysis-check-in-policies"></a>Cómo: Crear o actualizar directivas de inserción en el repositorio de análisis de código estándar

Puede requerir que el análisis de código se ejecute en todos los proyectos de código en un proyecto de DevOps de Azure mediante la Directiva de protección de análisis de código. Requerir el análisis de código puede mejorar la calidad del código que se protege en la base de código.

> [!NOTE]
> Esta característica solo está disponible si usa Team Foundation Server.

Las directivas de protección de análisis de código se establecen en la configuración del proyecto y se aplican a cada proyecto de código. Las ejecuciones de análisis de código se configuran para los proyectos de código en el archivo de proyecto (. xxproj) para el proyecto de código. Las ejecuciones de análisis de código se realizan en el equipo local. Cuando se habilita una directiva de protección de análisis de código, los archivos de un proyecto de código que se van a proteger se deben compilar después de la última edición y una ejecución de análisis de código que contiene, como mínimo, las reglas de la configuración del proyecto que se deben realizar en el equipo en el que se realizó el cambio se han realizado.

- En el caso de código administrado, establezca la Directiva de inserción en el repositorio especificando un *conjunto de reglas* que contenga un subconjunto de las reglas de análisis de código.

- En el casoC++ de C/Code, en la versión 15,6 y anteriores de Visual Studio 2017, la Directiva de protección requiere que se ejecuten todas las reglas de análisis de código. Puede Agregar directivas de preprocesador para deshabilitar las reglas específicas para los proyectos de código individuales en el proyecto DevOps de Azure. En 15,7 y versiones posteriores, puede usar **/Analyze: ruleset** para especificar las reglas que se van a ejecutar. Para obtener más información, vea [usar conjuntos de reglas para C++ especificar las reglas que se van a ejecutar](using-rule-sets-to-specify-the-cpp-rules-to-run.md).

Después de especificar una directiva de inserción en el repositorio para el código administrado, los miembros del equipo pueden sincronizar la configuración de análisis de código de los proyectos de código con la configuración de la Directiva del proyecto DevOps de Azure.

## <a name="to-open-the-check-in-policy-editor"></a>Para abrir el editor de directivas de inserción en el repositorio

1. En Team Explorer, haga clic con el botón secundario en el nombre del proyecto, seleccione **configuración del proyecto**y, a continuación, haga clic en **control de código fuente**.

1. En el cuadro de diálogo **control de código fuente** , seleccione la pestaña **Directiva de inserción en el repositorio** .

1. Siga uno de los procedimientos que se describen a continuación:

    - Haga clic en **Agregar** para crear una nueva Directiva de inserción en el repositorio.

    - Haga doble clic en el elemento de **análisis de código** existente en la lista **tipo de directiva** para cambiar la Directiva.

## <a name="to-set-policy-options"></a>Para establecer las opciones de Directiva

Active o desactive las siguientes opciones:

|Opción|Descripción|
|------------|-----------------|
|**Forzar la inserción en el repositorio solo contiene archivos que forman parte de la solución actual.**|El análisis de código solo se puede ejecutar en los archivos especificados en los archivos de configuración de la solución y del proyecto. Esta Directiva garantiza que se analice todo el código que forma parte de una solución.|
|**Exigir análisisC++ de código C/(/Analyze)**|Requiere que todos los proyectos C++ de C o se compilen con la opción del compilador/Analyze para ejecutar el análisis de código antes de que se puedan proteger.|
|**Aplicar el análisis de código para código administrado**|Requiere que todos los proyectos administrados ejecuten el análisis de código y compilar antes de que se puedan proteger.|

## <a name="to-specify-a-managed-rule-set"></a>Para especificar un conjunto de reglas administrado

En la lista **ejecutar este conjunto de reglas** , use uno de los métodos siguientes:

- Seleccione un conjunto de reglas estándar de Microsoft.

- Seleccione un conjunto de reglas personalizado haciendo clic en **\<seleccionar conjunto de reglas en el control de código fuente... >** . A continuación, escriba la ruta de acceso de control de versiones del conjunto de reglas en el explorador de control de código fuente. La sintaxis de una ruta de acceso de control de versiones es:

   **$/** `TeamProjectName` **/** `VersionControlPath`

Para obtener más información sobre cómo crear e implementar un conjunto de reglas de directivas de protección personalizadas, vea [implementar directivas de protección personalizadas para código administrado](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md).

## <a name="see-also"></a>Vea también

- [Implementar directivas de protección de análisis de código personalizadas para el código administrado](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md)
