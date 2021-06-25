---
title: Implementación de un servicio de lenguaje heredado1 | Microsoft Docs
description: Obtenga información sobre cómo implementar un servicio de lenguaje heredado que admita características extendidas del servicio de lenguaje mediante el marco de paquetes administrados (MPF). Parte 1 de 2.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- language services, managed
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 34be4e54fbce413fe5ba916892216a9234d4ba93
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901154"
---
# <a name="implementing-a-legacy-language-service-1"></a>Implementación de un servicio de lenguaje heredado 1
Puede usar clases en el marco de paquetes administrados (MPF) para implementar un servicio de lenguaje heredado que admita una amplia variedad de características, como el resaltado de sintaxis, la coincidencia de llaves y la finalización de IntelliSense.

 Los servicios de lenguaje heredados se implementan como parte de un VSPackage, pero la manera más reciente de implementar características del servicio de lenguaje es usar extensiones MEF. Para obtener más información sobre la nueva manera de implementar un servicio de lenguaje, vea [Editor and Language Service Extensions](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Se recomienda empezar a usar la nueva API del editor lo antes posible. Esto mejorará el rendimiento del servicio de lenguaje y le permitirá aprovechar las nuevas características del editor.

## <a name="in-this-section"></a>En esta sección
- [Información general del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-overview.md)

 Información general de las características del servicio de lenguaje que se admiten en MPF.

- [Implementación de un servicio de lenguaje heredado](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 Describe lo que se necesita para implementar un servicio de lenguaje mediante MPF.

- [Registro de un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service1.md)

 Describe los pasos necesarios para registrar un servicio de lenguaje basado en MPF con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Escáner y analizador del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 Describe los dos analizadores necesarios para implementar todas las características de un servicio de lenguaje mediante MPF.

- [Tutorial: Creación de un servicio de lenguaje heredado](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)

 Proporciona los pasos básicos necesarios para implementar un servicio de lenguaje MPF en un VSPackage.

- [Tutorial: Obtención de una lista de los fragmentos de código instalados (implementación heredada)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)

 Muestra las técnicas de recuperación de una lista de fragmentos de código instalados.

- [Características del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-features1.md)

 Proporciona vínculos a temas que detallan lo que se debe hacer para implementar todas las características de un servicio de lenguaje mediante MPF.
