---
title: Servicios proporcionados (VSPackage de control de código fuente) | Microsoft Docs
description: Obtenga información sobre cómo los VSPackages comparten la funcionalidad a través de los servicios, incluida la interacción con el IDE de Visual Studio y sus VSPackages.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 4a97ed69d37330132196f0334f5684c0704c5fd2
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876082"
---
# <a name="services-provided-source-control-vspackage"></a>Servicios proporcionados (VSPackage de control de código fuente)
Los servicios son el mecanismo principal a través del cual se comparte la funcionalidad entre los VSPackages y entre el entorno de desarrollo integrado (IDE) de Visual Studio y sus VSPackages instalados. Para obtener una descripción detallada de los servicios y su importancia en el IDE de Visual Studio, vea[usar y proporcionar servicios](../../extensibility/using-and-providing-services.md).

## <a name="the-source-control-service"></a>Servicio de control de código fuente
 Visual Studio proporciona dos niveles de servicios, servicios de nivel de IDE y servicios de nivel de paquete. El IDE de Visual Studio proporciona de forma nativa los servicios de nivel de IDE. El paquete de control de código fuente consume algunos de estos servicios. El paquete de control de código fuente como VSPackage comparte su funcionalidad de control de código fuente proporcionando un servicio de control de código fuente privado propio. El paquete de control de código fuente encapsula el conjunto de interfaces relacionadas con el control de código fuente implementadas por este en forma de un contrato que se puede usar en el IDE de Visual Studio.

## <a name="see-also"></a>Consulte también
- [Elementos de diseño](../../extensibility/internals/source-control-vspackage-design-elements.md)
