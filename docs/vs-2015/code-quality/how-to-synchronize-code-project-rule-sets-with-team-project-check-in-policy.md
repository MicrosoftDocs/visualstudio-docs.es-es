---
title: Filtrar Sincronizar conjuntos de reglas del proyecto de código con la directiva de comprobación del proyecto de equipo | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.selecttfsruleset
ms.assetid: 9b02f934-2db6-41ec-aaff-9c31ceec2f04
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2f79b8baf3740fdbd57828552a192746e839578c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58995140"
---
# <a name="how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy"></a>Filtrar Sincronizar conjuntos de reglas del proyecto de código con la directiva de protección del proyecto de equipo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sincronizar la configuración de análisis de código para proyectos de código a la directiva de protección del proyecto de equipo mediante la especificación de un conjunto de reglas que contenga al menos las reglas que se especifican en el conjunto de reglas para la directiva de protección. El responsable de desarrollo puede informar a los que el nombre y la ubicación de la regla establecida para la directiva de protección. Puede usar una de las opciones siguientes para asegurarse de que el análisis de código para el proyecto usa el conjunto correcto de reglas:  
  
-   Si la directiva de protección usa uno de los conjuntos de reglas integrados de Microsoft, abra el cuadro de diálogo de propiedades para el proyecto de código, mostrar la página de análisis de código y seleccione la regla se establece en la página de análisis de código de la configuración del proyecto de código. Lo conjuntos de reglas estándar se instalan automáticamente con Visual Studio de Microsoft se establecen en solo lectura y no debe editarse. Si no se puede editar los conjuntos de reglas, se garantiza que las reglas de la directiva y los conjuntos de reglas local coinciden.  
  
-   Si la directiva de protección usa un conjunto de reglas personalizado, realizar una operación get en el archivo de conjunto de reglas de control de versiones para crear una copia local. A continuación, especificar esa ubicación local en la configuración de análisis de código para el proyecto de código. Se garantiza que las reglas de coincidencia si el conjunto de reglas para la directiva de protección está actualizada.  
  
     Si asigna la ubicación del control de versiones en una carpeta local que se encuentra en la misma relación a la raíz del proyecto de equipo que el proyecto de código, la ubicación de la regla se establece mediante el uso de una ruta de acceso relativa. La ruta de acceso relativa, se garantiza que la configuración del proyecto para el análisis de código se puede mover a otros equipos.  
  
-   Personalizar una copia de la regla establecida para la directiva de protección para un proyecto de código. Asegúrese de que el nuevo conjunto de reglas contiene todas las reglas de la directiva de protección y cualquier otra regla que se va a incluir. Debe asegurarse de que el conjunto de reglas incluye todas las reglas en el conjunto de reglas para la directiva de protección.  
  
### <a name="to-specify-a-microsoft-standard-rule-set"></a>Para especificar una regla estándar de Microsoft del conjunto  
  
1.  En **el Explorador de soluciones**, haga clic en el proyecto de código y, a continuación, haga clic en **propiedades**.  
  
2.  Haga clic en **análisis de código**.  
  
3.  En el **ejecutar este conjunto de reglas** lista, haga clic en el conjunto de reglas de directiva de protección.  
  
### <a name="to-specify-a-custom-check-in-policy-rule-set"></a>Para especificar un conjunto de reglas de directiva de protección personalizada  
  
1.  Si es necesario, realice una operación get en el archivo de conjunto de reglas que especifica la directiva de protección.  
  
2.  En **el Explorador de soluciones**, haga clic en el proyecto de código y, a continuación, haga clic en **propiedades**.  
  
3.  Haga clic en **análisis de código**.  
  
4.  En el **ejecutar este conjunto de reglas** lista, haga clic en  **\<Examinar... >**.  
  
5.  En el **abierto** diálogo cuadro, especifique el archivo de conjunto de la regla de directiva de protección.  
  
### <a name="to-create-a-custom-rule-set-for-a-code-project"></a>Para crear una regla personalizada establecido para un proyecto de código  
  
1.  Siga uno de los procedimientos anteriores de este tema para seleccionar la directiva de protección del proyecto de equipo en la página de análisis de código del cuadro de diálogo de configuración de proyecto.  
  
2.  Haga clic en **Abrir**.  
  
3.  Agregar o quitar reglas mediante el editor de conjunto de reglas.  
  
     Para obtener más información, consulte [crear conjuntos de reglas personalizadas](../code-quality/creating-custom-code-analysis-rule-sets.md).  
  
4.  Guardar la regla modificada establecida en un archivo .ruleset en el equipo local o en una ruta de acceso UNC.  
  
5.  Abra el cuadro de diálogo de propiedades para el proyecto de código y mostrar el **análisis de código** página.  
  
6.  En el **ejecutar este conjunto de reglas** lista, haga clic en  **\<Examinar... >**.  
  
7.  En el **abierto** diálogo cuadro, especifique el archivo de conjunto de la regla.
