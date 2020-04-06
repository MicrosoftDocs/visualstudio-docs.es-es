---
title: Arquitectura de complementos de Control de código fuente (Source Control Plug-in Architecture) Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705108"
---
# <a name="source-control-plug-in-architecture"></a>Arquitectura de complemento de control de código fuente
Puede agregar compatibilidad con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el control de código fuente al entorno de desarrollo integrado (IDE) implementando y adjuntando un complemento de control de código fuente. El IDE se conecta al complemento de control de código fuente a través de la API de complemento de Control de código fuente bien definida. El IDE expone las características de control de versiones del sistema de control de código fuente proporcionando una interfaz de usuario (UI) que consta de barras de herramientas y comandos de menú. El complemento de control de código fuente implementa la funcionalidad de control de código fuente.

## <a name="source-control-plug-in-resources"></a>Recursos de complementodes de Control de código fuente
 El complemento Control de código fuente proporciona recursos para ayudar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a crear y conectar la aplicación de control de versiones al IDE. El complemento de Control de código fuente contiene la especificación de API que debe implementar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] un complemento de control de código fuente para que se pueda integrar en el IDE. También contiene un ejemplo de código (escrito en C++) que implementa un complemento de control de código fuente de esqueleto que demuestra la implementación de funciones esenciales compatibles con la API de complemento de Control de código fuente.

 La especificación de API de complemento de Control de código fuente le permite aprovechar cualquier sistema de control de código fuente de su elección si crea un archivo DLL de control de código fuente con el conjunto necesario de funciones implementadas de acuerdo con la API de complemento de Control de código fuente.

## <a name="components"></a>Componentes
 El paquete de adaptador de control de código fuente en el diagrama es el componente del IDE que traduce la solicitud del usuario para una operación de control de código fuente en una llamada de función admitida por el complemento de control de código fuente. Para que esto suceda, el IDE y el complemento de control de código fuente deben tener un cuadro de diálogo eficaz que pase información entre el IDE y el complemento. Para que este diálogo tenga lugar, ambos deben hablar el mismo idioma. La API de complemento de Control de código fuente que se describe en esta documentación es el vocabulario común para este intercambio.

 ![Diagrama](../../extensibility/internals/media/vs_sccsdk_plug_in_arch.gif "vs_sccsdk_plug_in_arch") de arquitectura de control de código fuente Diagrama de arquitectura que muestra la interacción entre VS y el complemento de control de código fuente

 Como se muestra en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el diagrama de arquitectura, el shell, etiquetado como shell VS en el diagrama, hospeda los proyectos de trabajo del usuario y los componentes asociados, como los editores y el Explorador de soluciones. El paquete de adaptador de control de código fuente controla la interacción entre el IDE y el complemento de control de código fuente. El paquete de adaptador de control de código fuente proporciona su propia interfaz de usuario de control de código fuente. Es la interfaz de usuario de nivel superior con la que interactúa el usuario para iniciar y definir el ámbito de una operación de control de código fuente.

 El complemento de control de código fuente puede tener su propia interfaz de usuario, que puede constar de dos partes como se muestra en la figura. El cuadro etiquetado "User UI" representa los elementos de interfaz de usuario personalizados que usted, como creador de complementos de control de código fuente, proporciona. Estos se muestran directamente por el complemento de control de código fuente cuando el usuario invoca una operación de control de código fuente avanzada. El cuadro etiquetado "Helper UI" es un conjunto de características de interfaz de usuario de complemento de control de código fuente que se invocan indirectamente a través del IDE. El complemento de control de código fuente pasa mensajes relacionados con la interfaz de usuario al IDE a través de funciones de devolución de llamada especiales proporcionadas por el IDE. La interfaz de usuario auxiliar facilita una integración más fluida con el IDE (a menudo mediante el uso de un botón **avanzado)** y, por lo tanto, proporciona una experiencia de usuario final más unificada.

 Un complemento de control de código [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fuente no puede realizar cambios en el shell y, en consecuencia, en el paquete de adaptador de control de código fuente o en la interfaz de usuario de control de código fuente proporcionada por el IDE. Debe aprovechar al máximo la flexibilidad ofrecida a través de la implementación de las diversas funciones de API de complemento de Control de código fuente que contribuyen a una experiencia integrada para el usuario final. La sección de referencia de la documentación de la API de complemento de Control de código fuente incluye información sobre algunas capacidades avanzadas del complemento de control de código fuente. Para aprovechar estas características, el complemento de control de código fuente debe declarar sus capacidades avanzadas al IDE durante la inicialización y debe implementar funciones avanzadas específicas para cada capacidad.

## <a name="see-also"></a>Vea también
- [Complementos de control de código fuente](../../extensibility/source-control-plug-ins.md)
- [Glosario](../../extensibility/source-control-plug-in-glossary.md)
- [Creación de un complemento de control de código fuente](../../extensibility/internals/creating-a-source-control-plug-in.md)
