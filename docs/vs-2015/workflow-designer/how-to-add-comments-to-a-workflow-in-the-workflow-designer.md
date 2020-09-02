---
title: 'Cómo: agregar comentarios a un flujo de trabajo en el Diseñador de flujo de trabajo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.Annotations.Annotation.UI
- Annotation
ms.assetid: 9aa0e8d6-8129-4438-8389-d460611581a7
caps.latest.revision: 7
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d775c79cc7abdf6a66b1174ae625ca468f0764fc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663448"
---
# <a name="how-to-add-comments-to-a-workflow-in-the-workflow-designer"></a>Agregar comentarios a un flujo de trabajo en el Diseñador de flujo de trabajo
Para facilitar la creación de flujos de trabajo mayores y más complicados, [!INCLUDE[net_v45](../includes/net-v45-md.md)] permite al desarrollador agregar anotaciones a los siguientes tipos de elemento en el diseñador:

- <xref:System.Activities.Activity>

- <xref:System.Activities.Statements.State>

- <xref:System.Activities.Statements.Transition>

- Clases derivadas de <xref:System.Activities.Statements.FlowNode>.

- <xref:System.Activities.Variable>

- <xref:System.Activities.Argument>

> [!IMPORTANT]
> El contenido de una anotación se guarda como texto sin formato en el archivo XAML asociado al flujo de trabajo y podrían leerlo otras personas. Tenga cuidado al especificar información confidencial en una anotación.

### <a name="adding-an-annotation-to-an-activity-in-the-designer"></a>Agregar una anotación a una actividad en el diseñador

1. En el diseñador de flujo de trabajo, haga clic con el botón derecho en un elemento en el diseñador de flujo de trabajo y seleccione **anotaciones**, **Agregar anotación**.

2. Agregue el texto de la anotación en el espacio proporcionado.

3. El elemento mostrará un icono de anotación. Al mantener el mouse sobre el icono de anotación se mostrará el texto de la anotación.

     ![Actividad Sequence que muestra una anotación](../workflow-designer/media/annotation.png "Anotación")

### <a name="displaying-an-annotation-in-an-activitys-designer"></a>Mostrar una anotación en el diseñador de una actividad

1. Con un diseñador de actividad que tiene una anotación que se muestra fuera de la actividad, haga clic en el icono de **anclaje** en el adorno de anotación.

2. La anotación se mostrará en el diseñador de la actividad. En la captura de pantalla siguiente, la anotación "Iniciando actividad en el flujo de trabajo" se muestra en el diseñador de la actividad.

     ![Anotación que se muestra en el diseñador de actividades](../workflow-designer/media/annotationindesigner.png "AnnotationInDesigner")

3. Para mostrar la anotación fuera del diseñador de la actividad, mantenga el mouse sobre el área de anotación en el diseñador de la actividad y haga clic en el icono **desanclar** .

     ![Anotación que se muestra fuera del diseñador de actividades](../workflow-designer/media/annotationoutsidedesigner.png "AnnotationOutsideDesigner")

### <a name="showing-or-hiding-all-annotations"></a>Mostrar u ocultar todas las anotaciones

1. Haga clic con el botón secundario en una actividad que tiene una anotación. Seleccione **anotaciones**y **muestre todas las anotaciones**.

2. Todas las anotaciones se mostrarán en los diseñadores de la actividad.

3. Para mostrar todas las anotaciones fuera de los diseñadores de la actividad, haga clic con el botón derecho en la actividad y seleccione **anotaciones**, **ocultar todas las anotaciones**.

### <a name="editing-or-deleting-an-annotation-for-an-activity"></a>Editar o eliminar una anotación para una actividad

1. Haga clic con el botón secundario en una actividad que tiene una anotación.

2. Seleccione **anotaciones**, **Editar** anotación o **eliminar anotación**.

3. La anotación se abrirá para editar o eliminar.

4. Para eliminar todas las anotaciones al mismo tiempo, haga clic con el botón secundario en el diseñador de flujo de trabajo y seleccione **anotación**, **eliminar todas las anotaciones**.

### <a name="adding-editing-and-deleting-an-annotation-for-a-variable-or-argument"></a>Agregar, editar y eliminar una anotación para una variable o argumento

1. Haga clic con el botón secundario en una variable o argumento y seleccione Agregar anotación.

2. Escriba el texto de la anotación. La variable o argumento mostrará un icono de anotación.

3. Haga clic con el botón secundario en una variable o argumento que tiene una anotación. Seleccione Editar anotación.

4. La anotación se abrirá para editar.

5. Haga clic con el botón secundario en una variable o argumento que tiene una anotación. Seleccione Eliminar anotación.

6. La anotación se eliminará.