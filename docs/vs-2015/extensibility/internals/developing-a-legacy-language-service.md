---
title: Desarrollar un servicio de lenguaje heredado | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 801a349b588a1dd7612b573fcc97b4b344a69452
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51746793"
---
# <a name="developing-a-legacy-language-service"></a>Desarrollo de un servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Esta sección contiene vínculos a temas que le ayudarán a crear un servicio de lenguaje heredado.  
  
 Servicios de lenguaje heredado se implementan como parte de un paquete VSPackage, pero la forma más reciente para implementar características de servicio de lenguaje es usar las extensiones MEF. Para obtener más información acerca de la nueva forma de implementar un servicio de lenguaje, consulte [Editor y extensiones de servicio de lenguaje](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Se recomienda que comience a usar el nuevo editor de API tan pronto como sea posible. Esto mejorará el rendimiento de su servicio de lenguaje y le permiten aprovechar las nuevas características del editor.  
  
## <a name="in-this-section"></a>En esta sección  
 [Modelo de un servicio de lenguaje heredado](../../extensibility/internals/model-of-a-legacy-language-service.md)  
 Proporciona un modelo de un servicio de lenguaje mínimo para el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] editor básico. Puede usar este modelo como una guía para crear su propio servicio de lenguaje.  
  
 [Interfaces de servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-interfaces.md)  
 Describe los objetos necesarios para implementar un servicio de lenguaje y proporciona una lista de objetos adicionales que puede usar para proporcionar resaltado de sintaxis, los datos de método y otras características.  
  
 [Intercepción de comandos del servicio de lenguaje heredado](../../extensibility/internals/intercepting-legacy-language-service-commands.md)  
 Describe cómo insertar un filtro de comandos en el servicio de lenguaje para los comandos de intercepción que en caso contrario, controlaría la vista de texto.  
  
 [Registro de un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service2.md)  
 Proporciona información sobre cómo registrar su servicio de lenguaje mediante [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 [Compatibilidad del servicio de lenguaje para la depuración](../../extensibility/internals/language-service-support-for-debugging.md)  
 Describe cómo un servicio de lenguaje puede proporcionar características para admitir a un depurador.  
  
 [Lista de comprobación: creación de un servicio de lenguaje heredado](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)  
 Proporciona instrucciones paso a paso para crear e integrar un servicio de lenguaje para el editor básico.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Colores de la sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 Describe cómo implementar el resaltado de sintaxis en el servicio de lenguaje.  
  
 [Finalización de declaraciones en un servicio de lenguaje heredado](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)  
 Describe la finalización de instrucciones, el proceso por el que un servicio de lenguaje ayuda a los usuarios finalizar una palabra clave del lenguaje o un elemento que ha comenzado a escribir.  
  
 [Información de parámetros en un servicio de lenguaje heredado](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)  
 Describe cómo proporcionar sugerencias de método para los métodos y las funciones sobrecargadas.  
  
 [Provisión de compatibilidad con texto oculto en un servicio de lenguaje heredado](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)  
 Explica el propósito de una región de texto oculto y se proporcionan instrucciones sobre cómo implementar una región de texto oculto.  
  
 [Provisión de compatibilidad con esquematización ampliada en un servicio de lenguaje heredado](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)  
 Explica las dos opciones que amplían la compatibilidad con esquematización para el lenguaje más allá de admitir la *contraer a definiciones* comando.

