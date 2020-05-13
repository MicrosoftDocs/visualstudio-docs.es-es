---
title: Decisiones de diseño de tipo de proyecto ? Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706370"
---
# <a name="project-type-design-decisions"></a>Decisiones de diseño del tipo de proyecto
Antes de crear un nuevo tipo de proyecto, debe tomar varias decisiones de diseño con respecto al tipo de proyecto. Debe decidir qué tipos de elementos contendrán sus proyectos, cómo se conservarán los archivos de proyecto y qué modelo de compromiso usará.

## <a name="project-items"></a>Elementos de un proyecto
 ¿Utilizará el proyecto archivos u objetos abstractos? Si utiliza archivos, ¿serán archivos basados en referencias o en directorios? ¿Los archivos u objetos abstractos van a ser locales o remotos?

 Los elementos de un proyecto pueden ser archivos o pueden ser objetos más abstractos, como objetos en un repositorio de base de datos o conexiones de datos a través de Internet. Si los elementos son archivos, el proyecto puede ser un proyecto basado en referencias o un proyecto basado en directorios.

 En los proyectos basados en referencias, los elementos pueden aparecer en más de un proyecto. Sin embargo, el archivo real que representa un elemento se encuentra en un solo directorio. En los proyectos basados en directorios, todos los elementos de proyecto existen en la estructura de directorios.

 Los elementos locales se almacenan en el mismo equipo donde está instalada la aplicación. Los elementos remotos se pueden almacenar en un servidor independiente en una red local o en otro lugar de Internet.

## <a name="project-file-persistence"></a>Persistencia del archivo de proyecto
 ¿Los datos se almacenarán en sistemas de archivos planos comunes o en almacenamiento estructurado? ¿Se abrirán los archivos mediante un editor estándar o un editor específico del proyecto?

 Para conservar sus datos, la mayoría de las aplicaciones guardan sus datos en un archivo y, a continuación, los vuelven a leer cuando un usuario debe revisar o cambiar la información.

 El almacenamiento estructurado, también denominado archivos compuestos, se utiliza normalmente cuando varios objetos del modelo de objetos componentes (COM) necesitan almacenar sus datos persistentes en un único archivo. Con el almacenamiento estructurado, varios componentes de software diferentes pueden compartir un único archivo de disco.

 Tiene varias opciones a tener en cuenta con respecto a la persistencia de los elementos del proyecto. Puede realizar cualquiera de las siguientes opciones:

- Guarde cada archivo individualmente cuando se haya cambiado.

- Capture muchas transacciones en una sola operación **De guardar.**

- Guarde archivos localmente y, a continuación, publique en un servidor o use otro enfoque para guardar elementos de proyecto cuando el elemento representa una conexión de datos a un objeto remoto.

  Para obtener más información acerca de la persistencia, vea [Persistencia](../../extensibility/internals/project-persistence.md) del proyecto y [Abrir y guardar elementos](../../extensibility/internals/opening-and-saving-project-items.md)de proyecto .

## <a name="project-commitment-model"></a>Modelo de compromiso del proyecto
 ¿Se abrirán los objetos de datos persistentes en modo directo o en modo de transacción?

 Cuando los objetos de datos se abren en modo directo, los cambios realizados en los datos se incorporan inmediatamente o cuando el usuario guarda manualmente el archivo.

 Cuando los objetos de datos se abren mediante el modo de transacción, los cambios se guardan en una ubicación temporal en la memoria y no se confirman hasta que el usuario elige manualmente guardar el archivo. En ese momento, todos los cambios deben ocurrir juntos o no se realizarán cambios.

## <a name="see-also"></a>Vea también
- [Lista de comprobación: creación de nuevos tipos de proyecto](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Apertura y guardado de elementos de proyecto](../../extensibility/internals/opening-and-saving-project-items.md)
- [Persistencia de un proyecto](../../extensibility/internals/project-persistence.md)
- [Elementos de un modelo de proyecto](../../extensibility/internals/elements-of-a-project-model.md)
- [Componentes principales del modelo de proyecto](../../extensibility/internals/project-model-core-components.md)
- [Creación de tipos de proyecto](../../extensibility/internals/creating-project-types.md)
