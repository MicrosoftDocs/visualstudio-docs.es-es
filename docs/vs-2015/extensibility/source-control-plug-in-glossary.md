---
title: Glosario de complementos de control de código fuente | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f5120a5c6678cac32ef65e08ef7dc34649364cf9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160606"
---
# <a name="source-control-plug-in-glossary"></a>Glosario del complemento de control de código fuente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los siguientes términos y definiciones útiles pertenecen a la documentación del SDK del complemento de control de código fuente.  
  
## <a name="definitions"></a>Definiciones  
 Checkin  
 Cuando un usuario realiza cambios en una copia de trabajo, el usuario debe enviar los cambios de la copia de trabajo en el repositorio central de control de código fuente. Esto crea una nueva revisión del archivo que está disponible para otros usuarios. Este proceso se denomina protección.  
  
 Restauración  
 Acción de solicitar una copia de trabajo desde el repositorio, que informa al repositorio de su intención de modificarla. Una copia de trabajo refleja el estado del proyecto en el momento en que se desprotege.  
  
 Remoto  
 Programa que utiliza el sistema de control de código fuente. Para el propósito de esta documentación, es el IDE de Visual Studio.  
  
 Comentario  
 Un mensaje que describe los cambios que un usuario puede adjuntar a una revisión cuando se realiza una operación de control de código fuente.  
  
 Conflicto  
 Situación en la que dos usuarios intentan proteger los cambios en la misma región del mismo archivo. Normalmente, se debe realizar una combinación.  
  
 Directorio  
 Se hace referencia a una carpeta local del lado cliente como un directorio. Esta es la copia en la que un usuario realmente realiza cambios. Puede haber muchas copias de trabajo de un proyecto determinado. generalmente, cada desarrollador tiene su propia copia.  
  
 Obtener  
 Una operación Get pone la copia de trabajo del usuario al día con la copia del repositorio. A diferencia de una desprotección, se realiza una obtención cuando el usuario simplemente necesita la última copia, pero pretende no realizar ningún cambio.  
  
 Historial  
 Normalmente, es un resumen de todas las desprotecciones, protecciones, actualizaciones, etiquetas y versiones realizadas en el repositorio de control de código fuente.  
  
 IDE  
 Normalmente hace referencia al entorno de desarrollo integrado de Visual Studio. Sin embargo, también podría hacer referencia a otros entornos de cliente que reconozcan la API del complemento de control de código fuente.  
  
 Merge  
 Proceso en el que dos o más archivos de código fuente se combinan para formar un nuevo archivo que incorpora todas las características de los archivos anteriores. Este concepto es fundamental en el control de versiones, en el que dos o más desarrolladores trabajan en los archivos al mismo tiempo.  
  
 Proyecto  
 Una carpeta de control de código fuente a menudo se denomina proyecto. Esto no tiene ninguna relación con proyectos o soluciones en Visual Studio.  
  
 Complemento  
 DLL que proporciona la funcionalidad de control de código fuente mediante la implementación de la API del complemento de control de código fuente.  
  
 Repositorio  
 Copia maestra en la que un sistema de control de código fuente almacena el historial de revisiones completo de un proyecto. Cada proyecto tiene exactamente un repositorio.  
  
 Revisión  
 Un cambio confirmado en el historial de un archivo o conjunto de archivos. Una revisión es una instantánea en un proyecto que cambia continuamente.  
  
## <a name="see-also"></a>Consulte también  
 [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)
