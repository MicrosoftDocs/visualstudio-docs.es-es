---
title: Glosario de complementos de control de código fuente | Microsoft Docs
description: En este artículo se incluyen términos y definiciones útiles que pertenecen a la documentación del SDK del complemento de control de código fuente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5fe262091b25db3dae0388427afc3af6c9027872
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090101"
---
# <a name="source-control-plug-in-glossary"></a>Glosario del complemento de control de código fuente
Los siguientes términos y definiciones útiles pertenecen a la documentación del SDK del complemento de control de código fuente.

## <a name="definitions"></a>Definiciones
 Proteger cuando un usuario realiza cambios en una copia de trabajo, un usuario debe enviar los cambios de la copia de trabajo en el repositorio central de control de código fuente. Esto crea una nueva revisión del archivo que está disponible para otros usuarios. Este proceso se denomina protección.

 Desproteger el acto de solicitar una copia de trabajo desde el repositorio, lo que informa al repositorio de su intención de modificarla. Una copia de trabajo refleja el estado del proyecto en el momento en que se desprotege.

 Cliente un programa que utiliza el sistema de control de código fuente. Para el propósito de esta documentación, es el IDE de Visual Studio.

 Comente un mensaje que describe los cambios que un usuario puede adjuntar a una revisión cuando se realiza una operación de control de código fuente.

 Conflicto con una situación en la que dos usuarios intentan proteger los cambios en la misma región del mismo archivo. Normalmente, se debe realizar una combinación.

 Directorio: se hace referencia a una carpeta local del lado cliente como un directorio. Esta es la copia en la que un usuario realmente realiza cambios. Puede haber muchas copias de trabajo de un proyecto determinado. generalmente, cada desarrollador tiene su propia copia.

 Obtener una operación Get pone la copia de trabajo del usuario al día con la copia del repositorio. A diferencia de una desprotección, se realiza una obtención cuando el usuario simplemente necesita la última copia, pero pretende no realizar ningún cambio.

 Historial es normalmente un resumen de todas las desprotecciones, protecciones, actualizaciones, etiquetas y versiones realizadas en el repositorio de control de código fuente.

 El IDE normalmente hace referencia al entorno de desarrollo integrado de Visual Studio. Sin embargo, también podría hacer referencia a otros entornos de cliente que reconozcan la API del complemento de control de código fuente.

 Combine el proceso durante el cual dos o más archivos de código fuente se combinan para formar un nuevo archivo que incorpore todas las características de los archivos anteriores. Este concepto es fundamental en el control de versiones, en el que dos o más desarrolladores trabajan en los archivos al mismo tiempo.

 Project una carpeta de control de código fuente a menudo se denomina proyecto. Esto no tiene ninguna relación con proyectos o soluciones en Visual Studio.

 Complemento de un archivo DLL que proporciona la funcionalidad de control de código fuente mediante la implementación de la API del complemento de control de código fuente.

 Repositorio la copia maestra en la que un sistema de control de código fuente almacena el historial de revisiones completo de un proyecto. Cada proyecto tiene exactamente un repositorio.

 Revisar un cambio confirmado en el historial de un archivo o conjunto de archivos. Una revisión es una instantánea en un proyecto que cambia continuamente.

## <a name="see-also"></a>Consulte también
- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)
