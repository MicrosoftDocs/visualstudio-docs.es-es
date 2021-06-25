---
title: Glosario del complemento de control de código fuente | Microsoft Docs
description: En este artículo se incluyen términos y definiciones útiles que pertenecen a la documentación del SDK del complemento de control de código fuente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 05b215de4191362a539d3b03ac858da6bb7ee292
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899529"
---
# <a name="source-control-plug-in-glossary"></a>Glosario del complemento de control de código fuente
Los siguientes términos y definiciones útiles pertenecen a la documentación del SDK del complemento de control de código fuente.

## <a name="definitions"></a>Definiciones
 Checkin Cuando un usuario realiza cambios en una copia en funcionamiento, un usuario debe enviar los cambios de la copia de trabajo al repositorio central de control de código fuente. Esto crea una nueva revisión del archivo que está disponible para otros usuarios. Este proceso se denomina "checkin".

 Desproteme El acto de solicitar una copia en funcionamiento del repositorio, informando al repositorio de su intención de modificarlo. Una copia de trabajo refleja el estado del proyecto en el momento en que se desprotee.

 Cliente Un programa que usa el sistema de control de código fuente. Para esta documentación, es el ide Visual Studio.

 Comentario Mensaje que describe los cambios que un usuario puede adjuntar a una revisión cuando se realiza una operación de control de código fuente.

 Conflicto Una situación en la que dos usuarios intentan comprobar los cambios en la misma región del mismo archivo. Normalmente, se debe realizar una combinación.

 Directorio Una carpeta local del lado cliente se conoce como directorio. Esta es la copia en la que un usuario realmente realiza cambios. Puede haber muchas copias de trabajo de un proyecto determinado; por lo general, cada desarrollador tiene su propia copia.

 Obtener una operación get pone al día la copia de trabajo del usuario con la copia del repositorio. A diferencia de una desprotección, se realiza una operación get cuando el usuario simplemente necesita la copia más reciente, pero no tiene intención de realizar ningún cambio.

 Historial Suele ser un resumen de todas las desprotecciones, checkins, actualizaciones, etiquetas y versiones realizadas en el repositorio de control de código fuente.

 El IDE suele hacer referencia a la Visual Studio entorno de desarrollo integrado. Sin embargo, también podría hacer referencia a otros entornos de cliente que reconocen la API del complemento de control de código fuente.

 Combinar Proceso durante el cual se combinan dos o más archivos de código fuente para formar un nuevo archivo que incorpora todas las características de los archivos anteriores. Este concepto es fundamental en el control de versiones, donde dos o más desarrolladores trabajan en archivos simultáneamente.

 Proyecto Una carpeta de control de código fuente se conoce a menudo como proyecto. Esto no tiene ninguna relación con proyectos o soluciones en Visual Studio.

 Complemento Dll que proporciona funcionalidad de control de código fuente mediante la implementación de la API de complemento de control de código fuente.

 Repositorio Copia maestra donde un sistema de control de código fuente almacena el historial de revisiones completo de un proyecto. Cada proyecto tiene exactamente un repositorio.

 Revisión Un cambio confirmado en el historial de un archivo o conjunto de archivos. Una revisión es una instantánea de un proyecto que cambia continuamente.

## <a name="see-also"></a>Consulte también
- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)
