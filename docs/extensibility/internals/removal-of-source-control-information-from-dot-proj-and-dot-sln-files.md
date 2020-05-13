---
title: Quitar información de control de código fuente de archivos .proj y .sln
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ba3085a7806bfb0556613d1fca1b94953dcdb0b2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705584"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>Eliminación de la información de control de código fuente de archivos .Proj y .Sln
En la versión 1.2 de la API del complemento de control de código fuente, la información SCC se almacena en un MSSCCPRJ. SCC. La ventaja del MSSCCPRJ. SCC es que la información de SCC no está controlada por código fuente, como en los archivos .proj y .sln.

## <a name="version-12-changes"></a>Cambios en la versión 1.2
 En los complementos de control de código fuente que se basan en la versión 1.1 de la API de complemento de Control de código fuente, la información sobre el control de código fuente se almacena en los archivos de proyecto (.proj) y solución (.sln). AuxPath especifica la ubicación de la base de datos de la información del control de código fuente y ProjName especifica la ubicación específica dentro de la base de datos. Este comportamiento puede causar problemas después de las operaciones de bifurcación, bifurcación o copia porque ProjName normalmente no sería válido después de cualquiera de estas operaciones.

 En la versión 1.1 de la API de complemento de Control de código fuente, el IDE utilizaba archivos de tipo SAK para detectar si un complemento admitía MSSCCPRJ. Método SCC de almacenamiento de información de control de código fuente. La versión 1.2 de la API del complemento de control de código fuente proporciona una nueva capacidad para detectar el soporte para MSSCCPRJ. SCC sin utilizar un archivo .SAK. Para obtener más información, consulte [Eliminación de archivos de sak](../../extensibility/internals/elimination-of-tilde-sak-files.md).

## <a name="see-also"></a>Vea también
- [Novedades de la API del complemento de control de código fuente, versión 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
