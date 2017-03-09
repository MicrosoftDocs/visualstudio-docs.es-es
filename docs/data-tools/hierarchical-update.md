---
title: "Actualizaci&#243;n jer&#225;rquica | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "datos [Visual Basic], actualización jerárquica"
  - "conjuntos de datos [Visual Basic], actualización jerárquica"
  - "actualización jerárquica"
  - "guardar datos modificados"
  - "tablas relacionadas, guardar"
  - "guardar datos, datos modificados"
  - "guardar datos, actualización jerárquica"
  - "guardar datos actualizados"
  - "guardar datos actualizados"
ms.assetid: 68bae3f6-ec9b-45ee-a33a-69395029f54c
caps.latest.revision: 26
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Actualizaci&#243;n jer&#225;rquica
La *actualización jerárquica* se refiere al proceso de volver a guardar los datos actualizados \(de un conjunto de datos con dos o más tablas relacionadas\) en una base de datos manteniendo las reglas de integridad referencial.  La *integridad referencial* consiste en las reglas de coherencia proporcionadas por las restricciones de una base de datos que controlan el comportamiento de las operaciones de inserción, actualización y eliminación de registros relacionados.  Por ejemplo, es integridad referencial que exige la creación de un registro de cliente antes de permitir crear órdenes para ese cliente.  
  
 Guardar los datos modificados de las tablas de datos relacionadas es un poco más complejo que guardar los datos en una tabla única.  Esto se debe a que los comandos Update, Insert y Delete para cada tabla relacionada tienen que ejecutarse en un orden concreto para evitar infringir las restricciones de integridad referencial.  Por ejemplo, considere una aplicación de entrada de orden con la que puede administrar tanto los clientes y pedidos nuevos, como los existentes.  Si tiene que eliminar un cliente existente, debe eliminar todos los pedidos de ese cliente antes de eliminar el registro de cliente.  Si agrega un nuevo cliente \(con un pedido\), debe insertar el nuevo registro de cliente antes de insertar los pedidos de ese cliente debido a las restricciones FOREIGN KEY que existen en las tablas.  Como se muestra en estos ejemplos, debe extraer los subconjuntos de datos concretos y enviar las actualizaciones \(inserciones, actualizaciones y eliminaciones\) en el orden correcto para mantener la integridad referencial.  
  
 La característica de actualización jerárquica usa `TableAdapterManager` para administrar `TableAdapter`s en un conjunto de datos con tipo.  El componente `TableAdapterManager` es un componente generado por [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], con lo que no forma parte de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Para obtener información detallada sobre la clase `TableAdapterManager`, vea la sección de referencia de TableAdapterManager de [Información general sobre TableAdapterManager](../Topic/TableAdapterManager%20Overview.md).  
  
 Si la aplicación usa conjuntos de datos con tipo y proporciona a los usuarios la capacidad de modificar los datos de tablas de datos relacionadas \(tablas de datos en una relación uno a varios, como Clientes y Pedidos\), probablemente deseará usar la actualización jerárquica.  
  
## En esta sección  
 [Información general sobre la actualización jerárquica](../Topic/Hierarchical%20Update%20Overview.md)  
 Explica qué es la actualización jerárquica y proporciona detalles de cómo se implementa.  
  
 [Información general sobre TableAdapterManager](../Topic/TableAdapterManager%20Overview.md)  
 Explica qué es `TableAdapterManager` y proporciona descripciones del código `TableAdapterManager` generado por el Diseñador de DataSet.  
  
 [Cómo: Habilitar y deshabilitar la actualización jerárquica](../Topic/How%20to:%20Enable%20and%20Disable%20Hierarchical%20Update.md)  
 Describe cómo establecer la propiedad `Hierarchical Update` de un conjunto de datos con tipo para generar el código para guardar tablas relacionadas.  
  
 [Cómo: Configurar restricciones FOREIGN KEY en un conjunto de datos](../Topic/How%20to:%20Configure%20Foreign-Key%20Constraints%20in%20a%20Dataset.md)  
 Describe cómo configurar las restricciones en un conjunto de datos.  
  
 [Cómo: Confirmar tareas de edición en proceso en controles enlazados a datos antes de guardar los datos](../data-tools/commit-in-process-edits-on-data-bound-controls-before-saving-data.md)  
 Describe cómo detener todos los cambios en proceso de los controles con enlace a datos en un formulario para preparar el origen de datos para guardarlo.  
  
 [Cómo: Establecer el orden al realizar una actualización jerárquica](../Topic/How%20to:%20Set%20the%20Order%20When%20Performing%20a%20Hierarchical%20Update.md)  
 Describe cómo establecer la propiedad `UpdateOrder` de `TableAdapterManager` para controlar el orden en el que se deben realizar las inserciones, actualizaciones y eliminaciones.  
  
 [Cómo: Implementar una actualización jerárquica en proyectos de Visual Studio existentes](../Topic/How%20to:%20Implement%20Hierarchical%20Update%20in%20Existing%20Visual%20Studio%20Projects.md)  
 Describe cómo actualizar una aplicación con tablas de datos relacionadas para guardar los datos mediante `TableAdapterManager`.  
  
 [Tutorial: Guardar datos de tablas de datos relacionadas \(actualización jerárquica\)](../Topic/Walkthrough:%20Saving%20Data%20from%20Related%20Data%20Tables%20\(Hierarchical%20Update\).md)  
 Proporciona instrucciones paso a paso para crear una aplicación con tablas de datos relacionadas y guardar los datos mediante `TableAdapterManager`.  
  
## Referencia  
 <xref:System.Data.DataSet>  
  
 <xref:System.Data.DataTable>  
  
## Secciones relacionadas  
 [Trabajar con conjuntos de datos en aplicaciones de n capas](../data-tools/work-with-datasets-in-n-tier-applications.md)  
  
 [Guardar datos](../data-tools/saving-data.md)  
  
 [Crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md)  
  
 [TableAdapters](../Topic/TableAdapters.md)  
  
 [DataSets, DataTables y DataViews](../Topic/DataSets,%20DataTables,%20and%20DataViews.md)  
  
 [DataTables](../Topic/DataTables.md)  
  
 [Obtener acceso a los datos en Visual Studio](../data-tools/accessing-data-in-visual-studio.md)