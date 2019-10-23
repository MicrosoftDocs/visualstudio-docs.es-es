---
title: Quitar la información de control de código fuente de los archivos. proj y. sln
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 68e50932a83e3db6d405119d3721d021144cbaeb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724278"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>Eliminación de la información de control de código fuente de archivos .Proj y .Sln
En la versión 1,2 de la API del complemento de control de código fuente, la información de SCC se almacena en MSSCCPRJ. Archivo SCC. La ventaja de MSSCCPRJ. El archivo SCC es que la información de SCC no está controlada por código fuente, como se encuentra en los archivos. proj y. sln.

## <a name="version-12-changes"></a>Cambios en la versión 1,2
 En los complementos de control de código fuente que se basan en la API del complemento de control de código fuente versión 1,1, la información sobre el control de código fuente se almacena en los archivos de proyecto (. proj) y de solución (. sln). La ubicación de la base de datos de la información de control de código fuente se especifica mediante AuxPath, y la ubicación específica dentro de la base de datos se especifica mediante Nombre_proyecto. Este comportamiento puede producir problemas después de las operaciones de bifurcación, bifurcación o copia porque Nombre_proyecto normalmente no sería válido después de alguna de estas operaciones.

 En la API del complemento de control de código fuente versión 1,1, el IDE usaba archivos ~ SAK para detectar si un complemento admitía la MSSCCPRJ. Método SCC para almacenar información de control de código fuente. La API del complemento de control de código fuente versión 1,2 proporciona una nueva capacidad para detectar la compatibilidad con MSSCCPRJ. Archivo SCC sin usar un archivo ~ SAK. Para obtener más información, vea [eliminación de archivos ~ Sak](../../extensibility/internals/elimination-of-tilde-sak-files.md).

## <a name="see-also"></a>Vea también
- [Novedades de la API del complemento de control de código fuente, versión 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)