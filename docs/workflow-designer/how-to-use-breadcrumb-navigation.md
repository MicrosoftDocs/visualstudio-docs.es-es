---
title: "Cómo: usar la ruta de navegación | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4a688056-37dc-406a-9071-be2141e192fe
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: c66c11c3e43b7efbb025b6ea44c4a686c95b47e7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-use-breadcrumb-navigation"></a>Utilizar la ruta de navegación
Existen tres formas principales de cambiar el conjunto de actividades que se muestran en [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]:  
  
1.  Haga doble clic para desplazarse hasta una actividad secundaria.  
  
2.  Haga clic en un botón en la barra de ruta de navegación para desplazarse hasta una actividad antecesora.  
  
3.  Expanda o contraiga las actividades que aparecen.  
  
### <a name="using-breadcrumb-navigation"></a>Utilizar la barra de ruta de navegación  
  
1.  Haga doble clic en una actividad de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] para cambiar la actividad raíz a la actividad donde ha hecho clic. A continuación, la actividad donde ha hecho clic se expande totalmente desde la raíz y se muestran sus antecesores en la barra de ruta de navegación. En ocasiones esto se denomina aumentar o disminuir el detalle de una actividad.  
  
2.  Para desplazarse hasta un antecesor de la actividad raíz actual, haga clic en la actividad en la barra de ruta de navegación.  
  
### <a name="expanding-or-collapsing-an-activity-in-place"></a>Expandir o contraer una actividad en el sitio  
  
1.  Al hacer clic en el botón de contenido adicional de una actividad, se expande o contrae la actividad en el sitio.  
  
2.  Cuando se modifica el estado del estado de expansión al hacer clic en el botón, se guarda el nuevo estado de expansión en XAML.  
  
    > [!WARNING]
    >  No todas las actividades se pueden expandir en el sitio. Existen dos casos en los que una actividad no se puede expandir en el sitio: cuando el elemento primario de la actividad no permite la expansión de sus elementos secundarios en el sitio, (por ejemplo, las actividades en un diagrama de flujo no se pueden expandir en el sitio) o cuando el diseñador de actividades no tiene permitido expandirse en el sitio. Aunque ninguno de los diseñadores de actividad que se incluyen en [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] se comportan según esta última posibilidad, algunas actividades personalizadas pueden exhibir este comportamiento.  
  
### <a name="expanding-all-or-collapsing-all-activities"></a>Expandir o contraer todas las actividades  
  
1.  Use la **Expandir todo** y **Contraer todo** botones en la interfaz de usuario para expandir o contraer todas las actividades bajo la raíz de la ruta de navegación actual. Observe que las acciones de expandir y contraer todas las actividades son estados globales. Esto significa que al cambiar la actividad raíz mediante la ruta de navegación, expandir todas o contraer todo el estado persiste hasta que haga clic **restaurar**.  
  
2.  Después de que se ha aplicado expandir todas o contraer todas, puede hacer clic en el **restaurar** botón que aparece para volver atrás y comprobar el estado que se había aplicado anteriormente a cada actividad.  
  
    > [!WARNING]
    >  Si una actividad, como <xref:System.Activities.Statements.Flowchart>, ha salido del estado de expansión en su lugar, la funcionalidad asociada con el **Expandir todo** y **Contraer todo** botones está deshabilitado en el **diagrama de flujo**  diseñador. [!INCLUDE[crabout](../test/includes/crabout_md.md)]el **Flowchart** designer, vea el [Flowchart](../workflow-designer/flowchart-activity-designer.md) tema.  
  
    > [!WARNING]
    >  Expandir todo tiene también un efecto especial en **conmutador** y **TryCatch** diseñadores de actividad. Al hacer clic en **Expandir todo**, se muestran todos los casos de conmutador y todos los bloques try/catch/finally. Haga clic en **restaurar** o **Contraer todo** estos diseñadores vuelven a su estado predeterminado, desde el que puede hacer clic en un caso o bloque individuales para ver su contenido.