---
title: "Introducci&#243;n general a las herramientas de dise&#241;o del modelo BDC | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.BDC.Method_Details"
  - "VS.SharePointTools.BDC.Explorer"
  - "VS.SharePointTools.BDC.Diagram"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC [desarrollo de SharePoint en Visual Studio], Explorador de BDC"
  - "BDC [desarrollo de SharePoint en Visual Studio], diseñador"
  - "BDC [desarrollo de SharePoint en Visual Studio], detalles del método"
  - "BDC [desarrollo de SharePoint en Visual Studio], herramientas visuales"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], Explorador de BDC"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], diseñador"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], detalles del método"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], herramientas visuales"
ms.assetid: dbd7b746-9e93-4ed4-a546-4a6f17a4725f
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Introducci&#243;n general a las herramientas de dise&#241;o del modelo BDC
  Puede diseñar un modelo de Conectividad a datos profesionales \(BDC\) utilizando el Diseñador de BDC, la ventana **Detalles del método de BDC** y el **Explorador de BDC**.  
  
 El **Explorador de BDC** le permite examinar el modelo, buscar en el modelo y definir los descriptores de tipos.  
  
## Diseñador de BDC  
 El Diseñador de BDC le permite definir las entidades de su modelo y organizar visualmente las relaciones mutuas.  Utilice el Diseñador de BDC para llevar a cabo las siguientes tareas:  
  
-   Agregar entidades al modelo.  
  
-   Quitar entidades del modelo.  
  
-   Definir relaciones entre las entidades.  
  
 Para abrir el diseñador de BDC, haga doble clic en el archivo de modelo del proyecto, o abrir el menú contextual para el archivo modelo y elegir **Abierta**.  Agregue una entidad al modelo arrastrando o copiando **Entidad** de **Cuadro de herramientas** sobre el diseñador.  Para crear una asociación entre dos entidades, elija el control de **Asociación** en **Cuadro de herramientas**, elija la primera entidad, y elija la segunda.  
  
## Ventana Detalles del método de BDC  
 Utilice la ventana **Detalles del método de BDC** para definir los parámetros, las instancias y los descriptores de filtro de un método.  
  
 Puede generar rápidamente métodos Finder, Finder específico, Creator, Updater y Deleter en la ventana **Detalles del método de BDC**.  Al generar estos métodos, Visual Studio agrega metadatos, como parámetros, instancias y descriptores de tipos, al método.  Puede modificar estos metadatos para adaptarlos a un escenario concreto.  
  
 Para abrir la ventana de **Detalles del método de BDC** , en la barra de menú, elija **Visualización**, **Otras ventanas**, **Detalles del método de BDC**.  
  
 Para ver los métodos en la ventana de **Detalles del método de BDC** , elija la entidad en el diseñador de BDC.  Los métodos de la entidad seleccionada aparecen en la ventana **Detalles del método de BDC**.  Si no elige una entidad en el diseñador de BDC, la ventana de **Detalles del método de BDC** no muestra ninguna información.  
  
 Expanda o contraiga los nodos en la ventana **Detalles del método de BDC** para definir parámetros, instancias y descriptores de filtro.  Utilice el **Explorador de BDC** para definir los descriptores de tipo.  
  
## Explorador de BDC  
 El **Explorador de BDC** muestra los elementos que constituyen el modelo.  Para abrir **Explorador de BDC**, en la barra de menú, elija **Visualización**, **Otras ventanas**, **Explorador de BDC**.  Para examinar el modelo, expanda los nodos en el **Explorador de BDC**.  Cada nodo representa un elemento en el XML del archivo del modelo.  
  
 Cuando elige nodos en **Explorador de BDC**, las propiedades de cada nodo que elija aparecen en la ventana de **Propiedades** .  Muchas de estas propiedades corresponden a los atributos del archivo del modelo.  Puede buscar en el modelo usando el cuadro de búsqueda de la parte superior del **Explorador de BDC**.  
  
> [!NOTE]  
>  El **Explorador de BDC** no muestra identificadores, propiedades personalizadas, cadenas adaptadas, grupos de asociaciones, acciones, filtran descriptores, listas de control de acciones y los valores de parámetro predeterminados.  
  
### Definir descriptores de tipo  
 Utilice el **Explorador de BDC** para definir los descriptores de tipo.  El Explorador de BDC permite definir un descriptor de tipos en una ocasión y después reutilizarlo en otra parte del modelo.  Para ello, copie el descriptor de tipos y péguelo en cualquier otro parámetro o descriptor de tipos.  
  
> [!NOTE]  
>  Los cambios hechos en un descriptor de tipos original no afecta a las copias de ese descriptor de tipos.  
  
 Para obtener más información, vea [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
## Vea también  
 [Cómo: Crear un modelo BDC](../sharepoint/how-to-create-a-bdc-model.md)   
 [Cómo: Agregar una entidad a un modelo](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Cómo: Agregar un método Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Cómo: Agregar un método Finder específico](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Cómo: Agregar un método Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Cómo: Agregar un método Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Cómo: Agregar un método Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Crear una asociación entre entidades](../sharepoint/creating-an-association-between-entities.md)   
 [Tutorial: Crear una lista externa en SharePoint con datos profesionales](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)   
 [Integrar Datos profesionales en SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)   
 [Crea un modelo de conectividad a datos profesionales](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  