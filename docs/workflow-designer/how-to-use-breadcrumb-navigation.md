---
title: 'Diseñador de flujo de trabajo: Cómo usar la ruta de navegación'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4a688056-37dc-406a-9071-be2141e192fe
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 291badb04c791305f655e187ff7853fc8c5087a1
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75584574"
---
# <a name="how-to-use-breadcrumb-navigation"></a>Utilizar la ruta de navegación

Hay tres formas principales de cambiar el conjunto de actividades que se muestran en Diseñador de flujo de trabajo:

1. Haga doble clic para desplazarse hasta una actividad secundaria.

2. Haga clic en un botón en la barra de ruta de navegación para desplazarse hasta una actividad antecesora.

3. Expanda o contraiga las actividades que aparecen.

## <a name="using-breadcrumb-navigation"></a>Utilizar la barra de ruta de navegación

1. Haga doble clic en una actividad de Diseñador de flujo de trabajo para cambiar la actividad raíz a la actividad en la que hizo clic. La actividad en la que se hace clic se expande por completo en la raíz y sus antecesores se muestran en la barra de ruta de navegación. En ocasiones esto se denomina aumentar o disminuir el detalle de una actividad.

2. Para desplazarse hasta un antecesor de la actividad raíz actual, haga clic en la actividad en la barra de ruta de navegación.

## <a name="expanding-or-collapsing-an-activity-in-place"></a>Expandir o contraer una actividad en el sitio

1. Al hacer clic en el botón de contenido adicional de una actividad, se expande o contrae la actividad en el sitio.

2. Cuando se modifica el estado del estado de expansión al hacer clic en el botón, se guarda el nuevo estado de expansión en XAML.

    > [!WARNING]
    > No todas las actividades se pueden expandir en el sitio. Existen dos casos en los que una actividad no se puede expandir en el sitio: cuando el elemento primario de la actividad no permite la expansión de sus elementos secundarios en el sitio, (por ejemplo, las actividades en un diagrama de flujo no se pueden expandir en el sitio) o cuando el diseñador de actividades no tiene permitido expandirse en el sitio. Aunque ninguno de los diseñadores de actividad incluidos en Diseñador de flujo de trabajo tiene el último comportamiento, algunas actividades personalizadas pueden presentar este comportamiento.

## <a name="expanding-all-or-collapsing-all-activities"></a>Expandir o contraer todas las actividades

1. Use los botones **expandir todo** y **contraer todo** en la interfaz de usuario para expandir o contraer todas las actividades de la raíz de la ruta de navegación actual. Observe que las acciones de expandir y contraer todas las actividades son estados globales. Esto significa que cuando se cambia la actividad raíz mediante la navegación por la ruta de navegación, el estado expandir todo o contraer todo persiste hasta que se hace clic en **restaurar**.

2. Después de aplicar un estado expandir todo o contraer todo, puede hacer clic en el botón **restaurar** que aparece para volver a examinar el estado aplicado previamente a cada actividad.

    > [!WARNING]
    > Si una actividad, como <xref:System.Activities.Statements.Flowchart>, ha optado por expandirse en su lugar, la funcionalidad asociada con los botones **expandir todo** y **contraer todo** está deshabilitada en el diseñador de **diagramas de flujo** . Para obtener más información sobre el diseñador de **diagramas de flujo** , vea el tema [Diagrama de flujo](../workflow-designer/flowchart-activity-designer.md) .

    > [!WARNING]
    > Expandir todo también tiene un efecto especial en los diseñadores de actividad **Switch** y **TryCatch** . Al hacer clic en **expandir todo**, se muestran todos los casos de cambio y todos los bloques try/catch/finally. Al hacer clic en **restaurar** o **contraer todo** , se devuelven estos diseñadores a su estado predeterminado, desde el que puede hacer clic en un caso o bloque individual para ver su contenido.
