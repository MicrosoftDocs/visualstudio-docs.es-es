---
title: Glosario de complementos de Control de código fuente (Source Control Plug-in Glossary) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3835561eb63fa2a4a71174732c07ecd73f1df5d7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699907"
---
# <a name="source-control-plug-in-glossary"></a>Glosario del complemento de control de código fuente
Los siguientes términos y definiciones útiles pertenecen a la documentación del SDK de complementode de Control de código fuente.

## <a name="definitions"></a>Definiciones
 Protección Cuando un usuario realiza cambios en una copia de trabajo, un usuario debe enviar cambios desde la copia de trabajo al repositorio de control de código fuente central. Esto crea una nueva revisión del archivo que está disponible para otros usuarios. Este proceso se denomina check-in.

 Desprotección El acto de solicitar una copia de trabajo del repositorio, informando al repositorio de su intención de modificarla. Una copia de trabajo refleja el estado del proyecto en el momento en que se desprotege.

 Cliente Un programa que utiliza el sistema de control de código fuente. Para el propósito de esta documentación, es el IDE de Visual Studio.

 Comentario Un mensaje que describe los cambios que un usuario puede adjuntar a una revisión cuando se realiza una operación de control de código fuente.

 Conflicto Una situación cuando dos usuarios intentan proteger los cambios en la misma región del mismo archivo. Normalmente, se debe realizar una combinación.

 Directorio Una carpeta local del lado cliente se conoce como un directorio. Esta es la copia en la que un usuario realmente realiza cambios. Puede haber muchas copias de trabajo de un proyecto determinado; generalmente cada desarrollador tiene su propia copia.

 Obtener una operación get pone al día la copia de trabajo del usuario con la copia del repositorio. A diferencia de una desprotección, se realiza una obtención cuando el usuario simplemente necesita la copia más reciente, pero tiene la intención de no realizar ningún cambio.

 Historial Normalmente es un resumen de todas las desprotecciones, comprobaciones, actualizaciones, etiquetas y versiones realizadas en el repositorio de control de código fuente.

 IDE Generalmente hace referencia al entorno de desarrollo integrado de Visual Studio. Sin embargo, también podría hacer referencia a otros entornos de cliente que reconocen la API de complemento de Control de código fuente.

 Combinar El proceso durante el cual se combinan dos o más archivos de código fuente para formar un nuevo archivo que incorpora todas las características de los archivos anteriores. Este concepto es vital en el control de versiones donde dos o más desarrolladores trabajan en archivos simultáneamente.

 Proyecto Una carpeta de control de código fuente se conoce a menudo como un proyecto. Esto no tiene ninguna relación con proyectos o soluciones en Visual Studio.

 Complemento un archivo DLL que proporciona funcionalidad de control de código fuente mediante la implementación de la API de complemento de Control de código fuente.

 Repositorio La copia maestra donde un sistema de control de código fuente almacena el historial de revisiones completo de un proyecto. Cada proyecto tiene exactamente un repositorio.

 Revisión Un cambio confirmado en el historial de un archivo o conjunto de archivos. Una revisión es una instantánea en un proyecto que cambia continuamente.

## <a name="see-also"></a>Vea también
- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)
