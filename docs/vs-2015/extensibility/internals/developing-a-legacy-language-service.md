---
title: Desarrollo de un servicio de lenguaje heredado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
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
caps.latest.revision: 29
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 36ff8335bfaf99b5826d217a48910bfd581321e9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842766"
---
# <a name="developing-a-legacy-language-service"></a>Desarrollo de un servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En esta sección se proporcionan vínculos a temas que le ayudarán a crear un servicio de lenguaje heredado.  
  
 Los servicios de lenguaje heredados se implementan como parte de un VSPackage, pero la forma más reciente de implementar las características del servicio de lenguaje es usar extensiones de MEF. Para obtener más información sobre la nueva manera de implementar un servicio de lenguaje, vea [Editor y extensiones del servicio de lenguaje](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
> Le recomendamos que empiece a usar la nueva API del editor lo antes posible. Esto mejorará el rendimiento del servicio de lenguaje y le permitirá aprovechar las nuevas características del editor.  
  
## <a name="in-this-section"></a>En esta sección  
 [Modelo de un servicio de lenguaje heredado](../../extensibility/internals/model-of-a-legacy-language-service.md)  
 Proporciona un modelo de un servicio de lenguaje mínimo para el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Editor básico. Puede usar este modelo como guía para crear su propio servicio de lenguaje.  
  
 [Interfaces de servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-interfaces.md)  
 Describe los objetos necesarios para implementar un servicio de lenguaje y proporciona una lista de objetos adicionales que se pueden usar para proporcionar resaltado de sintaxis, datos de método y otras características.  
  
 [Intercepción de comandos del servicio de lenguaje heredado](../../extensibility/internals/intercepting-legacy-language-service-commands.md)  
 Describe cómo insertar un filtro de comandos en el servicio de lenguaje para interceptar comandos que, de otro modo, controlarían la vista de texto.  
  
 [Registro de un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service2.md)  
 Proporciona información sobre cómo registrar el servicio de lenguaje mediante [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 [Compatibilidad del servicio de lenguaje con la depuración](../../extensibility/internals/language-service-support-for-debugging.md)  
 Describe cómo un servicio de lenguaje puede proporcionar características para admitir un depurador.  
  
 [Lista de comprobación: Creación de un servicio de lenguaje heredado](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)  
 Proporciona instrucciones paso a paso para crear e integrar un servicio de lenguaje para el editor básico.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Colores de la sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 Describe cómo implementar el resaltado de sintaxis en el servicio de lenguaje.  
  
 [Finalización de instrucciones en un servicio de lenguaje heredado](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)  
 Describe la finalización de instrucciones, el proceso por el que un servicio de lenguaje ayuda a los usuarios a finalizar una palabra clave o un elemento de lenguaje que han empezado a escribir.  
  
 [Información de parámetros en un servicio de lenguaje heredado](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)  
 Describe cómo proporcionar sugerencias de método para funciones y métodos sobrecargados.  
  
 [Provisión de compatibilidad con texto oculto en un servicio de lenguaje heredado](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)  
 Explica el propósito de una región de texto oculto y proporciona instrucciones sobre cómo implementar una región de texto oculto.  
  
 [Provisión de compatibilidad con esquematización ampliada en un servicio de lenguaje heredado](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)  
 Explica las dos opciones que amplían la compatibilidad de la esquematización con el idioma más allá del comando *contraer a definiciones* .
