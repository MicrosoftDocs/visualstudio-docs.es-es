---
title: Servicios proporcionados (VSPackage de control de código fuente) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 13be907eeb35a2d4382fb63726c09cb2924e57e7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723859"
---
# <a name="services-provided-source-control-vspackage"></a>Servicios proporcionados (VSPackage de control de código fuente)
Los servicios son el mecanismo principal a través del cual se comparte la funcionalidad entre los VSPackages y entre el entorno de desarrollo integrado (IDE) de Visual Studio y sus VSPackages instalados. Para obtener una descripción detallada de los servicios y su importancia en el IDE de Visual Studio, vea[usar y proporcionar servicios](../../extensibility/using-and-providing-services.md).

## <a name="the-source-control-service"></a>Servicio de control de código fuente
 Visual Studio proporciona dos niveles de servicios, servicios de nivel de IDE y servicios de nivel de paquete. El IDE de Visual Studio proporciona de forma nativa los servicios de nivel de IDE. El paquete de control de código fuente consume algunos de estos servicios. El paquete de control de código fuente como VSPackage comparte su funcionalidad de control de código fuente proporcionando un servicio de control de código fuente privado propio. El paquete de control de código fuente encapsula el conjunto de interfaces relacionadas con el control de código fuente implementadas por este en forma de un contrato que se puede usar en el IDE de Visual Studio.

## <a name="see-also"></a>Vea también
- [Elementos de diseño](../../extensibility/internals/source-control-vspackage-design-elements.md)