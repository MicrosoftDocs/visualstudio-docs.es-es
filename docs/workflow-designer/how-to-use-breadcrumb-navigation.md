---
title: 'Diseñador de flujo de trabajo - Cómo: Usar la ruta de navegación'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4a688056-37dc-406a-9071-be2141e192fe
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: de1004dd7a62fe4163147db4928783dd9a0dca98
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60049575"
---
# <a name="how-to-use-breadcrumb-navigation"></a>Procedimiento Usar la ruta de navegación

Hay tres maneras principales para cambiar el conjunto de actividades que se muestran en el Diseñador de flujo de trabajo:

1. Haga doble clic para desplazarse hasta una actividad secundaria.

2. Haga clic en un botón en la barra de ruta de navegación para desplazarse hasta una actividad antecesora.

3. Expanda o contraiga las actividades que aparecen.

## <a name="using-breadcrumb-navigation"></a>Utilizar la barra de ruta de navegación

1. Haga doble clic en una actividad del Diseñador de flujo de trabajo para cambiar la actividad raíz a la actividad donde ha hecho clic. La actividad donde ha hecho clic, a continuación, se expande totalmente en la raíz y sus antecesores se muestran en la barra de ruta de navegación. En ocasiones esto se denomina aumentar o disminuir el detalle de una actividad.

2. Para desplazarse hasta un antecesor de la actividad raíz actual, haga clic en la actividad en la barra de ruta de navegación.

## <a name="expanding-or-collapsing-an-activity-in-place"></a>Expandir o contraer una actividad en el sitio

1. Al hacer clic en el botón de contenido adicional de una actividad, se expande o contrae la actividad en el sitio.

2. Cuando se modifica el estado del estado de expansión al hacer clic en el botón, se guarda el nuevo estado de expansión en XAML.

    > [!WARNING]
    > No todas las actividades se pueden expandir en el sitio. Existen dos casos en los que una actividad no se puede expandir en el sitio: cuando el elemento primario de la actividad no permite la expansión de sus elementos secundarios en el sitio, (por ejemplo, las actividades en un diagrama de flujo no se pueden expandir en el sitio) o cuando el diseñador de actividades no tiene permitido expandirse en el sitio. Aunque ninguno de los diseñadores de actividades incluidos en el Diseñador de flujo de trabajo tiene el comportamiento de este último, algunas actividades personalizadas pueden exhibir este comportamiento.

## <a name="expanding-all-or-collapsing-all-activities"></a>Expandir o contraer todas las actividades

1. Use la **Expandir todo** y **Contraer todo** botones en la interfaz de usuario para expandir o contraer todas las actividades bajo la raíz de la ruta de navegación actual. Observe que las acciones de expandir y contraer todas las actividades son estados globales. Esto significa que al cambiar la actividad raíz mediante la ruta de navegación, la expansión de todas o contraer todo el estado persiste hasta que haga clic **restaurar**.

2. Una vez que se ha aplicado expandir todas o contraer todos los Estados, haga clic en el **restaurar** botón que aparece para volver a comprobar el estado previamente aplicado a cada actividad.

    > [!WARNING]
    > Si una actividad, como <xref:System.Activities.Statements.Flowchart>, ha salido del estado de expansión en su lugar, la funcionalidad asociada con el **Expandir todo** y **Contraer todo** botones está deshabilitado en el **diagrama de flujo**  diseñador. Para obtener más información sobre la **Flowchart** designer, vea el [Flowchart](../workflow-designer/flowchart-activity-designer.md) tema.

    > [!WARNING]
    > Expandir todo tiene también un efecto especial **conmutador** y **TryCatch** diseñadores de actividad. Al hacer clic en **Expandir todo**, se muestran todos los casos de conmutador y todos los bloques try/catch/finally. Al hacer clic en **restaurar** o **Contraer todo** devuelve estos diseñadores a su estado predeterminado, desde el que puede hacer clic en un caso o bloque individuales para ver su contenido.