---
title: Arquitectura de complemento de control de código fuente | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, architecture
ms.assetid: 35351d4c-9414-409b-98fc-f2023e2426b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f549ad2c4ee456860a08fbf20ccda813934a8582
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705108"
---
# <a name="source-control-plug-in-architecture"></a>Arquitectura de complemento de control de código fuente
Puede Agregar compatibilidad con el control de código fuente al [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno de desarrollo integrado (IDE) implementando y adjuntando un complemento de control de código fuente. El IDE se conecta al complemento de control de código fuente a través de la API del complemento de control de código fuente bien definida. El IDE expone las características de control de versiones del sistema de control de código fuente proporcionando una interfaz de usuario (IU) que consta de barras de herramientas y comandos de menú. El complemento de control de código fuente implementa la funcionalidad de control de código fuente.

## <a name="source-control-plug-in-resources"></a>Recursos de complemento de control de código fuente
 El complemento de control de código fuente proporciona recursos para ayudarle a crear y conectar su aplicación de control de versiones al [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. El complemento de control de código fuente contiene la especificación de API que debe ser implementada por un complemento de control de código fuente para que se pueda integrar en el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. También contiene un ejemplo de código (escrito en C++) que implementa un complemento de control de código fuente esqueleto que muestra la implementación de las funciones esenciales conforme a la API del complemento de control de código fuente.

 La especificación de la API del complemento de control de código fuente le permite aprovechar cualquier sistema de control de código fuente de su elección si crea un archivo DLL de control de código fuente con el conjunto de funciones necesario implementado de acuerdo con la API del complemento de control de código fuente.

## <a name="components"></a>Componentes
 El paquete del adaptador de control de código fuente del diagrama es el componente del IDE que traduce la solicitud del usuario para una operación de control de código fuente en una llamada de función compatible con el complemento de control de código fuente. Para que esto suceda, el IDE y el complemento de control de código fuente deben tener un cuadro de diálogo efectivo que pase información hacia atrás y hacia delante entre el IDE y el complemento. Para que se lleve a cabo este cuadro de diálogo, ambos deben hablar del mismo idioma. La API del complemento de control de código fuente que se describe en esta documentación es el vocabulario común de este intercambio.

 ![Diagrama de arquitectura de control de código fuente](../../extensibility/internals/media/vs_sccsdk_plug_in_arch.gif "vs_sccsdk_plug_in_arch") Diagrama de arquitectura que muestra la interacción entre VS y el complemento de control de código fuente

 Como se muestra en el diagrama de la arquitectura, el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Shell, etiquetado como vs Shell en el diagrama, hospeda los proyectos de trabajo del usuario y los componentes asociados, como los editores y el explorador de soluciones. El paquete del adaptador de control de código fuente controla la interacción entre el IDE y el complemento de control de código fuente. El paquete del adaptador de control de código fuente proporciona su propia interfaz de usuario de control de código fuente. Es la interfaz de usuario de nivel superior con la que el usuario interactúa para iniciar y definir el ámbito de una operación de control de código fuente.

 El complemento de control de código fuente puede tener su propia interfaz de usuario, que puede constar de dos partes, tal como se muestra en la ilustración. El cuadro con la etiqueta "interfaz de usuario del proveedor" representa los elementos de la interfaz de usuario personalizados que proporciona, como creador del complemento de control de código fuente. Los muestra directamente el complemento de control de código fuente cuando el usuario invoca una operación de control de código fuente avanzada. El cuadro con la etiqueta "interfaz de usuario auxiliar" es un conjunto de características de la interfaz de usuario del complemento de control de código fuente que se invocan indirectamente a través del IDE. El complemento de control de código fuente pasa los mensajes relacionados con la interfaz de usuario al IDE a través de funciones de devolución de llamada especiales proporcionadas por el IDE. La interfaz de usuario auxiliar facilita una integración más fluida con el IDE (a menudo mediante el uso de un botón **avanzado** ) y, por tanto, proporciona una experiencia de usuario final más unificada.

 Un complemento de control de código fuente no puede realizar cambios en el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Shell y, por consiguiente, en el paquete del adaptador de control de código fuente o en la interfaz de usuario del control de código fuente proporcionada por el IDE. Debe sacar el máximo partido de la flexibilidad que se ofrece a través de la implementación de las distintas funciones de la API del complemento de control de código fuente que contribuyen a una experiencia integrada para el usuario final. La sección de referencia de la documentación de la API del complemento de control de código fuente incluye información para algunas funcionalidades avanzadas del complemento de control de código fuente. Para aprovechar estas características, el complemento de control de código fuente debe declarar sus capacidades avanzadas para el IDE durante la inicialización y debe implementar funciones avanzadas específicas para cada funcionalidad.

## <a name="see-also"></a>Consulte también
- [Complementos de control de código fuente](../../extensibility/source-control-plug-ins.md)
- [Glosario](../../extensibility/source-control-plug-in-glossary.md)
- [Creación de un complemento de control de código fuente](../../extensibility/internals/creating-a-source-control-plug-in.md)
