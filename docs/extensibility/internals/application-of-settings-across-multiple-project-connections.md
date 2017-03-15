---
title: "Aplicaci&#243;n de configuraci&#243;n a trav&#233;s de varias conexiones de proyecto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "origen control complementos, aplicación de configuración"
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Aplicaci&#243;n de configuraci&#243;n a trav&#233;s de varias conexiones de proyecto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un complemento de control de código fuente compilado mediante el Control de origen API de complemento 1,2, puede utilizar una operación de lote para ejecutar la misma operación de control de código fuente en varios proyectos o varios contextos de la conexión.  Los lotes se pueden utilizar para eliminar redundante, cuadros de diálogo por\-proyecto de la experiencia del usuario.  
  
 Si un usuario selecciona varios elementos que pertenecen a más de una conexión en un complemento de control de código fuente compilado mediante el Control de origen API de complemento 1,1, \(por ejemplo, dos proyectos web en equipos diferentes de la archivo\-acción\) y los desprotegidos, el usuario ve el mismo cuadro de diálogo repetidamente.  Esto ocurre incluso si el usuario hace clic en la casilla de **Aplicar a todo** en el cuadro de diálogo, porque el IDE restaura su estado para cada contexto de conexión.  
  
## Nueva marca de capacidad  
 la función de`SccBeginBatch` establece la marca de `SCC_CAP_BATCH` para indicar que una operación de lote está en curso  
  
## nuevas funciones  
 Las nuevas funciones siguientes admiten la operación por lotes:  
  
-   [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)  
  
-   [SccEndBatch](../../extensibility/sccendbatch-function.md)  
  
 La función de `SCCBeginBatch` inicia un grupo de operaciones de control de código fuente.  `SccEndBatch` cierra el grupo.  Los grupos pueden no estar anidados.  
  
## Vea también  
 [Novedades de la API de complemento de origen Control versión 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)