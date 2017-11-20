---
title: "Eliminación de información de Control de origen de. Proj y. SLN (archivos) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 73ea933a7e9efc08347ea107b089101f1e5d5459
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>Eliminación de información de Control de origen de. Proj y. SLN (archivos)
En la versión 1.2 de la API de complemento de Control de origen de SCC información se almacena en un MSSCCPRJ. Archivo de control de código fuente. La ventaja de la MSSCCPRJ. Archivo de control de código fuente es que la información de control de código fuente no es origen - controlado, como en los archivos .sln y de proj.  
  
## <a name="version-12-changes"></a>Cambios de la versión 1.2  
 En origen control complementos que se basan en la API de complementos de Control de origen de la versión 1.1, se almacena información sobre el control de código fuente en el proyecto (proj) y archivos de solución (.sln). La ubicación de la base de datos de la información de control de origen especificada por el AuxPath, y se especifica la ubicación específica dentro de la base de datos por ProjName. Este comportamiento puede producir problemas después de la bifurcación, bifurcación o las operaciones de copia porque el Nombre_proyecto normalmente sería válido después de cualquiera de estas operaciones.  
  
 En la API de complementos de Control de código fuente versión 1.1, el IDE usa ~ archivos SAK para detectar si un complemento admite el MSSCCPRJ. Método de control de código fuente de almacenar información de control de código fuente. La API de complementos de Control de origen de la versión 1.2 proporciona una nueva capacidad para detectar la compatibilidad con MSSCCPRJ. Archivo de control de código fuente sin usar un ~ archivo SAK. Para obtener más información, consulte [eliminación de ~ SAK archivos](../../extensibility/internals/elimination-of-tilde-sak-files.md).  
  
## <a name="see-also"></a>Vea también  
 [Novedades de la API del complemento de control de código fuente, versión 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)