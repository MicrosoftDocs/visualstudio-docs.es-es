---
title: Glosario del complemento de Control de origen | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0df624a27513fa0eb18b2643bb7c680d71d94c0c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56722380"
---
# <a name="source-control-plug-in-glossary"></a>Glosario del complemento de control de código fuente
Los siguientes términos útiles y definiciones se refieren a la documentación del SDK de complemento de Control de origen.

## <a name="definitions"></a>Definiciones
 Protección cuando un usuario realiza cambios en una copia de trabajo, un usuario debe enviar los cambios desde la copia de trabajo en el repositorio de control de origen central. Esto crea una nueva revisión del archivo que está disponible para otros usuarios. Este proceso se denomina una protección.

 Retirada el acto de solicitar una copia de trabajo desde el repositorio, que informa el repositorio de su intención para modificarlo. Una copia de trabajo refleja el estado del proyecto hasta el momento en que lo tiene desprotegido.

 Programa de un cliente que usa el sistema de control de código fuente. En esta documentación, es el IDE de Visual Studio.

 Mensaje de un comentario que describa los cambios que un usuario puede asociar a una revisión cuando se realiza una operación de control de código fuente.

 Situación de un conflicto cuando dos usuarios intentan insertar en el repositorio los cambios en la misma región del mismo archivo. Normalmente, se debe realizar una fusión mediante combinación.

 Carpeta local del directorio un cliente se conoce como un directorio. Ésta es la copia en el que un usuario realiza los cambios. Puede haber muchas copias de trabajo de un proyecto determinado; por lo general, cada desarrollador tiene su propia copia.

 Operación de obtención de un Get aporta la copia de trabajo del usuario al día con la copia del repositorio. A diferencia de una desprotección, se realiza una operación get cuando el usuario simplemente necesita la copia más reciente, pero tiene la intención de realizar ningún cambio.

 Historial normalmente es un resumen de todas las desprotecciones, protecciones, actualizaciones, etiquetas y las versiones que se realiza en el repositorio de control de código fuente.

 IDE suele hacer referencia en el entorno de desarrollo integrado de Visual Studio. Sin embargo, también podría referirse a otros entornos de cliente que reconocen la API de complemento de Control de código fuente.

 Combine el proceso durante el origen de dos o más archivos de código se combinan para formar un nuevo archivo que incorpora todas las características de los archivos anteriores. Este concepto es fundamental en el control de versiones donde dos o más desarrolladores pueden trabaja en archivos al mismo tiempo.

 Carpeta de control de código fuente de un proyecto a menudo se conoce como un proyecto. Esto no tiene ninguna relación con los proyectos o soluciones en Visual Studio.

 Complemento de una DLL que proporciona funcionalidad de control de código fuente mediante la implementación de la API de complemento de Control de código fuente.

 Repositorio la copia maestra donde un sistema de control de código fuente almacena el historial de revisión completa del proyecto. Cada proyecto tiene exactamente un repositorio.

 Revisión A confirmó el cambio en el historial de un archivo o conjunto de archivos. Una revisión es una instantánea en un proyecto que cambia continuamente.

## <a name="see-also"></a>Vea también
- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)