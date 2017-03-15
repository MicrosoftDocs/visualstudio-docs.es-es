---
title: "Herramientas de Entity Data Model de ADO.NET | Microsoft Docs"
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
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
caps.latest.revision: 21
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Herramientas de Entity Data Model de ADO.NET
Las herramientas de [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] están diseñadas para ayudarle a compilar aplicaciones [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)].  Toda la documentación de las herramientas de [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] se encuentra aquí: [ADO.NET Entity Data Model  Tools](http://msdn.microsoft.com/es-es/91076853-0881-421b-837a-f582f36be527).  
  
 Con las herramientas de [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)], puede crear un *modelo conceptual* a partir de una base de datos existente y, a continuación, visualizarlo y editarlo de forma gráfica.  O bien, puede crear primero un gráfico del modelo conceptual y, a continuación, generar una base de datos que sea compatible con ese modelo.  En cualquier caso, puede actualizar automáticamente el modelo a medida que la base de datos subyacente cambia y generar automáticamente código de capa de objeto para la aplicación.  La generación de bases de datos y la generación de código de capa de objeto se pueden personalizar.  
  
 En la lista siguiente se describen las herramientas concretas que conforman las herramientas de Entity Data Model:  
  
-   El diseñador de [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] \(Entity Designer\) permite crear y modificar de forma visual entidades, asociaciones, asignaciones y relaciones de herencia.  Entity Designer también genera código de capa de objeto de [!INCLUDE[TLA#tla_cshrp](../data-tools/includes/tlasharptla_cshrp_md.md)] o [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  
  
-   El Asistente de [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] permite generar un modelo conceptual a partir de una base de datos existente y agrega información de la conexión a base de datos a la aplicación.  
  
-   El Asistente para crear bases de datos permite crear primero un modelo conceptual y, a continuación, crear una base de datos que admita el modelo.  
  
-   El Asistente para actualizar modelos permite actualizar el modelo conceptual, el modelo de almacenamiento y las asignaciones cuando se realizan cambios en la base de datos subyacente.  
  
    > [!NOTE]
    >  Desde Visual Studio 2010, las herramientas de [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] no admiten [!INCLUDE[ss2k](../data-tools/includes/ss2k_md.md)].  
  
 Las herramientas generan o modifican un archivo .edmx que contiene información en la que se describe el modelo conceptual, el modelo de almacenamiento y las asignaciones entre ellos.  Para obtener más información, vea [.edmx File Overview](http://msdn.microsoft.com/es-es/f4c8e7ce-1db6-417e-9759-15f8b55155d4).  
  
 Hay también una herramienta de línea de comandos diseñada para ayudarle a compilar las aplicaciones que utilizan el EDM: la herramienta de EdmGen.exe.  Esta herramienta puede generar un modelo conceptual, validar un modelo existente, generar archivos de código fuente que contengan clases de objetos basadas en el modelo conceptual y generar archivos de código fuente que contengan vistas generadas por el modelo.  Para obtener información detallada sobre esta herramienta de línea de comandos, vea [Generador de EDM \(EdmGen.exe\)](../Topic/EDM%20Generator%20\(EdmGen.exe\).md).  
  
## Temas relacionados  
  
|Título|Descripción|  
|------------|-----------------|  
|[ADO.NET Entity Framework](../Topic/ADO.NET%20Entity%20Framework.md)|Se describe cómo se usan las herramientas de [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)], que [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)] proporciona para crear aplicaciones.|  
|[Entity Data Model](../Topic/Entity%20Data%20Model.md)|Se incluyen vínculos e información para trabajar con datos que usan las aplicaciones integradas en [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)].|