---
title: Implementar un Service1 de lenguaje heredado | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, managed
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0486b8ad035d64f542d48f1e304413780958d90c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="implementing-a-legacy-language-service"></a>Implementar un servicio de lenguaje heredado
Puede utilizar las clases de managed package framework (MPF) para implementar un servicio de lenguaje heredado que admite una amplia variedad de características, como la finalización de IntelliSense, coincidencia de llaves y resaltado de sintaxis.  
  
 Los servicios de lenguaje heredado se implementan como parte de un paquete VSPackage, pero la forma más reciente para implementar características del servicio de lenguaje es utilizar las extensiones MEF. Para obtener más información acerca de la nueva forma de implementar un servicio de lenguaje, consulte [Editor y extensiones de servicio de lenguaje](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Le recomendamos que empiece a usar el nuevo editor de API tan pronto como sea posible. Esto mejora el rendimiento de su servicio de lenguaje y le permiten aprovechar las nuevas características del editor.  
  
## <a name="in-this-section"></a>En esta sección  
 [Información general del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-overview.md)  
 Información general sobre las características del servicio de lenguaje que se admiten en MPF.  
  
 [Implementar un servicio de lenguaje heredado](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 Describe lo que se requiere para implementar un servicio de lenguaje mediante MPF.  
  
 [Registrar un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 Describe los pasos necesarios para registrar un servicio de lenguaje basado en MPF con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Escáner y analizador del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 Describe los analizadores de dos que se necesitan para implementar todas las características de un servicio de lenguaje mediante MPF.  
  
 [Tutorial: creación de un servicio de lenguaje heredado](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)  
 Proporciona los pasos básicos necesarios para implementar un servicio de lenguaje MPF en un paquete VSPackage.  
  
 [Tutorial: obtención de una lista de fragmentos de código instalados (implementación heredada)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)  
 Muestra las técnicas de recuperación de una lista de fragmentos de código instalados.  
  
 [Características del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-features1.md)  
 Proporciona vínculos a temas que lo que debe hacer para implementar todas las características de un servicio de lenguaje mediante MPF de detalles.