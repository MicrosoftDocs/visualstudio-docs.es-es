---
title: Desarrollar un servicio de lenguaje heredado | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6cf384a22429c6314bf5e2fcbb66db7974d42c87
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129857"
---
# <a name="developing-a-legacy-language-service"></a>Desarrollar un servicio de lenguaje heredado
Esta sección contiene vínculos a temas que le ayudarán a crear un servicio de lenguaje heredado.  
  
 Los servicios de lenguaje heredado se implementan como parte de un paquete VSPackage, pero la forma más reciente para implementar características del servicio de lenguaje es utilizar las extensiones MEF. Para obtener más información acerca de la nueva forma de implementar un servicio de lenguaje, consulte [Editor y extensiones de servicio de lenguaje](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Le recomendamos que empiece a usar el nuevo editor de API tan pronto como sea posible. Esto mejora el rendimiento de su servicio de lenguaje y le permiten aprovechar las nuevas características del editor.  
  
## <a name="in-this-section"></a>En esta sección  
 [Modelo de un servicio de lenguaje heredado](../../extensibility/internals/model-of-a-legacy-language-service.md)  
 Proporciona un modelo de un servicio de lenguaje mínimo para el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] editor principal. Puede usar este modelo como guía para crear su propio servicio de lenguaje.  
  
 [Interfaces de servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-interfaces.md)  
 Describe los objetos necesarios para implementar un servicio de lenguaje y proporciona una lista de objetos adicionales que puede usar para proporcionar resaltado de sintaxis, datos sobre métodos y otras características.  
  
 [Intercepción de comandos del servicio de lenguaje heredado](../../extensibility/internals/intercepting-legacy-language-service-commands.md)  
 Describe cómo insertar un filtro de comandos en el servicio de lenguaje para los comandos de intersección en caso contrario, controlaría la vista de texto.  
  
 [Registrar un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service2.md)  
 Proporciona información sobre cómo registrar el servicio de lenguaje con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Compatibilidad del servicio de lenguaje para la depuración](../../extensibility/internals/language-service-support-for-debugging.md)  
 Describe cómo un servicio de lenguaje puede incluir características para admitir a un depurador.  
  
 [Lista de comprobación: creación de un servicio de lenguaje heredado](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)  
 Proporciona instrucciones paso a paso para crear e integrar un servicio de lenguaje para el editor principal.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Colores de la sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 Describe cómo implementar el resaltado de sintaxis en el servicio de lenguaje.  
  
 [Finalización de declaraciones en un servicio de lenguaje heredado](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)  
 Describe la finalización de instrucciones, el proceso por el que un servicio de lenguaje ayuda a los usuarios finalizar una palabra clave de lenguaje o el elemento que se haya iniciado escribiendo.  
  
 [Información de parámetros en un servicio de lenguaje heredado](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)  
 Describe cómo proporcionar sugerencias de método para los métodos y las funciones sobrecargadas.  
  
 [Provisión de compatibilidad con texto oculto en un servicio de lenguaje heredado](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)  
 Explica el propósito de una región de texto oculto y se proporcionan instrucciones sobre cómo implementar un área de texto oculto.  
  
 [Provisión de compatibilidad con esquematización ampliada en un servicio de lenguaje heredado](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)  
 Explica las dos opciones para amplían la compatibilidad de esquematización para el lenguaje más allá de admitir la *contraer a definiciones* comando.