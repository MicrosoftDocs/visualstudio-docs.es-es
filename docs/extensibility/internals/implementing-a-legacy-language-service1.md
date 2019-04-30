---
title: Implementación de una función de lenguaje heredado1 | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, managed
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2fe405ea62562a9e7eb90948d92fcd5075887c8d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63420493"
---
# <a name="implementing-a-legacy-language-service"></a>Implementar un servicio de lenguaje heredado
Puede usar las clases de managed package framework (MPF) para implementar un servicio de lenguaje heredado que admite una amplia variedad de características, como resaltado de sintaxis, coincidencia de llaves y finalización de IntelliSense.

 Servicios de lenguaje heredado se implementan como parte de un paquete VSPackage, pero la forma más reciente para implementar características de servicio de lenguaje es usar las extensiones MEF. Para obtener más información acerca de la nueva forma de implementar un servicio de lenguaje, consulte [Editor y extensiones de servicio de lenguaje](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Se recomienda que comience a usar el nuevo editor de API tan pronto como sea posible. Esto mejorará el rendimiento de su servicio de lenguaje y le permiten aprovechar las nuevas características del editor.

## <a name="in-this-section"></a>En esta sección
- [Información general del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-overview.md)

 Información general de las características del servicio de lenguaje que se admiten en MPF.

- [Implementación de un servicio de lenguaje heredado](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 Describe lo que es necesario implementar un servicio de lenguaje mediante MPF.

- [Registro de un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service1.md)

 Describe los pasos necesarios para registrar un servicio de lenguaje basado en MPF con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

- [Escáner y analizador del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 Describe los dos analizadores que son necesarios para implementar todas las características de un servicio de lenguaje mediante MPF.

- [Tutorial: Creación de un servicio de lenguaje heredado](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)

 Proporciona los pasos básicos que son necesarios para implementar un servicio de lenguaje MPF en un VSPackage.

- [Tutorial: Obtención de una lista de los fragmentos de código instalados (implementación heredada)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)

 Muestra las técnicas de recuperación de una lista de fragmentos de código instalados.

- [Características del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-features1.md)

 Proporciona vínculos a temas que detallan lo que debe realizarse para implementar todas las características de un servicio de lenguaje mediante MPF.