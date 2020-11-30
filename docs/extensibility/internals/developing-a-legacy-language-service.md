---
title: Desarrollo de un servicio de lenguaje heredado | Microsoft Docs
description: Obtenga información sobre cómo implementar un servicio de lenguaje heredado como parte de un VSPackage o mediante extensiones de Managed Extensibility Framework (MEF).
ms.custom: SEO-VS-2020
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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f7876b590cb5b09cf5db571ba1145f6bf747e5e5
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329749"
---
# <a name="develop-a-legacy-language-service"></a>Desarrollo de un servicio de lenguaje heredado
En esta sección se proporcionan vínculos a temas que le ayudarán a crear un servicio de lenguaje heredado.

 Los servicios de lenguaje heredados se implementan como parte de un VSPackage, pero la forma más reciente de implementar las características del servicio de lenguaje es usar extensiones de MEF. Para obtener más información sobre la nueva manera de implementar un servicio de lenguaje, vea [Editor y extensiones del servicio de lenguaje](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Le recomendamos que empiece a usar la nueva API del editor lo antes posible. Esto mejorará el rendimiento del servicio de lenguaje y le permitirá aprovechar las nuevas características del editor.

## <a name="in-this-section"></a>En esta sección
- [Modelo de un servicio de lenguaje heredado](../../extensibility/internals/model-of-a-legacy-language-service.md)

 Proporciona un modelo de un servicio de lenguaje mínimo para el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Editor básico. Puede usar este modelo como guía para crear su propio servicio de lenguaje.

- [Interfaces del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-interfaces.md)

 Describe los objetos necesarios para implementar un servicio de lenguaje y proporciona una lista de objetos adicionales que se pueden usar para proporcionar resaltado de sintaxis, datos de método y otras características.

- [Interceptar comandos del servicio de lenguaje heredado](../../extensibility/internals/intercepting-legacy-language-service-commands.md)

 Describe cómo insertar un filtro de comandos en el servicio de lenguaje para interceptar comandos que, de otro modo, controlarían la vista de texto.

- [Registro de un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service2.md)

 Proporciona información sobre cómo registrar el servicio de lenguaje mediante [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Compatibilidad del servicio de lenguaje para la depuración](../../extensibility/internals/language-service-support-for-debugging.md)

 Describe cómo un servicio de lenguaje puede proporcionar características para admitir un depurador.

- [Lista de comprobación: creación de un servicio de lenguaje heredado](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)

 Proporciona instrucciones paso a paso para crear e integrar un servicio de lenguaje para el editor básico.

## <a name="related-sections"></a>Secciones relacionadas
- [Color de la sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Describe cómo implementar el resaltado de sintaxis en el servicio de lenguaje.

- [Finalización de instrucciones en un servicio de lenguaje heredado](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)

 Describe la finalización de instrucciones, el proceso por el que un servicio de lenguaje ayuda a los usuarios a finalizar una palabra clave o un elemento de lenguaje que han empezado a escribir.

- [Información de parámetros en un servicio de lenguaje heredado](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)

 Describe cómo proporcionar sugerencias de método para funciones y métodos sobrecargados.

- [Cómo: proporcionar compatibilidad de texto oculto en un servicio de lenguaje heredado](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)

 Explica el propósito de una región de texto oculto y proporciona instrucciones sobre cómo implementar una región de texto oculto.

- [Cómo: proporcionar compatibilidad de esquematización ampliada en un servicio de lenguaje heredado](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

 Explica las dos opciones que amplían la compatibilidad de la esquematización con el idioma más allá del comando *contraer a definiciones* .
