---
title: "Arquitectura de complemento de Control de c&#243;digo fuente | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "control de código fuente plug-ins, arquitectura"
ms.assetid: 35351d4c-9414-409b-98fc-f2023e2426b7
caps.latest.revision: 24
caps.handback.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
---
# Arquitectura de complemento de Control de c&#243;digo fuente
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Puede agregar compatibilidad de control de código fuente al entorno de desarrollo integrado de \(IDE\) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] implementando y asociar un complemento de control de código fuente.  El IDE conecta con el complemento de control de código fuente mediante el complemento de control de código fuente bien definido API.  El IDE expone las características de control de versiones del sistema de control de código fuente que proporciona una \(UI\) interfaz de usuario formado por las barras de herramientas y los comandos de menú.  El complemento de control de código fuente implementa la funcionalidad de control de código fuente.  
  
## Recursos del complemento de control de código fuente  
 El complemento de control de código fuente proporciona recursos para ayudar a crear y a conectar la aplicación de la versión a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el IDE.  El complemento de control de código fuente contiene la especificación de API que deben implementar por un complemento de control de código fuente de modo que pueda integrar en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el IDE.  También contiene un ejemplo de código \(escrito en C\+\+\) que implementa una implementación de demostración de complemento básica del control de origen de las funciones esenciales compatible con la API del complemento Control de código fuente.  
  
 La especificación de la API del complemento de control de código fuente le permite aprovechar cualquier sistema de control de código fuente de la opción si crea un control de código fuente DLL con el conjunto necesario de funciones implementadas de acuerdo con el complemento de control de código fuente API.  
  
## Componentes  
 El paquete de adaptador de Control de código fuente en el diagrama es el componente del IDE que traduce el orden de usuario una operación de control de código fuente a una llamada de función admitida por el complemento de control de código fuente.  Para que esto suceda, el IDE y el complemento de control de código fuente deben tener un diálogo eficaz que pase información de uno a otro entre el IDE y el complemento.  Para que este diálogo tenga lugar, ambos deben comunicarse el mismo lenguaje.  El complemento de control de código fuente API antes de esta documentación es el vocabulario común para este intercambio.  
  
 ![Diagrama de arquitectura de control de código fuente](../../extensibility/internals/media/vs_sccsdk_plug_in_arch.png "vs\_sccsdk\_plug\_in\_arch")  
Diagrama de arquitectura que muestra la interacción entre VS y el complemento de control de código fuente  
  
 Como se muestra en el diagrama de la arquitectura, del shell de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , etiquetados como VS el shell en el diagrama, hospeda proyectos de ejecución del usuario y los componentes asociados, como los editores y el explorador de soluciones.  El paquete de adaptador de control de código fuente controla la comunicación entre el IDE y el complemento de control de código fuente.  El paquete de adaptador de control de código fuente proporciona su propia interfaz de usuario del control de código fuente.  Es la interfaz de usuario de nivel superior que el usuario interactúa con para iniciar y definir el ámbito de una operación de control de código fuente.  
  
 El complemento de control de código fuente puede tener su propia interfaz de usuario, que pueden estar compuestos de dos partes como se muestra en la ilustración.  El cuadro con la etiqueta “interfaz de usuario del proveedor” representa los elementos personalizados de interfaz de usuario que, como generador de complemento de control de código fuente, proporciona.  Éstos son mostrar directamente por el complemento de control de código fuente cuando el usuario invoca una operación de control de código fuente avanzado.  El cuadro con la etiqueta “interfaz de usuario de la aplicación auxiliar” es un conjunto de características del complemento de la interfaz de usuario del control de código fuente que se invocan al IDE.  El complemento de control de código fuente pasa mensajes con la Interfaz de usuario al IDE con funciones de devolución de llamada especiales proporcionadas por el IDE.  La interfaz de usuario de la aplicación auxiliar facilita una más integración sin problemas con el IDE \(con el uso de un botón de **AVANZADAS** \) y proporciona así una experiencia unificada del usuario final.  
  
 Un complemento de control de origen no puede realizar cambios en el shell de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y, por consiguiente, el paquete de adaptador de Control de código fuente o a la interfaz de usuario del control de código fuente proporcionada por el IDE.  Debe crear el uso máximo de la flexibilidad proporcionada con la implementación de las diversas funciones API del complemento de control de código fuente que contribuyen a una experiencia integrada para el usuario final.  La sección de referencia de la documentación de la API del complemento de control de código fuente incluye información por algunas características avanzadas del complemento de control de código fuente.  Para aprovechar estas características, el complemento de control de origen debe declarar las características avanzadas al IDE durante la inicialización, y debe implementar funciones avanzadas específicas de cada función.  
  
## Vea también  
 [Complementos de Control de código fuente](../../extensibility/source-control-plug-ins.md)   
 [Glosario](../../extensibility/source-control-plug-in-glossary.md)   
 [Creación de un Control de origen de complemento](../../extensibility/internals/creating-a-source-control-plug-in.md)