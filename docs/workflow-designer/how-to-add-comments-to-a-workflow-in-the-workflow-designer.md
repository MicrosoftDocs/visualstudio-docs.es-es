---
title: 'Diseñador de flujo de trabajo - Cómo: agregar comentarios a un flujo de trabajo'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Presentation.Annotations.Annotation.UI
- Annotation
ms.assetid: 9aa0e8d6-8129-4438-8389-d460611581a7
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 43b17390f077238a6874784f186eb8add3819f6d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49883311"
---
# <a name="how-to-add-comments-to-a-workflow-in-the-workflow-designer"></a>Agregar comentarios a un flujo de trabajo en el Diseñador de flujo de trabajo

Para facilitar la creación de flujos de trabajo mayores y más complicados, .NET Framework 4.5 permite al desarrollador agregar anotaciones a los siguientes tipos de elemento en el diseñador:

-   <xref:System.Activities.Activity>

-   <xref:System.Activities.Statements.State>

-   <xref:System.Activities.Statements.Transition>

-   Clases derivadas de <xref:System.Activities.Statements.FlowNode>.

-   <xref:System.Activities.Variable>

-   <xref:System.Activities.Argument>

> [!IMPORTANT]
> El contenido de una anotación se guarda como texto sin formato en el archivo XAML asociado al flujo de trabajo y podrían leerlo otras personas. Tenga cuidado al especificar información confidencial en una anotación.

## <a name="adding-an-annotation-to-an-activity-in-the-designer"></a>Agregar una anotación a una actividad en el diseñador

1. En el Diseñador de flujo de trabajo, haga doble clic en un elemento en el flujo de trabajo de diseñador y seleccione **anotaciones**, **Agregar anotación**.

1. Agregue el texto de la anotación en el espacio proporcionado.

   El elemento muestra un icono de anotación. Al mantener el mouse sobre el icono de anotación muestra el texto de la anotación.

## <a name="displaying-an-annotation-in-an-activitys-designer"></a>Mostrar una anotación en el diseñador de una actividad

1. Con un diseñador de actividad que tiene una anotación que se muestre fuera de la actividad, haga clic en el **Pin** icono en el adorno de la anotación.

   La anotación se muestra en el Diseñador de actividad. En la captura de pantalla siguiente, la anotación "Iniciando actividad en el flujo de trabajo" se muestra en el diseñador de la actividad.

   ![Anotación que se muestra en el diseñador de actividades](../workflow-designer/media/annotationindesigner.png)

2. Para mostrar la anotación fuera del Diseñador de actividad, mantenga el mouse sobre el área de anotación en el Diseñador de actividad y haga clic en el **Desanclar** icono

   ![Anotación que se muestra fuera del Diseñador de actividad](../workflow-designer/media/annotationoutsidedesigner.png)

## <a name="showing-or-hiding-all-annotations"></a>Mostrar u ocultar todas las anotaciones

1. Haga clic con el botón secundario en una actividad que tiene una anotación. Seleccione **anotaciones**, **mostrar todas las anotaciones**.

   Todas las anotaciones se muestran en los diseñadores de actividades.

1. Para mostrar todas las anotaciones fuera de los diseñadores de actividades, haga doble clic en la actividad y seleccione **anotaciones**, **ocultar todas las anotaciones**.

## <a name="editing-or-deleting-an-annotation-for-an-activity"></a>Editar o eliminar una anotación para una actividad

1. Haga clic con el botón secundario en una actividad que tiene una anotación.

1. Seleccione **anotaciones**, **Editar anotación** o **Eliminar anotación**.

   Se abre para su edición o se elimina la anotación.

1. Para eliminar todas las anotaciones a la vez, haga clic en el flujo de trabajo de diseñador y seleccione **anotación**, **eliminar todas las anotaciones**.

## <a name="adding-editing-and-deleting-an-annotation-for-a-variable-or-argument"></a>Agregar, editar y eliminar una anotación para una variable o argumento

1. Haga clic con el botón secundario en una variable o argumento y seleccione Agregar anotación.

1. Escriba el texto de la anotación. La variable o argumento muestra un icono de anotación.

1. Haga clic con el botón secundario en una variable o argumento que tiene una anotación. Seleccione Editar anotación.

   La anotación se abre para su edición.

1. Haga clic con el botón secundario en una variable o argumento que tiene una anotación. Seleccione Eliminar anotación.

   Se elimina la anotación.