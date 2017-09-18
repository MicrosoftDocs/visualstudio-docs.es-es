---
title: "C&#243;mo: Crear un conjunto de reglas para PolicyActivity (Heredado) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "PolicyActivity, actividad, crear conjuntos de reglas"
  - "PolicyActivity, actividad, seleccionar conjuntos de reglas"
  - "Cuadro de diálogo Editor de conjunto de reglas"
  - "conjuntos de reglas, crear para PolicyActivity"
  - "cuadro de diálogo Seleccionar conjunto de reglas"
ms.assetid: f272489d-3342-4511-8b59-6a0fd7a42d70
caps.latest.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# C&#243;mo: Crear un conjunto de reglas para PolicyActivity (Heredado)
En este tema se describe cómo crear un conjunto de reglas de actividades de directiva mediante [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] heredado que tiene como destino [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Una vez que haya arrastrado un elemento de la actividad **Policy** del **Cuadro de herramientas** a la superficie de diseño del flujo de trabajo, deseará seleccionar una regla existente o crear un conjunto de reglas nuevo para la actividad [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019).Un conjunto de reglas existente se selecciona utilizando el [Seleccionar conjunto de reglas \(Cuadro de diálogo\) \(Heredado\)](../workflow-designer/select-rule-set-dialog-box-legacy.md) y los conjuntos de reglas se crean utilizando [Editor de conjunto de reglas \(Cuadro de diálogo\) \(Heredado\)](../workflow-designer/rule-set-editor-dialog-box-legacy.md).  
  
> [!NOTE]
>  Puede abrir directamente el cuadro de diálogo [Editor de conjunto de reglas \(Cuadro de diálogo\) \(Heredado\)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) haciendo doble clic en una actividad [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)PolicyActivity que esté en la superficie de diseño del flujo de trabajo.  
  
### Para seleccionar o crear un conjunto de reglas para una actividad PolicyActivity  
  
1.  Haga doble clic en la actividad [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) y, a continuación, haga clic en **Propiedades** para que se abra la ventana **Propiedades**.  
  
2.  Haga clic en la propiedad **RuleSetReference**.  
  
3.  Realice una de estas acciones:  
  
    -   Haga clic en los puntos suspensivos de **RuleSetReference**, **\[...\]** y, a continuación, seleccione un conjunto de reglas existente en el cuadro de diálogo [Seleccionar conjunto de reglas \(Cuadro de diálogo\) \(Heredado\)](../workflow-designer/select-rule-set-dialog-box-legacy.md).A continuación, vaya al paso 10.  
  
         – O bien –  
  
    -   Escriba un nombre para un conjunto de reglas.Haga clic en los puntos suspensivos de **de RuleSetReference**, **\[...\]** y, a continuación, seleccione **Editar** en el cuadro de diálogo [Seleccionar conjunto de reglas \(Cuadro de diálogo\) \(Heredado\)](../workflow-designer/select-rule-set-dialog-box-legacy.md).  
  
         o bien  
  
    -   Escriba un nombre para un conjunto de reglas.Expanda la propiedad **RuleSetReference** y seleccione los puntos suspensivos **\[...\]** de la propiedad **RuleSet Definition**.  
  
         Se abre el [Editor de conjunto de reglas \(Cuadro de diálogo\) \(Heredado\)](../workflow-designer/rule-set-editor-dialog-box-legacy.md).  
  
4.  En el cuadro de diálogo [Editor de conjunto de reglas \(Cuadro de diálogo\) \(Heredado\)](../workflow-designer/rule-set-editor-dialog-box-legacy.md), haga clic en **Agregar regla** para agregar una nueva regla al conjunto de reglas.  
  
5.  Escriba las propiedades **Nombre**, **Prioridad** y **Reevaluación**, o mantenga los valores predeterminados.  
  
6.  Escriba el texto de la **Condición**.  
  
7.  Escriba el texto para **Acciones Then** y **Acciones Else**.  
  
8.  Vuelva a hacer clic en **Agregar regla** para agregar otra regla.  
  
9. Cuando termine, haga clic en **Aceptar**.  
  
## Vea también  
 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)   
 [Seleccionar conjunto de reglas \(Cuadro de diálogo\) \(Heredado\)](../workflow-designer/select-rule-set-dialog-box-legacy.md)   
 [Editor de conjunto de reglas \(Cuadro de diálogo\) \(Heredado\)](../workflow-designer/rule-set-editor-dialog-box-legacy.md)   
 [Uso de PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004)   
 [Actividades de flujo de trabajo heredadas](../workflow-designer/legacy-workflow-activities.md)