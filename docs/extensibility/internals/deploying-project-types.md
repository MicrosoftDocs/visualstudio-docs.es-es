---
title: "Tipos de proyecto de implementaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "proyectos [Visual Studio SDK], código administrado"
  - "agregador de proyectos [Visual Studio SDK],"
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Tipos de proyecto de implementaci&#243;n
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] instala un agregador de tipo de proyecto nuevo \(ProjectAggregator2.dll\) y también un paquete de Windows Installer para su redistribución \(ProjectAggregator2.msi\). Debe utilizar el agregador de nuevo para tipos de proyecto de código administrado. ProjectAggregator2 funciona soluciones limitaciones en el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proyecto aggregator que impiden que los tipos de proyecto de código administrado funciona correctamente. Los pasos siguientes describen cómo cambiar el VSPackage para usar el agregador de nuevo.  
  
1.  Quitar el proyecto NativeHierarchyWrapper de la solución.  
  
2.  Quitar todos los archivos binarios de NativeHierarchyWrapper de su instalación.  
  
3.  Agregar ProjectAggregator2.msi a su instalación.