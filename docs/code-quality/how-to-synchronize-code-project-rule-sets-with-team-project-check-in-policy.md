---
title: Sincronizar conjuntos de reglas del proyecto con la Directiva de inserción en el repositorio
ms.date: 11/04/2016
description: Obtenga información sobre cómo sincronizar un conjunto de reglas de proyecto de Visual Studio Code con una directiva de protección del proyecto de Azure DevOps.
ms.custom: SEO-VS-2020
ms.topic: how-to
f1_keywords:
- vs.codeanalysis.selecttfsruleset
ms.assetid: 9b02f934-2db6-41ec-aaff-9c31ceec2f04
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 913860538fe7f9da1514d0e51d23bb3ea48c3b66
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2020
ms.locfileid: "94434693"
---
# <a name="how-to-synchronize-code-project-rule-sets-with-an-azure-devops-project-check-in-policy"></a>Cómo: sincronizar conjuntos de reglas del proyecto de código con una directiva de inserción en el repositorio del proyecto DevOps de Azure

Puede sincronizar la configuración de análisis de código para los proyectos de código con la Directiva de protección del proyecto DevOps de Azure especificando un conjunto de reglas que contenga al menos las reglas que se especifican en el conjunto de reglas para la Directiva de protección. El responsable de desarrollo puede informarle del nombre y la ubicación del conjunto de reglas de la Directiva de inserción en el repositorio. Puede usar una de las siguientes opciones para asegurarse de que el análisis de código para el proyecto utiliza el conjunto de reglas correcto:

- Si la Directiva de inserción en el repositorio usa uno de los conjuntos de reglas integrados de Microsoft, abra el cuadro de diálogo Propiedades del proyecto de código, muestre la página Análisis de código y seleccione el conjunto de reglas. Los conjuntos de reglas estándar de Microsoft se instalan automáticamente con Visual Studio están configurados como de solo lectura y no se deben modificar. Si no se editan los conjuntos de reglas, se garantiza que las reglas de los conjuntos de reglas locales y de directiva coinciden.

- Si la Directiva de protección utiliza un conjunto de reglas personalizado, realice una operación get en el archivo de conjunto de reglas en el control de versiones para crear una copia local. Después, especifique la ubicación local en la configuración de análisis de código para el proyecto de código. Se garantiza que las reglas coinciden si el conjunto de reglas de la Directiva de inserción en el repositorio está actualizado.

     Si asigna la ubicación del control de versiones a una carpeta local que está en la misma relación con la raíz del proyecto DevOps de Azure como proyecto de código, la ubicación de la regla se establece mediante una ruta de acceso relativa. La ruta de acceso relativa garantiza que la configuración del proyecto de código para el análisis de código se puede pasar a otros equipos.

- Personalizar una copia del conjunto de reglas para la Directiva de protección de un proyecto de código. Asegúrese de que el nuevo conjunto de reglas contiene todas las reglas de la Directiva de inserción en el repositorio y cualquier otra regla que desee incluir. Debe asegurarse de que el conjunto de reglas incluye todas las reglas del conjunto de reglas para la Directiva de inserción en el repositorio.

## <a name="to-specify-a-microsoft-standard-rule-set"></a>Para especificar un conjunto de reglas estándar de Microsoft

1. En **Explorador de soluciones** , haga clic con el botón secundario en el proyecto de código y, a continuación, haga clic en **propiedades**.

2. Haga clic en **Análisis de código**.

::: moniker range="vs-2017"

3. En la lista **ejecutar este conjunto de reglas** , seleccione el conjunto de reglas de la Directiva de inserción en el repositorio.

::: moniker-end

::: moniker range=">=vs-2019"

3. En la lista **reglas activas** , seleccione el conjunto de reglas de la Directiva de inserción en el repositorio.

::: moniker-end

## <a name="to-specify-a-custom-check-in-policy-rule-set"></a>Para especificar un conjunto de reglas de directiva de protección personalizada

1. Si es necesario, realice una operación get en el archivo de conjunto de reglas que especifica la Directiva de inserción en el repositorio.

2. En **Explorador de soluciones** , haga clic con el botón secundario en el proyecto de código y, a continuación, haga clic en **propiedades**.

3. Haga clic en **Análisis de código**.

::: moniker range="vs-2017"

4. En la lista **ejecutar este conjunto de reglas** , haga clic en **\<Browse>** .

::: moniker-end

::: moniker range=">=vs-2019"

4. En la lista **reglas activas** , haga clic en **\<Browse>** .

::: moniker-end

5. En el cuadro de diálogo **abrir** , especifique el archivo de conjunto de reglas de la Directiva de protección.

## <a name="to-create-a-custom-rule-set-for-a-code-project"></a>Para crear un conjunto de reglas personalizado para un proyecto de código

Para obtener información sobre cómo crear un conjunto de reglas personalizado, vea [personalizar un conjunto de reglas](how-to-create-a-custom-rule-set.md).
