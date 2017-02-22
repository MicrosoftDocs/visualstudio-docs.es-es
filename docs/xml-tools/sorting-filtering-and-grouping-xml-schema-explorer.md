---
title: "Ordenar, filtrar y agrupar (Explorador de esquemas XML) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Ordenar, filtrar y agrupar (Explorador de esquemas XML)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En este tema se describen las opciones que están disponibles a través del menú de **Opciones de ordenación, filtrado y agrupación** de la barra de herramientas del Explorador de esquemas XML.  
  
## Opciones de filtro  
 Están disponibles las opciones de filtro siguientes:de forma predeterminada, las opciones **Mostrar espacios de nombres** y **Mostrar archivos de esquema** están seleccionadas.  
  
-   **Mostrar espacios de nombres**.  
  
-   **Mostrar archivos de esquema**.  
  
-   **Mostrar composiciones \(sequence\/choice\/all\)**.  
  
## Opciones de ordenación  
 Están disponibles las opciones de ordenación siguientes:el valor predeterminado es **Ordenar por tipo**.Las opciones de ordenación no se aplican a archivos ni espacios de nombres.  
  
-   **Ordenar por tipo**.  
  
-   **Ordenar por nombre**.  
  
-   **Ordenar por orden de documento**.  
  
### Ordenar por tipo  
 Cuando se selecciona la opción **Ordenar por tipo**, los nodos globales se ordenan de la forma siguiente.Después, los nodos se ordenan alfabéticamente en cada grupo.  
  
1.  Nodos `import`.  
  
2.  Nodos `include`.  
  
3.  Nodos `redefine`.  
  
4.  Nodos `attribute`.  
  
5.  Nodos `attributeGroup`.  
  
6.  Nodos `complexType`.  
  
7.  Nodos `simpleType`.  
  
8.  Nodos `element`.  
  
9. Nodos `group`.  
  
### Ordenar por nombre  
 Cuando se selecciona la opción **Ordenar por nombre**, los nodos globales se ordenan de la forma siguiente:  
  
1.  nodos `import` \(por orden alfabético de espacios de nombres\).  
  
2.  nodos `include` \(por orden alfabético de atributos `schemaLocation`\).  
  
3.  nodos `redefine` \(por orden alfabético de atributos `schemaLocation`\).  
  
4.  Otros nodos globales por orden alfabético.  
  
### Orden del documento  
 La opción **Ordenar por orden de documento** está disponible cuando se selecciona la opción **Mostrar archivos de esquema**.Cuando se selecciona **Ordenar por orden de documento**, los nodos globales se muestran en el orden en que aparecen en el archivo de esquema.  
  
## Opciones de ordenación y filtrado persistentes  
 Las opciones de ordenación, filtrado y agrupación se guardan en el Registro para cada usuario, independientemente de la solución o de los archivos que estuvieran abiertos cuando se cambió la configuración.