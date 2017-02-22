---
title: "Usar el dise&#241;ador de actividad Legacy | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "actividades, agregar secundarias"
  - "actividades, configurar"
  - "actividades, crear personalizadas"
  - "Diseñador de actividades"
  - "actividades secundarias, agregar"
  - "actividades personalizadas"
ms.assetid: 2fea8a05-6e58-423d-94bf-a822b15ffb80
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Usar el dise&#241;ador de actividad Legacy
En este tema se describe cómo usar el diseñador de actividad en [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] heredado.Use el diseñador heredado cuando tenga como destino [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 El diseñador de actividad le permite crear sus propias actividades personalizadas.  
  
## Crear una actividad personalizada  
 Siga estos pasos para crear una actividad personalizada con el diseñador de actividades:  
  
1.  En el menú **Proyecto**, haga clic en **Agregar actividad**.  
  
2.  Seleccione la plantilla **Actividad** o **Actividad \(con separación del código\)**.  
  
    1.  Use la plantilla **Actividad** para crear una actividad con la definición de actividad y el código de usuario en el mismo archivo de código.  
  
    2.  Use la plantilla **Actividad \(con separación del código\)** para crear una actividad con la definición de actividad expresada como marcado del flujo de trabajo y el código de usuario en un archivo de código independiente.  
  
3.  Escriba un nombre de actividad o mantenga el nombre predeterminado y, a continuación, haga clic en **Agregar**.  
  
 También puede crear un conjunto de actividades personalizadas creando un nuevo proyecto de tipo **Workflow Activity Library**.Para obtener más información sobre este tipo de proyecto, vea [Cómo: Crear una biblioteca de actividades de flujo de trabajo \(Heredado\)](../Topic/How%20to:%20Create%20a%20Workflow%20Activity%20Library%20\(Legacy\).md).  
  
## Configurar una actividad  
 Aunque el diseñador de actividades esté activo, puede utilizar el explorador de propiedades para configurar las propiedades enumeradas en la siguiente tabla.  
  
|Propiedad|Comentarios|  
|---------------|-----------------|  
|**Name**|Nombre de la actividad.|  
|**Base Class**|Clase base de la que deriva la actividad.La clase base predeterminada es [SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020).En la ventana **Propiedades**, haga clic en los puntos suspensivos **\[…\]** de **Clase base** para seleccionar otra clase base en el [Examinar y seleccionar un cuadro de diálogo de tipo .NET \(Heredado\)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md).|  
|**Description**|Descripción de la actividad definida por el usuario.|  
|**Enabled**|Se debe establecer de forma predeterminada en **True** para habilitar la ejecución y validación de la actividad.Se debe establecer de forma predeterminada en **False** para deshabilitar la ejecución y validación de la actividad.Para obtener información sobre la ejecución y validación de actividades, vea [Desarrollar actividades del flujo de trabajo](http://go.microsoft.com/fwlink?LinkID=65024).|  
  
## Agregar actividades secundarias  
 Puede arrastrar actividades secundarias del cuadro de herramientas hasta la actividad que esté diseñando.Puede configurar cada una de las actividades secundarias con el explorador de propiedades.  
  
## Vea también  
 [Desarrollar actividades de flujo de trabajo](http://go.microsoft.com/fwlink?LinkID=65024)   
 [Creación de actividades personalizadas](http://go.microsoft.com/fwlink?LinkID=65021)   
 [Actividades de flujo de trabajo heredadas](../workflow-designer/legacy-workflow-activities.md)   
 [Muestras de actividades personalizadas](http://go.microsoft.com/fwlink?LinkID=65022)   
 [Cómo: Crear una biblioteca de actividades de flujo de trabajo \(Heredado\)](../Topic/How%20to:%20Create%20a%20Workflow%20Activity%20Library%20\(Legacy\).md)   
 [Usar el Diseñador de flujo de trabajo heredado](../workflow-designer/using-the-legacy-workflow-designer.md)