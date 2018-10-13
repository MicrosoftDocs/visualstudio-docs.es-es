---
title: Glosario del complemento de Control de origen | Documentos de Microsoft
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
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fabf99b4402fe8c8a2792b90f966e3ddaee4aeeb
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49282170"
---
# <a name="source-control-plug-in-glossary"></a>Glosario del complemento de control de código fuente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los siguientes términos útiles y definiciones se refieren a la documentación del SDK de complemento de Control de origen.  
  
## <a name="definitions"></a>Definiciones  
 Checkin  
 Cuando un usuario realiza cambios en una copia de trabajo, un usuario debe enviar los cambios desde la copia de trabajo en el repositorio de control de origen central. Esto crea una nueva revisión del archivo que está disponible para otros usuarios. Este proceso se denomina una protección.  
  
 Desprotección  
 El acto de solicitar una copia de trabajo desde el repositorio, que informa el repositorio de su intención para modificarlo. Una copia de trabajo refleja el estado del proyecto hasta el momento en que lo tiene desprotegido.  
  
 Cliente  
 Un programa que usa el sistema de control de código fuente. En esta documentación, es el IDE de Visual Studio.  
  
 Comentario  
 Un mensaje que describe los cambios que un usuario puede asociar a una revisión cuando se realiza una operación de control de código fuente.  
  
 Conflicto  
 Una situación cuando dos usuarios intentan proteger cambios en la misma región del mismo archivo. Normalmente, se debe realizar una fusión mediante combinación.  
  
 Directorio  
 Una carpeta local del cliente se conoce como un directorio. Ésta es la copia en el que un usuario realiza los cambios. Puede haber muchas copias de trabajo de un proyecto determinado; por lo general, cada desarrollador tiene su propia copia.  
  
 Obtener  
 Una operación get aporta la copia de trabajo del usuario al día con la copia del repositorio. A diferencia de una desprotección, se realiza una operación get cuando el usuario simplemente necesita la copia más reciente, pero tiene la intención de realizar ningún cambio.  
  
 Historial  
 Normalmente es un resumen de todas las desprotecciones, protecciones, actualizaciones, etiquetas y las versiones que se realiza en el repositorio de control de código fuente.  
  
 IDE  
 Normalmente, se hace referencia en el entorno de desarrollo integrado de Visual Studio. Sin embargo, también podría referirse a otros entornos de cliente que reconocen la API de complemento de Control de código fuente.  
  
 Combinar  
 El proceso durante el origen de dos o más archivos de código se combinan para formar un nuevo archivo que incorpora todas las características de los archivos anteriores. Este concepto es fundamental en el control de versiones donde dos o más desarrolladores pueden trabaja en archivos al mismo tiempo.  
  
 Proyecto  
 Una carpeta de control de código fuente a menudo se conoce como un proyecto. Esto no tiene ninguna relación con los proyectos o soluciones en Visual Studio.  
  
 Complemento  
 Un archivo DLL que proporciona funcionalidad de control de código fuente mediante la implementación de la API de complemento de Control de código fuente.  
  
 Repositorio  
 La copia maestra en un origen de sistema de control almacena el historial de revisión completa del proyecto. Cada proyecto tiene exactamente un repositorio.  
  
 Revisión  
 Un cambio confirmado en el historial de un archivo o conjunto de archivos. Una revisión es una instantánea en un proyecto que cambia continuamente.  
  
## <a name="see-also"></a>Vea también  
 [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)

