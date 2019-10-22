---
title: Desarrollar un servicio de lenguaje heredado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.vsip.LangServWiz.langtoks
- vs.vsip.LangServWiz.welcome
- vs.vsip.LangServWiz.langSpec
- vs.vsip.LangServWiz.langInfo
- vs.vsip.LangServWiz.langServOpts
helpviewer_keywords:
- language services, developing
ms.assetid: 6151ba88-c1c3-41de-a1cc-668f494d48d1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6aa21b2f2e8b0321e829fd27fde1d833a63e7ecb
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351574"
---
# <a name="develop-a-legacy-language-service"></a>Desarrollar un servicio de lenguaje heredado
Esta sección contiene vínculos a temas que le ayudarán a crear un servicio de lenguaje heredado.

 Servicios de lenguaje heredado se implementan como parte de un paquete VSPackage, pero la forma más reciente para implementar características de servicio de lenguaje es usar las extensiones MEF. Para obtener más información acerca de la nueva forma de implementar un servicio de lenguaje, consulte [Editor y lenguaje de extensiones de servicio](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Se recomienda que comience a usar el nuevo editor de API tan pronto como sea posible. Esto mejorará el rendimiento de su servicio de lenguaje y le permiten aprovechar las nuevas características del editor.

## <a name="in-this-section"></a>En esta sección
- [Modelo de un servicio de lenguaje heredado](../../extensibility/internals/model-of-a-legacy-language-service.md)

 Proporciona un modelo de un servicio de lenguaje mínimo para el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] editor básico. Puede usar este modelo como una guía para crear su propio servicio de lenguaje.

- [Interfaces de servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-interfaces.md)

 Describe los objetos necesarios para implementar un servicio de lenguaje y proporciona una lista de objetos adicionales que puede usar para proporcionar resaltado de sintaxis, los datos de método y otras características.

- [Interceptar los comandos del servicio de lenguaje heredado](../../extensibility/internals/intercepting-legacy-language-service-commands.md)

 Describe cómo insertar un filtro de comandos en el servicio de lenguaje para los comandos de intercepción que en caso contrario, controlaría la vista de texto.

- [Registrar un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service2.md)

 Proporciona información sobre cómo registrar su servicio de lenguaje mediante [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

- [Soporte técnico de servicio de lenguaje para la depuración](../../extensibility/internals/language-service-support-for-debugging.md)

 Describe cómo un servicio de lenguaje puede proporcionar características para admitir a un depurador.

- [Lista de comprobación: Crear un servicio de lenguaje heredado](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)

 Proporciona instrucciones paso a paso para crear e integrar un servicio de lenguaje para el editor básico.

## <a name="related-sections"></a>Secciones relacionadas
- [Colores de sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Describe cómo implementar el resaltado de sintaxis en el servicio de lenguaje.

- [Finalización de instrucciones en un servicio de lenguaje heredado](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)

 Describe la finalización de instrucciones, el proceso por el que un servicio de lenguaje ayuda a los usuarios finalizar una palabra clave del lenguaje o un elemento que ha comenzado a escribir.

- [Información de parámetros en un servicio de lenguaje heredado](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)

 Describe cómo proporcionar sugerencias de método para los métodos y las funciones sobrecargadas.

- [Cómo: Proporcionar compatibilidad con texto oculto en un servicio de lenguaje heredado](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)

 Explica el propósito de una región de texto oculto y se proporcionan instrucciones sobre cómo implementar una región de texto oculto.

- [Cómo: Proporcionar compatibilidad con esquematización ampliada en un servicio de lenguaje heredado](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

 Explica las dos opciones que amplían la compatibilidad con esquematización para el lenguaje más allá de admitir la *contraer a definiciones* comando.