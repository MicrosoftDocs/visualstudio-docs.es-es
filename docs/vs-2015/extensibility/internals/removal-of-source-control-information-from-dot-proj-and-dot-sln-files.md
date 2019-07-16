---
title: Eliminación de información de Control de código fuente. Proj y. Los archivos sln | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b7cdaeb02f77d3775096f840a513f68e531b1299
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68199372"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>Eliminación de la información de control de código fuente de archivos .Proj y .Sln
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En la versión 1.2 de la API de complemento de Control de código fuente SCC información se almacena en un MSSCCPRJ. Archivo de control de código fuente. La ventaja de la MSSCCPRJ. Archivo de SCC es que la información de control de código fuente no es origen - controlado, como sucede en archivos .proj y .sln.  
  
## <a name="version-12-changes"></a>Cambios de la versión 1.2  
 En fuente control los complementos que se basan en la API de complemento de Control de origen de la versión 1.1, información sobre el control de código fuente se almacena en el proyecto (.proj) y archivos de solución (.sln). La ubicación de la base de datos de la información de control de origen especificada por el AuxPath, y se especifica la ubicación específica dentro de la base de datos por ProjName. Este comportamiento puede provocar problemas después de la bifurcación, bifurcación o las operaciones de copia porque la Nombre_proyecto normalmente sería válido después de cualquiera de estas operaciones.  
  
 En la API de complemento de Control de código fuente versión 1.1, el IDE usa ~ archivos SAK para detectar si un complemento admite el MSSCCPRJ. Método de control de código fuente de almacenar información de control de código fuente. La API de complemento de Control de origen de la versión 1.2 proporciona una nueva capacidad para detectar la compatibilidad con MSSCCPRJ. Archivo de control de código fuente sin usar un ~ archivo SAK. Para obtener más información, consulte [eliminación de ~ SAK archivos](../../extensibility/internals/elimination-of-tilde-sak-files.md).  
  
## <a name="see-also"></a>Vea también  
 [Novedades de la API del complemento de control de código fuente, versión 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
