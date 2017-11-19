---
title: Arquitectura de complemento de Control de origen | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control plug-ins, architecture
ms.assetid: 35351d4c-9414-409b-98fc-f2023e2426b7
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e0cde4ca360aa0059abcbe0b64d63b4a94e85d78
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="source-control-plug-in-architecture"></a>Arquitectura de complementos de Control de código fuente
Puede agregar compatibilidad de control de origen a la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el entorno de desarrollo integrado (IDE) mediante la implementación y adjuntar un complemento de control de código fuente. El IDE se conecta con el complemento a través de la API de complemento de Control de origen bien definido de control de código fuente. El IDE muestra las características de control de versión del sistema del control de código fuente proporcionando una interfaz de usuario (UI) que consta de las barras de herramientas y comandos de menú. El complemento de control de código fuente implementa la funcionalidad de control de código fuente.  
  
## <a name="source-control-plug-in-resources"></a>Recursos de complemento de Control de código fuente  
 El complemento de Control de código fuente, se proporcionan recursos para ayudar a crear y conectar la aplicación de control de versiones con el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. El complemento de Control de código fuente contiene la especificación de API que debe implementarse mediante un complemento de control de código fuente para que se puede integrar en el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. También contiene un ejemplo de código (escrito en C++) que implementa una origen esqueleto complemento que demuestra implementación del control de las funciones esenciales compatibles con la API de complementos de Control de código fuente.  
  
 La especificación de API de complemento de Control de origen le permite aprovechar cualquier sistema de control de código fuente de su elección, si crea un archivo DLL del control de código fuente con el conjunto necesario de funciones implementados de acuerdo con la API de complementos de Control de código fuente.  
  
## <a name="components"></a>Componentes  
 El paquete de adaptador de Control de origen en el diagrama es el componente del IDE que traduce la solicitud del usuario para una operación de control de código fuente en una llamada de función compatible con el complemento de control de código fuente. Para que esto ocurra, el IDE y el complemento de control de código fuente deben tener un cuadro de diálogo efectivo que pasa información y hacia atrás entre el IDE y el complemento. Para que este cuadro de diálogo que se realicen, ambos deben hablan el mismo idioma. La API de complementos de Control de código fuente que se describen en esta documentación es el vocabulario común para este intercambio.  
  
 ![Diagrama de arquitectura de Control de código de origen](../../extensibility/internals/media/vs_sccsdk_plug_in_arch.gif "vs_sccsdk_plug_in_arch")  
Diagrama de arquitectura que muestra la interacción entre VS y control de código fuente complemento  
  
 Como se muestra en el diagrama de arquitectura, el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] shell, etiquetado como shell de VS en el diagrama, hospeda proyectos de trabajo y los componentes asociados, como los editores y el Explorador de soluciones del usuario. El paquete de adaptador de Control de código fuente controla la interacción entre el IDE y el complemento de control de código fuente. El paquete de adaptador de Control de origen proporciona su propia interfaz de usuario de control de código fuente. Es la interfaz de usuario de nivel superior que el usuario interactúa con el fin de iniciar y definir el ámbito de una operación de control de código fuente.  
  
 El complemento de control de código fuente puede tener su propia interfaz de usuario, que puede constar de dos partes, como se muestra en la ilustración. La casilla de verificación "Interfaz de usuario de proveedor" representa los elementos de la interfaz de usuario personalizada proporcionada por usted, como un creador de complemento de control de código fuente. Cuando el usuario invoca una operación de control de origen avanzado, estos se muestran directamente mediante el complemento de control de código fuente. La casilla de verificación "Interfaz de usuario de aplicación auxiliar" es un conjunto de origen control IU características del complemento que se invoca indirectamente a través del IDE. El complemento de control de código fuente pasa mensajes relacionados con la interfaz de usuario para el IDE a través de funciones de devolución de llamada especial proporcionado por el IDE. La interfaz de usuario de aplicación auxiliar facilita una integración perfecta con el IDE (a menudo mediante el uso de un **avanzadas** botón) y, por tanto, proporciona una experiencia del usuario final más unificada.  
  
 Un complemento de control de código fuente no puede realizar cambios en el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de shell y, por lo tanto, para el paquete de adaptador de Control de origen o el origen de control de interfaz de usuario proporcionada por el IDE. Deben hacer un uso máximo de la flexibilidad que ofrecen a través de la implementación de las distintas funciones de API de complemento de Control de origen que contribuyen a una experiencia integrada para el usuario final. La sección de referencia de la documentación de API de complemento de Control de código fuente incluye información para algunas capacidades de complemento de control de origen avanzado. Para aprovechar estas características, el complemento de control de código fuente debe declarar sus capacidades avanzadas para el IDE durante la inicialización y deben implementar funciones avanzadas específicas de cada función.  
  
## <a name="see-also"></a>Vea también  
 [Complementos de Control de código fuente](../../extensibility/source-control-plug-ins.md)   
 [Glosario](../../extensibility/source-control-plug-in-glossary.md)   
 [Creación de un complemento de control de código fuente](../../extensibility/internals/creating-a-source-control-plug-in.md)