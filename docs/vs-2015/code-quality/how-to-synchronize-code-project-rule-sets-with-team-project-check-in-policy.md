---
title: 'Cómo: sincronizar conjuntos de reglas del proyecto de código con la Directiva de protección del proyecto de equipo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.selecttfsruleset
ms.assetid: 9b02f934-2db6-41ec-aaff-9c31ceec2f04
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 3c6e7550940f9d2efa5ca228123310f1b861ee76
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651599"
---
# <a name="how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy"></a>Cómo: Sincronizar conjuntos de reglas del proyecto de código con la directiva de protección del proyecto de equipo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La configuración de análisis de código para los proyectos de código se sincroniza con la Directiva de protección del proyecto de equipo mediante la especificación de un conjunto de reglas que contiene al menos las reglas que se especifican en el conjunto de reglas para la Directiva de inserción en el repositorio. El responsable de desarrollo puede informarle del nombre y la ubicación del conjunto de reglas de la Directiva de inserción en el repositorio. Puede usar una de las siguientes opciones para asegurarse de que el análisis de código para el proyecto utiliza el conjunto de reglas correcto:

- Si la Directiva de inserción en el repositorio usa uno de los conjuntos de reglas integrados de Microsoft, abra el cuadro de diálogo Propiedades del proyecto de código, muestre la página Análisis de código y seleccione el conjunto de reglas en la página Análisis de código de la configuración del proyecto de código. Los conjuntos de reglas estándar de Microsoft se instalan automáticamente con Visual Studio están configurados como de solo lectura y no se deben modificar. Si no se editan los conjuntos de reglas, se garantiza que las reglas de los conjuntos de reglas locales y de directiva coinciden.

- Si la Directiva de protección utiliza un conjunto de reglas personalizado, realice una operación get en el archivo de conjunto de reglas en el control de versiones para crear una copia local. Después, especifique la ubicación local en la configuración de análisis de código para el proyecto de código. Se garantiza que las reglas coinciden si el conjunto de reglas de la Directiva de inserción en el repositorio está actualizado.

     Si asigna la ubicación del control de versiones a una carpeta local que está en la misma relación con la raíz del proyecto de equipo que el proyecto de código, la ubicación de la regla se establece mediante una ruta de acceso relativa. La ruta de acceso relativa garantiza que la configuración del proyecto de código para el análisis de código se puede pasar a otros equipos.

- Personalizar una copia del conjunto de reglas para la Directiva de protección de un proyecto de código. Asegúrese de que el nuevo conjunto de reglas contiene todas las reglas de la Directiva de inserción en el repositorio y cualquier otra regla que desee incluir. Debe asegurarse de que el conjunto de reglas incluye todas las reglas del conjunto de reglas para la Directiva de inserción en el repositorio.

### <a name="to-specify-a-microsoft-standard-rule-set"></a>Para especificar un conjunto de reglas estándar de Microsoft

1. En **Explorador de soluciones**, haga clic con el botón secundario en el proyecto de código y, a continuación, haga clic en **propiedades**.

2. Haga clic en **Análisis de código**.

3. En la lista **ejecutar este conjunto de reglas** , haga clic en el conjunto de reglas de la Directiva de inserción en el repositorio.

### <a name="to-specify-a-custom-check-in-policy-rule-set"></a>Para especificar un conjunto de reglas de directiva de protección personalizada

1. Si es necesario, realice una operación get en el archivo de conjunto de reglas que especifica la Directiva de inserción en el repositorio.

2. En **Explorador de soluciones**, haga clic con el botón secundario en el proyecto de código y, a continuación, haga clic en **propiedades**.

3. Haga clic en **Análisis de código**.

4. En la lista **ejecutar este conjunto de reglas** , haga clic en **\<Browse...>** .

5. En el cuadro de diálogo **abrir** , especifique el archivo de conjunto de reglas de la Directiva de protección.

### <a name="to-create-a-custom-rule-set-for-a-code-project"></a>Para crear un conjunto de reglas personalizado para un proyecto de código

1. Siga uno de los procedimientos descritos anteriormente en este tema para seleccionar la Directiva de protección del proyecto de equipo en la página Análisis de código del cuadro de diálogo Configuración del proyecto.

2. Haga clic en **Abrir**.

3. Agregue o quite reglas mediante el editor de conjuntos de reglas.

     Para obtener más información, consulte [crear conjuntos de reglas personalizadas](../code-quality/creating-custom-code-analysis-rule-sets.md).

4. Guarde el conjunto de reglas modificadas en un archivo. ruleset en el equipo local o en una ruta de acceso UNC.

5. Abra el cuadro de diálogo Propiedades del proyecto de código y muestre la página **análisis de código** .

6. En la lista **ejecutar este conjunto de reglas** , haga clic en **\<Browse...>** .

7. En el cuadro de diálogo **abrir** , especifique el archivo de conjunto de reglas.
