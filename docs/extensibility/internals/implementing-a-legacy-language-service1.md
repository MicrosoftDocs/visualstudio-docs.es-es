---
title: Implementación de un servicio de lenguaje heredado1 Microsoft Docs
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
ms.openlocfilehash: c3805e49ffa83f7dea2ee58ef36e1bc8e48b1eaa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707697"
---
# <a name="implementing-a-legacy-language-service"></a>Implementación de un servicio de lenguaje heredado
Puede usar clases en el marco de paquete administrado (MPF) para implementar un servicio de lenguaje heredado que admita una amplia variedad de características, como resaltado de sintaxis, coincidencia de llaves y finalización de IntelliSense.

 Los servicios de lenguaje heredados se implementan como parte de un VSPackage, pero la forma más reciente de implementar características de servicio de lenguaje es usar extensiones MEF. Para obtener más información sobre la nueva forma de implementar un servicio de lenguaje, vea [Extensiones](../../extensibility/editor-and-language-service-extensions.md)de servicio de editor y lenguaje .

> [!NOTE]
> Le recomendamos que comience a usar la nueva API del editor lo antes posible. Esto mejorará el rendimiento de su servicio de lenguaje y le permitirá aprovechar las nuevas características del editor.

## <a name="in-this-section"></a>En esta sección
- [Información general del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-overview.md)

 Una visión general de las características del servicio de lenguaje que se admiten en MPF.

- [Implementación de un servicio de lenguaje heredado](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 Describe lo que se requiere para implementar un servicio de lenguaje mediante MPF.

- [Registro de un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service1.md)

 Describe los pasos necesarios para registrar un servicio [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]de lenguaje basado en MPF con .

- [Escáner y analizador del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 Describe los dos analizadores necesarios para implementar todas las características de un servicio de lenguaje mediante el MPF.

- [Tutorial: Creación de un servicio de lenguaje heredado](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)

 Proporciona los pasos básicos necesarios para implementar un servicio de lenguaje MPF en un VSPackage.

- [Tutorial: Obtención de una lista de fragmentos de código instalados (implementación heredada)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)

 Muestra las técnicas de recuperación de una lista de fragmentos de código instalados.

- [Características del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-features1.md)

 Proporciona vínculos a temas que detallan lo que se debe hacer para implementar todas las características de un servicio de lenguaje mediante MPF.
