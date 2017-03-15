---
title: "Eliminaci&#243;n de informaci&#243;n de Control de c&#243;digo fuente desde. Proj y. SLN (archivos) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "los complementos de control de código fuente, los archivos .sln y .proj"
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Eliminaci&#243;n de informaci&#243;n de Control de c&#243;digo fuente desde. Proj y. SLN (archivos)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

En la versión 1,2 del complemento de control de código fuente API información de SCC se almacena en un archivo de MSSCCPRJ.SCC.  La ventaja del archivo de MSSCCPRJ.SCC es que la información de SCC no es origen \- controlado, tal y como está en archivos de .proj y .sln.  
  
## Cambios de versión 1,2  
 En los complementos de control de código fuente que se basan en la versión 1,1 de la API del complemento de control de código fuente, la información sobre el control de código fuente se almacena en archivos de proyecto \(.proj\) y de solución \(.sln\).  La ubicación de la base de datos de la información de control de código fuente se especifica mediante el AuxPath, y la ubicación específica de la base de datos es especificada por Nombre proyecto.  Este comportamiento puede producir problemas después de bifurcación, de bifurcación, o para operaciones de copia porque el Nombre proyecto sería normalmente válido después de cualquiera de estas operaciones.  
  
 En la versión 1,1 de la API del complemento de control de código fuente, el IDE utilizado los archivos de ~SAK para detectar si un complemento se admitía el método de MSSCCPRJ.SCC para almacenar información de control de código fuente.  La versión 1,2 de la API del complemento de control de código fuente proporciona una nueva capacidad para detectar la compatibilidad para el archivo de MSSCCPRJ.SCC sin utilizar un archivo de ~SAK.  Para obtener más información, vea [Eliminación de ~ SAK archivos](../../extensibility/internals/elimination-of-tilde-sak-files.md).  
  
## Vea también  
 [Novedades de la API de complemento de origen Control versión 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)