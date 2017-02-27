---
title: "Utilizar la ruta de navegaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 4a688056-37dc-406a-9071-be2141e192fe
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Utilizar la ruta de navegaci&#243;n
Existen tres formas principales de cambiar el conjunto de actividades que se muestran en [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]:  
  
1.  Haga doble clic para desplazarse hasta una actividad secundaria.  
  
2.  Haga clic en un botón en la barra de ruta de navegación para desplazarse hasta una actividad antecesora.  
  
3.  Expanda o contraiga las actividades que aparecen.  
  
### Utilizar la barra de ruta de navegación  
  
1.  Haga doble clic en una actividad de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] para cambiar la actividad raíz a la actividad donde ha hecho clic.A continuación, la actividad donde ha hecho clic se expande totalmente desde la raíz y se muestran sus antecesores en la barra de ruta de navegación.En ocasiones esto se denomina aumentar o disminuir el detalle de una actividad.  
  
2.  Para desplazarse hasta un antecesor de la actividad raíz actual, haga clic en la actividad en la barra de ruta de navegación.  
  
### Expandir o contraer una actividad en el sitio  
  
1.  Al hacer clic en el botón de contenido adicional de una actividad, se expande o contrae la actividad en el sitio.  
  
2.  Cuando se modifica el estado del estado de expansión al hacer clic en el botón, se guarda el nuevo estado de expansión en XAML.  
  
    > [!WARNING]
    >  No todas las actividades se pueden expandir en el sitio.Existen dos casos en los que una actividad no se puede expandir en el sitio: cuando el elemento primario de la actividad no permite la expansión de sus elementos secundarios en el sitio, \(por ejemplo, las actividades en un diagrama de flujo no se pueden expandir en el sitio\) o cuando el diseñador de actividades no tiene permitido expandirse en el sitio.Aunque ninguno de los diseñadores de actividad que se incluyen en [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] se comportan según esta última posibilidad, algunas actividades personalizadas pueden exhibir este comportamiento.  
  
### Expandir o contraer todas las actividades  
  
1.  Utilice los botones **Expandir todo** y **Contraer todo** en la interfaz de usuario para expandir o contraer todas las actividades de la raíz de la ruta de navegación actual.Observe que las acciones de expandir y contraer todas las actividades son estados globales.Lo cual quiere decir que al cambiar la actividad raíz mediante la ruta de navegación, el estado expandir todos o contraer todos persistirá hasta que haga clic en **Restaurar**.  
  
2.  Después de haber aplicado el estado de expandir todas o contraer todas, puede hacer clic en el botón **Restaurar** que aparece para volver atrás y comprobar el estado que se había aplicado anteriormente a cada actividad.  
  
    > [!WARNING]
    >  Si una actividad, como <xref:System.Activities.Statements.Flowchart>, se ha salido del estado de expansión activo, la funcionalidad asociada con los botones **Expandir todo** y **Contraer todo** se deshabilita en el diseñador **Flowchart**.[!INCLUDE[crabout](../test/includes/crabout_md.md)] el diseñador de **Diagrama de flujo**, vea el tema [Diagrama de flujo](../workflow-designer/flowchart-activity-designer.md).  
  
    > [!WARNING]
    >  Expandir todo tiene también un efecto especial en los diseñadores de actividades **Switch** y **TryCatch**.Al hacer clic en **Expandir todo**, se muestran todos los casos de la instrucción switch y todos los bloques try\/catch\/finally.Al hacer clic en **Restaurar** o **Contraer todo** estos diseñadores vuelven a su estado predeterminado, desde el cual se puede hacer clic en un caso o bloque individuales para ver su contenido.