---
title: "Introducci&#243;n a los complementos de Control de c&#243;digo fuente | Microsoft Docs"
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
  - "origen control complementos, introducción"
  - "obtener iniciado, origen control complementos"
ms.assetid: 46ac1f9f-4ecc-4a72-88d3-4c7e1647e1cb
caps.latest.revision: 21
caps.handback.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
---
# Introducci&#243;n a los complementos de Control de c&#243;digo fuente
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Para crear un complemento de control de código fuente, debe crear un archivo DLL que implementa las funciones definido en el Control de origen API del complemento, y después registrar una DLL con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para hacerlo disponible para su uso en el control de versiones de código fuente.  
  
 Tres versiones del complemento de control de código fuente API \(versiones 1,1, 1,2, y 1,3\) están disponibles para los complementos de control de código fuente.  El complemento de control de código fuente API documentadas aquí es la versión 1,3.  Se ha diseñado para ser totalmente compatible con los complementos de control de código fuente que admitían las versiones 1,1 y 1,2.  Los detalles de la sección de [Novedades de la API de complemento de origen Control versión 1.3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md) que las nuevas características admitidas en la última versión del complemento API de Control de código fuente.  
  
## En esta sección  
 [Cómo: instalar un complemento de Control de código fuente](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)  
 Describe cómo crear las entradas del Registro necesarias para conectar un control de código fuente DLL.  
  
 [Novedades de la API de complemento de origen Control versión 1.3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)  
 Proporciona información general sobre los cambios realizados en el complemento de control de código fuente API en la versión 1,3.  
  
 [Novedades de la API de complemento de origen Control versión 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)  
 Proporciona información general sobre los cambios realizados en el complemento de control de código fuente API en la versión 1,2.  
  
## Secciones relacionadas  
 [Complementos de Control de código fuente](../../extensibility/source-control-plug-ins.md)  
 Proporciona una lista completa de todos los elementos del complemento de control de código fuente API.  
  
 [Creación de un Control de origen de complemento](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Define el complemento de control de código fuente SDK y describe los recursos incluidos.