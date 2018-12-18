---
title: Arquitectura de complemento de Control de origen | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, architecture
ms.assetid: 35351d4c-9414-409b-98fc-f2023e2426b7
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c7ded33f6296d9ddb0b87a3d2916a95249169f82
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51805221"
---
# <a name="source-control-plug-in-architecture"></a>Arquitectura de complemento de control de código fuente
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Puede agregar compatibilidad con control de origen a la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] el entorno de desarrollo integrado (IDE) mediante la implementación y asociar un complemento de control de código fuente. El IDE se conecta con el complemento a través de la API de complemento de Control de código fuente bien definido de control de origen. El IDE expone las características de control de versiones del sistema de control de código fuente, ya que proporciona una interfaz de usuario (UI) que consta de las barras de herramientas y comandos de menú. El complemento de control de origen implementa la funcionalidad de control de código fuente.  
  
## <a name="source-control-plug-in-resources"></a>Recursos de complemento de Control de código fuente  
 El complemento de Control de código fuente se proporcionan recursos para ayudarle a crear y conectar la aplicación de control de versiones a la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE. El complemento de Control de código fuente contiene la especificación de API que debe implementarse mediante un complemento de control de código fuente para que se puede integrar en el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE. También contiene un ejemplo de código (escrito en C++) que implementa una esqueleto de código fuente complemento muestra que demuestran implementación del control de las funciones esenciales compatibles con la API de complemento de Control de origen.  
  
 La especificación de API de complemento de Control de código fuente le permite aprovechar cualquier sistema de control de código fuente de su elección, si crea un archivo DLL de control de código fuente con el conjunto de funciones implementados de acuerdo con la API de complemento de Control de código fuente necesario.  
  
## <a name="components"></a>Componentes  
 El paquete de adaptador de Control de código fuente en el diagrama es el componente del IDE que traduce la solicitud del usuario para una operación de control de código fuente en una llamada de función admitida por el complemento de control de código fuente. Para que ello, el IDE y el complemento de control de origen deben tener un eficaz cuadro de diálogo que pasa información y hacia atrás entre el IDE y el complemento. Para que este cuadro de diálogo que tenga lugar, deben hablan el mismo idioma. La API de complemento de Control de origen que se describen en esta documentación es el vocabulario común para este intercambio.  
  
 ![Diagrama de arquitectura de Control de código de origen](../../extensibility/internals/media/vs-sccsdk-plug-in-arch.gif "vs_sccsdk_plug_in_arch")  
Diagrama de arquitectura que muestra la interacción entre VS y control de código fuente complemento  
  
 Como se muestra en el diagrama de arquitectura, el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] shell, etiquetado como el shell de VS en el diagrama, hospeda los proyectos de trabajo y componentes asociados, como los editores y el Explorador de soluciones del usuario. El paquete de adaptador de Control de código fuente controla la interacción entre el IDE y el complemento de control de código fuente. El paquete de adaptador de Control de código fuente proporciona su propia interfaz de usuario de control de código fuente. Es la interfaz de usuario de nivel superior que el usuario interactúa con el fin de iniciar y definir el ámbito de una operación de control de código fuente.  
  
 El complemento de control de código fuente puede tener su propia interfaz de usuario, que puede constar de dos partes, como se muestra en la ilustración. La casilla de verificación "Interfaz de usuario del proveedor" representa los elementos de interfaz de usuario personalizada que usted, como un creador de complemento de control de código fuente, proporciona. Estos se muestran directamente mediante el complemento de control de código fuente cuando el usuario invoca una operación de control de código fuente avanzados. La casilla de verificación "Aplicación auxiliar de la interfaz de usuario" es un conjunto de código fuente control UI características del complemento que se invoca indirectamente a través del IDE. El complemento de control de origen pasa los mensajes relacionados con la interfaz de usuario para el IDE a través de funciones de devolución de llamada especial proporcionada por el IDE. La aplicación auxiliar de la interfaz de usuario facilita una integración sin problemas con el IDE (a menudo mediante el uso de un **avanzadas** botón) y, por tanto, proporciona una experiencia de usuario final más unificada.  
  
 Un complemento de control de código fuente no puede realizar cambios en el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] de shell y, por lo tanto, para el paquete de adaptador de Control de código fuente o el origen de control de interfaz de usuario proporcionada por el IDE. Deben hacer un uso máximo de la flexibilidad que ofrecen a través de la implementación de las distintas funciones de API de complemento de Control de origen que contribuyen a una experiencia integrada para el usuario final. La sección de referencia de la documentación de API de complemento de Control de código fuente incluye información para algunas funcionalidades de complemento de control de origen avanzado. Para aprovechar estas características, el complemento de control de origen debe declarar sus capacidades avanzadas para el IDE durante la inicialización, y debe implementar funciones avanzadas específicas de cada función.  
  
## <a name="see-also"></a>Vea también  
 [Complementos de Control de código fuente](../../extensibility/source-control-plug-ins.md)   
 [Glosario](../../extensibility/source-control-plug-in-glossary.md)   
 [Creación de un complemento de control de código fuente](../../extensibility/internals/creating-a-source-control-plug-in.md)

