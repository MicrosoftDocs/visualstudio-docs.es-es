---
title: Filtrar Usar ruta de navegación | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 4a688056-37dc-406a-9071-be2141e192fe
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8327565d9705c8522442acc77899fe171a5bf12d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58997672"
---
# <a name="how-to-use-breadcrumb-navigation"></a>Filtrar Usar la ruta de navegación
Existen tres formas principales de cambiar el conjunto de actividades que se muestran en [!INCLUDE[wfd1](../includes/wfd1-md.md)]:  
  
1.  Haga doble clic para desplazarse hasta una actividad secundaria.  
  
2.  Haga clic en un botón en la barra de ruta de navegación para desplazarse hasta una actividad antecesora.  
  
3.  Expanda o contraiga las actividades que aparecen.  
  
### <a name="using-breadcrumb-navigation"></a>Utilizar la barra de ruta de navegación  
  
1.  Haga doble clic en una actividad de [!INCLUDE[wfd2](../includes/wfd2-md.md)] para cambiar la actividad raíz a la actividad donde ha hecho clic. A continuación, la actividad donde ha hecho clic se expande totalmente desde la raíz y se muestran sus antecesores en la barra de ruta de navegación. En ocasiones esto se denomina aumentar o disminuir el detalle de una actividad.  
  
2.  Para desplazarse hasta un antecesor de la actividad raíz actual, haga clic en la actividad en la barra de ruta de navegación.  
  
### <a name="expanding-or-collapsing-an-activity-in-place"></a>Expandir o contraer una actividad en el sitio  
  
1.  Al hacer clic en el botón de contenido adicional de una actividad, se expande o contrae la actividad en el sitio.  
  
2.  Cuando se modifica el estado del estado de expansión al hacer clic en el botón, se guarda el nuevo estado de expansión en XAML.  
  
    > [!WARNING]
    >  No todas las actividades se pueden expandir en el sitio. Existen dos casos en los que una actividad no se puede expandir en el sitio: cuando el elemento primario de la actividad no permite la expansión de sus elementos secundarios en el sitio, (por ejemplo, las actividades en un diagrama de flujo no se pueden expandir en el sitio) o cuando el diseñador de actividades no tiene permitido expandirse en el sitio. Aunque ninguno de los diseñadores de actividad que se incluyen en [!INCLUDE[wfd2](../includes/wfd2-md.md)] se comportan según esta última posibilidad, algunas actividades personalizadas pueden exhibir este comportamiento.  
  
### <a name="expanding-all-or-collapsing-all-activities"></a>Expandir o contraer todas las actividades  
  
1.  Use la **Expandir todo** y **Contraer todo** botones en la interfaz de usuario para expandir o contraer todas las actividades bajo la raíz de la ruta de navegación actual. Observe que las acciones de expandir y contraer todas las actividades son estados globales. Esto significa que al cambiar la actividad raíz mediante la ruta de navegación, la expansión de todas o contraer todo el estado persiste hasta que haga clic **restaurar**.  
  
2.  Una vez que se ha aplicado expandir todas o contraer todos los Estados, haga clic en el **restaurar** botón que aparece para volver a comprobar el estado previamente aplicado a cada actividad.  
  
    > [!WARNING]
    >  Si una actividad, como <xref:System.Activities.Statements.Flowchart>, ha salido del estado de expansión en su lugar, la funcionalidad asociada con el **Expandir todo** y **Contraer todo** botones está deshabilitado en el **diagrama de flujo**  diseñador. [!INCLUDE[crabout](../includes/crabout-md.md)] el **Flowchart** designer, vea el [Flowchart](../workflow-designer/flowchart-activity-designer.md) tema.  
  
    > [!WARNING]
    >  Expandir todo tiene también un efecto especial **conmutador** y **TryCatch** diseñadores de actividad. Al hacer clic en **Expandir todo**, se muestran todos los casos de conmutador y todos los bloques try/catch/finally. Al hacer clic en **restaurar** o **Contraer todo** devuelve estos diseñadores a su estado predeterminado, desde el que puede hacer clic en un caso o bloque individuales para ver su contenido.