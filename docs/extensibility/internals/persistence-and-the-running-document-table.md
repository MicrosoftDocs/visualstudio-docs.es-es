---
title: "Persistencia y la tabla Document de ejecuci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "persistencia, administrar"
  - "IVsPersistHierarchyItem (interfaz), implementar"
  - "arquitectura de persistencia"
  - "tabla document ejecución (RDT), arquitectura"
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Persistencia y la tabla Document de ejecuci&#243;n
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

En el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE, los proyectos son totalmente responsables de administrar la persistencia de sus elementos de proyecto, que cumplen con el servicio, <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. Documentos son la unidad básica de persistencia en el entorno de Visual Studio. Proyectos de coordinan la apertura, guardar y cambiar el nombre de los documentos en la tabla de documento ejecución \(RDT\), un recurso que realiza un seguimiento del estado de todos los documentos abiertos.  
  
## Administración de persistencia  
 Proyectos de control de servicio de persistencia del entorno mediante la implementación de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> interfaz. Mientras el entorno nunca directamente solicita un documento para continuar, solicita el proyecto propietario \(o jerarquía\) para guardar el documento. Esto hace posible para el proyecto guardar sus datos de elemento de proyecto en archivos locales, archivos remotos, una base de datos, un repositorio o cualquier otro medio.  
  
 El entorno global mantiene el RDT. El entorno mantiene las entradas de todas las ventanas abiertas y documentos en el RDT, que hace posible para que puedan reciben notificaciones especiales, como cuando se cierra una solución. Además, el RDT hace posible para el entorno realizar el seguimiento de sus nodos correspondientes en **el Explorador de soluciones**. El RDT mantiene un registro por cada objeto abierto y con persistencia, incluidos los archivos de proyecto y documentos de elemento de proyecto.  
  
## Vea también  
 [Tabla de documentos de ejecución](../../extensibility/internals/running-document-table.md)   
 [Selección y moneda en el IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)