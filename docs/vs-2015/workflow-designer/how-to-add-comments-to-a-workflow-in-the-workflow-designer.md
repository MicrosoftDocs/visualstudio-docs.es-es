---
title: 'Cómo: agregar comentarios a un flujo de trabajo en el Diseñador de flujo de trabajo | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.Annotations.Annotation.UI
- Annotation
ms.assetid: 9aa0e8d6-8129-4438-8389-d460611581a7
caps.latest.revision: 7
author: steved0x
ms.author: gewarren
manager: erikre
ms.openlocfilehash: f70f8ba1a30d5adcaffe7e693fcc711d08a28baf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47575177"
---
# <a name="how-to-add-comments-to-a-workflow-in-the-workflow-designer"></a>Agregar comentarios a un flujo de trabajo en el Diseñador de flujo de trabajo
Para facilitar la creación de flujos de trabajo mayores y más complicados, [!INCLUDE[net_v45](../includes/net-v45-md.md)] permite al desarrollador agregar anotaciones a los siguientes tipos de elemento en el diseñador:  
  
-   <xref:System.Activities.Activity>  
  
-   <xref:System.Activities.Statements.State>  
  
-   <xref:System.Activities.Statements.Transition>  
  
-   Clases derivadas de <xref:System.Activities.Statements.FlowNode>.  
  
-   <xref:System.Activities.Variable>  
  
-   <xref:System.Activities.Argument>  
  
> [!IMPORTANT]
>  El contenido de una anotación se guarda como texto sin formato en el archivo XAML asociado al flujo de trabajo y podrían leerlo otras personas. Tenga cuidado al especificar información confidencial en una anotación.  
  
### <a name="adding-an-annotation-to-an-activity-in-the-designer"></a>Agregar una anotación a una actividad en el diseñador  
  
1.  En el Diseñador de flujo de trabajo, haga doble clic en un elemento en el flujo de trabajo de diseñador y seleccione **anotaciones**, **Agregar anotación**.  
  
2.  Agregue el texto de la anotación en el espacio proporcionado.  
  
3.  El elemento mostrará un icono de anotación. Al mantener el mouse sobre el icono de anotación se mostrará el texto de la anotación.  
  
     ![Secuencia de actividad mostrando anotación](../workflow-designer/media/annotation.png "anotación")  
  
### <a name="displaying-an-annotation-in-an-activitys-designer"></a>Mostrar una anotación en el diseñador de una actividad  
  
1.  Con un diseñador de actividad que tiene una anotación que se muestre fuera de la actividad, haga clic en el **Pin** icono en el adorno de la anotación.  
  
2.  La anotación se mostrará en el diseñador de la actividad. En la captura de pantalla siguiente, la anotación "Iniciando actividad en el flujo de trabajo" se muestra en el diseñador de la actividad.  
  
     ![Anotación que se muestra en el Diseñador de actividad](../workflow-designer/media/annotationindesigner.png "AnnotationInDesigner")  
  
3.  Para mostrar la anotación fuera del Diseñador de actividad, mantenga el mouse sobre el área de anotación en el Diseñador de actividad y haga clic en el **Desanclar** icono  
  
     ![Anotación que se muestra fuera del Diseñador de actividades](../workflow-designer/media/annotationoutsidedesigner.png "AnnotationOutsideDesigner")  
  
### <a name="showing-or-hiding-all-annotations"></a>Mostrar u ocultar todas las anotaciones  
  
1.  Haga clic con el botón secundario en una actividad que tiene una anotación. Seleccione **anotaciones**, **mostrar todas las anotaciones**.  
  
2.  Todas las anotaciones se mostrarán en los diseñadores de la actividad.  
  
3.  Para mostrar todas las anotaciones fuera de los diseñadores de actividades, haga doble clic en la actividad y seleccione **anotaciones**, **ocultar todas las anotaciones**.  
  
### <a name="editing-or-deleting-an-annotation-for-an-activity"></a>Editar o eliminar una anotación para una actividad  
  
1.  Haga clic con el botón secundario en una actividad que tiene una anotación.  
  
2.  Seleccione **anotaciones**, **Editar anotación** o **Eliminar anotación**.  
  
3.  La anotación se abrirá para editar o eliminar.  
  
4.  Para eliminar todas las anotaciones a la vez, haga clic en el flujo de trabajo de diseñador y seleccione **anotación**, **eliminar todas las anotaciones**.  
  
### <a name="adding-editing-and-deleting-an-annotation-for-a-variable-or-argument"></a>Agregar, editar y eliminar una anotación para una variable o argumento  
  
1.  Haga clic con el botón secundario en una variable o argumento y seleccione Agregar anotación.  
  
2.  Escriba el texto de la anotación. La variable o argumento mostrará un icono de anotación.  
  
3.  Haga clic con el botón secundario en una variable o argumento que tiene una anotación. Seleccione Editar anotación.  
  
4.  La anotación se abrirá para editar.  
  
5.  Haga clic con el botón secundario en una variable o argumento que tiene una anotación. Seleccione Eliminar anotación.  
  
6.  La anotación se eliminará.