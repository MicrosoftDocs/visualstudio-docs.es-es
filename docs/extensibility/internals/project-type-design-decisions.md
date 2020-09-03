---
title: Decisiones de diseño de tipo de proyecto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, project file persistence
- project types, commitment mechanics
- project types, items
- project types, design decisions
ms.assetid: f68671fe-fd7a-4e56-a0b5-330b0f1fedb1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e33ac1c4168593b881f799dfdfb94005fb55fc1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80706370"
---
# <a name="project-type-design-decisions"></a>Decisiones de diseño del tipo de proyecto
Antes de crear un nuevo tipo de proyecto, debe tomar varias decisiones de diseño con respecto al tipo de proyecto. Debe decidir qué tipos de elementos contendrán los proyectos, cómo se conservarán los archivos del proyecto y qué modelo de compromiso usará.

## <a name="project-items"></a>Elementos de un proyecto
 ¿Usará el proyecto archivos o objetos abstractos? Si usa archivos, ¿serán archivos de referencia o basados en directorios? ¿Los archivos o los objetos abstractos van a ser locales o remotos?

 Los elementos de un proyecto pueden ser archivos o bien pueden ser objetos más abstractos como, por ejemplo, objetos en un repositorio de bases de datos o conexiones de datos a través de Internet. Si los elementos son archivos, el proyecto puede ser un proyecto basado en referencia o en un directorio.

 En los proyectos basados en referencias, los elementos pueden aparecer en más de un proyecto. Sin embargo, el archivo real que representa un elemento solo se encuentra en un directorio. En los proyectos basados en directorios, todos los elementos de proyecto existen en la estructura de directorios.

 Los elementos locales se almacenan en el mismo equipo en el que está instalada la aplicación. Los elementos remotos se pueden almacenar en un servidor independiente en una red local o en cualquier otro lugar de Internet.

## <a name="project-file-persistence"></a>Persistencia del archivo de proyecto
 ¿Los datos se almacenarán en sistemas de archivos planos comunes o en almacenamiento estructurado? ¿Se abrirán los archivos mediante un editor estándar o un editor específico del proyecto?

 Para conservar los datos, la mayoría de las aplicaciones guardan los datos en un archivo y, a continuación, los Lee de nuevo cuando un usuario debe revisar o cambiar la información.

 El almacenamiento estructurado, también denominado archivos compuestos, se utiliza normalmente cuando varios objetos del modelo de objetos componentes (COM) necesitan almacenar los datos almacenados en un único archivo. Con el almacenamiento estructurado, varios componentes de software diferentes pueden compartir un único archivo de disco.

 Tiene varias opciones que hay que tener en cuenta con respecto a la persistencia de los elementos del proyecto. Puede realizar cualquiera de las siguientes opciones:

- Guarde cada archivo individualmente cuando se haya cambiado.

- Capture muchas transacciones en una sola operación de **Guardar** .

- Guarde los archivos localmente y, a continuación, publique en un servidor o use otro método para guardar los elementos de proyecto cuando el elemento represente una conexión de datos a un objeto remoto.

  Para obtener más información sobre la persistencia, vea [persistencia del proyecto](../../extensibility/internals/project-persistence.md) y [abrir y guardar elementos de proyecto](../../extensibility/internals/opening-and-saving-project-items.md).

## <a name="project-commitment-model"></a>Modelo de compromiso del proyecto
 ¿Los objetos de datos persistentes se abrirán en modo directo o de transacción?

 Cuando los objetos de datos se abren en modo directo, los cambios que se realizaron en los datos se incorporan inmediatamente o cuando el usuario guarda manualmente el archivo.

 Cuando los objetos de datos se abren mediante el modo de transacción, los cambios se guardan en una ubicación temporal en la memoria y no se confirman hasta que el usuario elige guardar manualmente el archivo. En ese momento, todos los cambios deben realizarse juntos o no se realizará ningún cambio.

## <a name="see-also"></a>Consulte también
- [Lista de comprobación: Creación de nuevos tipos de proyectos](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Apertura y guardado de elementos de proyecto](../../extensibility/internals/opening-and-saving-project-items.md)
- [Persistencia de un proyecto](../../extensibility/internals/project-persistence.md)
- [Elementos de un modelo de proyecto](../../extensibility/internals/elements-of-a-project-model.md)
- [Componentes principales del modelo de proyecto](../../extensibility/internals/project-model-core-components.md)
- [Creación de tipos de proyecto](../../extensibility/internals/creating-project-types.md)
