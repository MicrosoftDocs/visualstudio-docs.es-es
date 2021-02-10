---
title: 'Diseñador de flujo de trabajo: Cómo agregar comentarios a un flujo de trabajo'
description: Obtenga información sobre cómo .NET Framework 4,5 permite al desarrollador agregar anotaciones a determinados tipos de elementos del diseñador, por ejemplo, elementos de actividad, estado y transición.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- System.Activities.Presentation.Annotations.Annotation.UI
- Annotation
ms.assetid: 9aa0e8d6-8129-4438-8389-d460611581a7
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: 9417dd0084b381d8fc997a90b4690c49191f4785
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971705"
---
# <a name="how-to-add-comments-to-a-workflow-in-the-workflow-designer"></a>Agregar comentarios a un flujo de trabajo en el Diseñador de flujo de trabajo

Para facilitar la creación de flujos de trabajo más grandes y complejos, .NET Framework 4,5 permite al desarrollador agregar anotaciones a los siguientes tipos de elemento en el diseñador:

- <xref:System.Activities.Activity>

- <xref:System.Activities.Statements.State>

- <xref:System.Activities.Statements.Transition>

- Clases derivadas de <xref:System.Activities.Statements.FlowNode>.

- <xref:System.Activities.Variable>

- <xref:System.Activities.Argument>

> [!IMPORTANT]
> El contenido de una anotación se guarda como texto sin formato en el archivo XAML asociado al flujo de trabajo y podrían leerlo otras personas. Tenga cuidado al especificar información confidencial en una anotación.

## <a name="adding-an-annotation-to-an-activity-in-the-designer"></a>Agregar una anotación a una actividad en el diseñador

1. En el diseñador de flujo de trabajo, haga clic con el botón derecho en un elemento en el diseñador de flujo de trabajo y seleccione **anotaciones**, **Agregar anotación**.

1. Agregue el texto de la anotación en el espacio proporcionado.

   El elemento muestra un icono de anotación. Al mantener el puntero sobre el icono de anotación se muestra el texto de la anotación.

## <a name="displaying-an-annotation-in-an-activitys-designer"></a>Mostrar una anotación en el diseñador de una actividad

1. Con un diseñador de actividad que tiene una anotación que se muestra fuera de la actividad, haga clic en el icono de **anclaje** en el adorno de anotación.

   La anotación se muestra en el diseñador de la actividad. En la captura de pantalla siguiente, la anotación "Iniciando actividad en el flujo de trabajo" se muestra en el diseñador de la actividad.

   ![Anotación que se muestra en el diseñador de actividades](../workflow-designer/media/annotationindesigner.png)

2. Para mostrar la anotación fuera del diseñador de la actividad, mantenga el mouse sobre el área de anotación en el diseñador de la actividad y haga clic en el icono **desanclar** .

   ![Anotación mostrada fuera del diseñador de una actividad](../workflow-designer/media/annotationoutsidedesigner.png)

## <a name="showing-or-hiding-all-annotations"></a>Mostrar u ocultar todas las anotaciones

1. Haga clic con el botón secundario en una actividad que tiene una anotación. Seleccione **anotaciones** y **muestre todas las anotaciones**.

   Todas las anotaciones se muestran en los diseñadores de la actividad.

1. Para mostrar todas las anotaciones fuera de los diseñadores de la actividad, haga clic con el botón derecho en la actividad y seleccione **anotaciones**, **ocultar todas las anotaciones**.

## <a name="editing-or-deleting-an-annotation-for-an-activity"></a>Editar o eliminar una anotación para una actividad

1. Haga clic con el botón secundario en una actividad que tiene una anotación.

1. Seleccione **anotaciones**, **Editar** anotación o **eliminar anotación**.

   La anotación se abre para su edición o eliminación.

1. Para eliminar todas las anotaciones al mismo tiempo, haga clic con el botón secundario en el diseñador de flujo de trabajo y seleccione **anotación**, **eliminar todas las anotaciones**.

## <a name="adding-editing-and-deleting-an-annotation-for-a-variable-or-argument"></a>Agregar, editar y eliminar una anotación para una variable o argumento

1. Haga clic con el botón secundario en una variable o argumento y seleccione Agregar anotación.

1. Escriba el texto de la anotación. La variable o argumento muestra un icono de anotación.

1. Haga clic con el botón secundario en una variable o argumento que tiene una anotación. Seleccione Editar anotación.

   La anotación se abre para su edición.

1. Haga clic con el botón secundario en una variable o argumento que tiene una anotación. Seleccione Eliminar anotación.

   Se elimina la anotación.
