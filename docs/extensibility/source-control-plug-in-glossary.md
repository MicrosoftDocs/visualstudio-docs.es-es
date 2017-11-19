---
title: Glosario de complemento de Control de origen | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dc45c47f47fe18bc857715acc3948561f06e718c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="source-control-plug-in-glossary"></a>Glosario de complemento de Control de código fuente
Los siguientes términos útiles y las definiciones se refieren a la documentación del SDK de complemento de Control de código fuente.  
  
## <a name="definitions"></a>Definiciones  
 Checkin  
 Cuando un usuario realiza cambios en una copia de trabajo, un usuario debe enviar los cambios desde la copia de trabajo en el repositorio de control de origen central. Esto crea una nueva revisión del archivo que está disponible para otros usuarios. Este proceso se denomina una protección.  
  
 Extracción del repositorio  
 El acto de solicitud de una copia de trabajo desde el repositorio, que informa el repositorio de la intención de modificarlo. Una copia de trabajo refleja el estado del proyecto hasta el momento en que se desprotege.  
  
 Cliente  
 Un programa que usa el sistema de control de código fuente. En esta documentación, es el IDE de Visual Studio.  
  
 Comentario  
 Un mensaje que describe los cambios que un usuario puede asociar a una revisión cuando se realiza una operación de control de código fuente.  
  
 Conflicto  
 Una situación cuando dos usuarios intentan proteger los cambios a la misma región del mismo archivo. Normalmente, se debe realizar una combinación.  
  
 Directorio  
 Una carpeta local del cliente se conoce como un directorio. Ésta es la copia en el que un usuario realiza cambios. Puede haber muchas copias de trabajo de un proyecto determinado; Generalmente, cada programador tiene su propia copia.  
  
 Obtener  
 Una operación get pone la copia de trabajo del usuario actualizada con la copia del repositorio. A diferencia de una desprotección, se realiza una operación get cuando el usuario simplemente necesita la copia más reciente, pero tiene intención de realizar ningún cambio.  
  
 Historial  
 Normalmente es un resumen de todas las desprotecciones, protecciones, actualizaciones, etiquetas y versiones que se realiza en el repositorio de control de código fuente.  
  
 IDE  
 Normalmente, se hace referencia en el entorno de desarrollo integrado de Visual Studio. Sin embargo, también podría referirse a otros entornos de cliente que reconoce la API de complementos de Control de código fuente.  
  
 Combinar  
 El proceso durante qué origen de dos o más archivos de código se combinan para formar un nuevo archivo que incorpora todas las características de los archivos anteriores. Este concepto es fundamental en el control de versiones en dos o más desarrolladores trabajan con archivos de forma simultánea.  
  
 Proyecto  
 Una carpeta de control de código fuente se conoce a menudo como un proyecto. Esto no tiene ninguna relación con los proyectos o soluciones en Visual Studio.  
  
 Complemento  
 Un archivo DLL que proporciona funcionalidad de control de código fuente mediante la implementación de la API de complementos de Control de código fuente.  
  
 Repositorio  
 La copia maestra en un origen de control sistema almacena el historial de revisión completa de un proyecto. Cada proyecto tiene exactamente un repositorio.  
  
 Revisión  
 Un cambio confirmado en el historial de un archivo o conjunto de archivos. Una revisión es una instantánea en un proyecto cambian continuamente.  
  
## <a name="see-also"></a>Vea también  
 [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)