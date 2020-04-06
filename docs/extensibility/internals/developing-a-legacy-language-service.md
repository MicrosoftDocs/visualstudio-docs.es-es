---
title: Desarrollo de un servicio de lenguaje heredado (Legacy Language Service) Microsoft Docs
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
ms.openlocfilehash: 0c7f930d5087b6a822156fd44024def0d5b42b49
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708669"
---
# <a name="develop-a-legacy-language-service"></a>Desarrollar un servicio de lenguaje heredado
En esta sección se vinculan a temas que le ayudan a crear un servicio de lenguaje heredado.

 Los servicios de lenguaje heredados se implementan como parte de un VSPackage, pero la forma más reciente de implementar características de servicio de lenguaje es usar extensiones MEF. Para obtener más información sobre la nueva forma de implementar un servicio de lenguaje, consulte [Editor y extensiones](../../extensibility/editor-and-language-service-extensions.md)de servicio de lenguaje .

> [!NOTE]
> Le recomendamos que comience a usar la nueva API del editor lo antes posible. Esto mejorará el rendimiento de su servicio de lenguaje y le permitirá aprovechar las nuevas características del editor.

## <a name="in-this-section"></a>En esta sección
- [Modelo de un servicio de lenguaje heredado](../../extensibility/internals/model-of-a-legacy-language-service.md)

 Proporciona un modelo de un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] servicio de lenguaje mínimo para el editor principal. Puede utilizar este modelo como guía para crear su propio servicio de lenguaje.

- [Interfaces de servicio de lenguaje heredadas](../../extensibility/internals/legacy-language-service-interfaces.md)

 Describe los objetos necesarios para implementar un servicio de lenguaje y proporciona una lista de objetos adicionales que puede usar para proporcionar resaltado de sintaxis, datos de método y otras características.

- [Interceptar comandos de servicio de lenguaje heredado](../../extensibility/internals/intercepting-legacy-language-service-commands.md)

 Describe cómo insertar un filtro de comandos en el servicio de lenguaje para interceptar comandos que la vista de texto controlaría de otro modo.

- [Registrar un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service2.md)

 Proporciona información sobre cómo registrar el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]servicio de lenguaje mediante .

- [Compatibilidad con el servicio de lenguaje para la depuración](../../extensibility/internals/language-service-support-for-debugging.md)

 Describe cómo un servicio de lenguaje puede proporcionar características para admitir un depurador.

- [Lista de verificación: Crear un servicio de lenguaje heredado](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)

 Proporciona instrucciones paso a paso para crear e integrar un servicio de lenguaje para el editor principal.

## <a name="related-sections"></a>Secciones relacionadas
- [Coloreación de sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Describe cómo implementar el resaltado de sintaxis en el servicio de lenguaje.

- [Finalización de instrucciones en un servicio de lenguaje heredado](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)

 Describe la finalización de instrucciones, el proceso mediante el cual un servicio de lenguaje ayuda a los usuarios a finalizar una palabra clave de idioma o elemento que han comenzado a escribir.

- [Información de parámetros en un servicio de lenguaje heredado](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)

 Describe cómo proporcionar sugerencias de método para funciones y métodos sobrecargados.

- [Cómo: Proporcionar soporte de texto oculto en un servicio de lenguaje heredado](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)

 Explica el propósito de una región de texto oculto y proporciona instrucciones sobre cómo implementar una región de texto oculta.

- [Cómo: Proporcionar soporte de esquematización ampliada en un servicio de lenguaje heredado](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

 Explica las dos opciones que amplían la compatibilidad de esquematización para el lenguaje más allá de admitir el comando *Contraer a definiciones.*
