---
title: Implementación de un lenguaje antiguo Service1 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, managed
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2535c527fc3d2d94609246959c5293e455b9808d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "88238756"
---
# <a name="implementing-a-legacy-language-service-1"></a>Implementación de un servicio de lenguaje heredado 1
Puede utilizar las clases de Managed Package Framework (MPF) para implementar un servicio de lenguaje heredado que admita una amplia variedad de características, como el resaltado de sintaxis, la coincidencia de llaves y la finalización de IntelliSense.

 Los servicios de lenguaje heredados se implementan como parte de un VSPackage, pero la forma más reciente de implementar las características del servicio de lenguaje es usar extensiones de MEF. Para obtener más información sobre la nueva manera de implementar un servicio de lenguaje, vea [Editor y extensiones del servicio de lenguaje](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Le recomendamos que empiece a usar la nueva API del editor lo antes posible. Esto mejorará el rendimiento del servicio de lenguaje y le permitirá aprovechar las nuevas características del editor.

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
