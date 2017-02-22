---
title: "Glosario de complemento de Control de c&#243;digo fuente | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Glosario [Visual Studio SDK]"
  - "los complementos de control de código fuente, el glosario"
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Glosario de complemento de Control de c&#243;digo fuente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Los siguientes términos útiles y definiciones se refieren a la documentación del SDK de complemento de Control de origen.  
  
## Definiciones  
 Protección  
 Cuando un usuario realiza cambios en una copia de trabajo, un usuario debe enviar los cambios desde la copia de trabajo en el repositorio de control de origen central. Esto crea una nueva versión del archivo que está disponible para otros usuarios. Este proceso se denomina una protección.  
  
 Desprotección  
 El acto de solicitar una copia de trabajo del repositorio, que informa el repositorio de su intención de modificarlo. Una copia de trabajo refleja el estado del proyecto hasta el momento en que lo tiene desprotegido.  
  
 Cliente  
 Un programa que utiliza el sistema de control de código fuente. En esta documentación es el IDE de Visual Studio.  
  
 Comentario  
 Un mensaje que describe los cambios que un usuario puede adjuntar a una revisión cuando se realiza una operación de control de código fuente.  
  
 Conflicto  
 Una situación cuando dos usuarios intentan proteger cambios en la misma región del mismo archivo. Normalmente, se debe realizar una combinación.  
  
 Directorio  
 Una carpeta local del cliente se conoce como un directorio. Ésta es la copia en el que un usuario realiza cambios. Puede haber muchas copias de trabajo de un proyecto determinado; por lo general, cada desarrollador tiene su propia copia.  
  
 Get  
 Una operación get aporta la copia de trabajo del usuario al día con la copia del repositorio. A diferencia de una desprotección, se realiza una operación get cuando el usuario simplemente necesita la copia más reciente, pero tiene intención de realizar ningún cambio.  
  
 Historial  
 Normalmente es un resumen de todas las desprotecciones, protecciones, actualizaciones, etiquetas y versiones en el repositorio de control de código fuente.  
  
 IDE  
 Generalmente se refiere al entorno de desarrollo integrado de Visual Studio. Sin embargo, también podría referirse a otros entornos de cliente que reconoce la API de complementos de Control de código fuente.  
  
 Combinar  
 El proceso durante el origen de dos o más archivos de código se combinan para formar un nuevo archivo que incorpora todas las características de los archivos anteriores. Este concepto es fundamental en el control de versiones en dos o más desarrolladores trabajan con archivos simultáneamente.  
  
 Proyecto  
 Una carpeta de control de código fuente se conoce a menudo como un proyecto. Esto no tiene ninguna relación con los proyectos o soluciones en Visual Studio.  
  
 Complemento  
 Una DLL que proporciona funcionalidad de control de código fuente mediante la implementación de la API de complementos de Control de código fuente.  
  
 Repositorio  
 La copia maestra en un origen de sistema de control almacena el historial de revisión completa del proyecto. Cada proyecto tiene exactamente un repositorio.  
  
 Revisión  
 Un cambio confirmado en el historial de un archivo o conjunto de archivos. Una revisión es una instantánea en un proyecto que cambia continuamente.  
  
## Vea también  
 [Complementos de Control de código fuente](../extensibility/source-control-plug-ins.md)