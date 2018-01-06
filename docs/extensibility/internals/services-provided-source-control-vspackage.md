---
title: "Servicios proporcionados (VSPackage de Control de código fuente) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 6951881e915b44c0cb0c85685280f2b770647f3a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="services-provided-source-control-vspackage"></a>Servicios proporcionados (VSPackage de Control de código fuente)
Los servicios son el mecanismo principal a través del cual la funcionalidad se comparte entre los VSPackages y entre el entorno de desarrollo integrado (IDE) de Visual Studio y su VSPackages instalado. Para una descripción detallada de los servicios y su importancia en el IDE de Visual Studio, consulte[Using y proporcionar servicios](../../extensibility/using-and-providing-services.md).  
  
## <a name="the-source-control-service"></a>El servicio de Control de código fuente  
 Visual Studio proporciona dos niveles de servicios, servicios de nivel de IDE y servicios de nivel de paquete. El IDE de Visual Studio proporcionan servicios de nivel superior IDE de forma nativa. El paquete de control de código fuente utiliza alguno de estos servicios. El paquete de control de código fuente como un paquete VSPackage comparte su funcionalidad de control de código fuente al proporcionar un servicio de control de origen privado de su propio. El paquete de control de código fuente encapsula el conjunto de interfaces relacionadas con el control de código fuente implementados por el objeto en forma de un contrato que puede usarse en el IDE de Visual Studio.  
  
## <a name="see-also"></a>Vea también  
 [Elementos de diseño](../../extensibility/internals/source-control-vspackage-design-elements.md)