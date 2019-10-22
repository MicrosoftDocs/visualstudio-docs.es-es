---
title: 'Cómo: crear o actualizar directivas de protección de análisis de código estándar | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.policyeditor
helpviewer_keywords:
- code analysis, migrating check-in policy
ms.assetid: 458eb3b8-bb5e-4056-82b7-7079ce9c4089
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5e8016032a0ea8d1b8c62b2dfc2bbdf72251590c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661779"
---
# <a name="how-to-create-or-update-standard-code-analysis-check-in-policies"></a>Cómo: Crear o actualizar directivas de inserción en el repositorio de análisis de código estándar
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede requerir que el análisis de código se ejecute en todos los proyectos de código de un proyecto de equipo mediante la Directiva de protección de análisis de código. Requerir el análisis de código puede mejorar la calidad del código que se protege en la base de código.

> [!NOTE]
> Esta característica solo está disponible si usa Team Foundation Server.

 Las directivas de protección de análisis de código se establecen en la configuración del proyecto de equipo y se aplican a cada proyecto de código en el proyecto de equipo. Las ejecuciones de análisis de código se configuran para los proyectos de código en el archivo de proyecto (. xxproj) para el proyecto de código. Las ejecuciones de análisis de código se realizan en el equipo local. Cuando se habilita una directiva de protección de análisis de código, los archivos de un proyecto de código que se van a proteger se deben compilar después de la última modificación y una ejecución de análisis de código que contiene, como mínimo, las reglas de la configuración del proyecto de equipo que se deben realizar en el equipo donde se encuentra el se han realizado bloqueos.

- En el caso de código administrado, establezca la Directiva de inserción en el repositorio especificando un *conjunto de reglas* que contenga un subconjunto de las reglas de análisis de código.

- Para C/C++ Code, la Directiva de protección requiere que se ejecuten todas las reglas de análisis de código. Puede Agregar directivas de preprocesador para deshabilitar las reglas específicas para los proyectos de código individuales del proyecto de equipo.

  Después de especificar una directiva de protección para el código administrado, los miembros del equipo pueden sincronizar la configuración de análisis de código de los proyectos de código con la configuración de la Directiva del proyecto de equipo.

### <a name="to-open-the-check-in-policy-editor"></a>Para abrir el editor de directivas de inserción en el repositorio

1. En Team Explorer, haga clic con el botón secundario en el nombre del proyecto de equipo, seleccione **configuración del proyecto de equipo**y, a continuación, haga clic en control de **código fuente**.

2. En el cuadro de diálogo **control de código fuente** , seleccione la pestaña **Directiva de inserción en el repositorio** .

3. Realice una de las siguientes acciones:

    - Haga clic en **Agregar** para crear una nueva Directiva de inserción en el repositorio.

    - Haga doble clic en el elemento de **análisis de código** existente en la lista **tipo de directiva** para cambiar la Directiva.

### <a name="to-set-policy-options"></a>Para establecer las opciones de Directiva

- Active o desactive las siguientes opciones:

    |Opción|Descripción|
    |------------|-----------------|
    |**Forzar la inserción en el repositorio solo contiene archivos que forman parte de la solución actual.**|El análisis de código solo se puede ejecutar en los archivos especificados en los archivos de configuración de la solución y del proyecto. Esta Directiva garantiza que se analice todo el código que forma parte de una solución.|
    |**Exigir análisisC++ de código C/(/Analyze)**|Requiere que todos los proyectos C++ de C o se compilen con la opción del compilador/Analyze para ejecutar el análisis de código antes de que se puedan proteger.|
    |**Aplicar el análisis de código para código administrado**|Requiere que todos los proyectos administrados ejecuten el análisis de código y compilar antes de que se puedan proteger.|

-

### <a name="to-specify-a-managed-rule-set"></a>Para especificar un conjunto de reglas administrado

- En la lista **ejecutar este conjunto de reglas** , use uno de los métodos siguientes:

  - Seleccione un conjunto de reglas estándar de Microsoft.

  - Para seleccionar un conjunto de reglas personalizado, haga clic en **\<Select conjunto de reglas del control de código fuente... >** y, a continuación, escriba la ruta de acceso de control de versiones del conjunto de reglas en el explorador de control de código fuente. La sintaxis de una ruta de acceso de control de versiones es:

  - **$/** `TeamProjectName` **/** `VersionControlPath`

  - Para obtener más información sobre cómo crear e implementar un conjunto de reglas de directivas de protección personalizadas, vea [implementar directivas de protección personalizadas para código administrado](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md).

## <a name="see-also"></a>Vea también
 [Crear y usar directivas de protección del análisis de código](../code-quality/creating-and-using-code-analysis-check-in-policies.md)
