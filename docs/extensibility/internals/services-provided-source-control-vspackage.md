---
title: Servicios proporcionados (Control de código fuente VSPackage) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f08ebe49756b442ef474ac2a032a72894f6bec15
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705407"
---
# <a name="services-provided-source-control-vspackage"></a>Servicios proporcionados (VSPackage de control de código fuente)
Los servicios son el mecanismo principal a través del cual la funcionalidad se comparte entre VSPackages y entre el entorno de desarrollo integrado (IDE) de Visual Studio y sus VSPackages instalados. Para obtener una descripción detallada de los servicios y su importancia en el IDE de Visual Studio, vea[Uso y suministro](../../extensibility/using-and-providing-services.md)de servicios .

## <a name="the-source-control-service"></a>El Servicio de Control de Código s(Source Control Service)
 Visual Studio proporciona dos capas de servicios, servicios de nivel IDE y servicios de nivel de paquete. El IDE de Visual Studio proporciona de forma nativa servicios de nivel IDE. El paquete de control de código fuente consume algunos de estos servicios. El paquete de control de código fuente como un VSPackage comparte su funcionalidad de control de código fuente proporcionando un servicio de control de código fuente privado propio. El paquete de control de código fuente encapsula el conjunto de interfaces relacionadas con el control de código fuente implementadas por él en forma de un contrato que puede usar el IDE de Visual Studio.

## <a name="see-also"></a>Vea también
- [Elementos de diseño](../../extensibility/internals/source-control-vspackage-design-elements.md)
