---
title: "Las decisiones de diseño del tipo de proyecto | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project types, project file persistence
- project types, commitment mechanics
- project types, items
- project types, design decisions
ms.assetid: f68671fe-fd7a-4e56-a0b5-330b0f1fedb1
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a3e0216161669e12c245484da3ca6e4de63c6a48
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="project-type-design-decisions"></a>Decisiones de diseño del tipo de proyecto
Antes de crear un nuevo tipo de proyecto, debe realizar varias decisiones de diseño con respecto a su tipo de proyecto. Debe decidir qué tipos de elementos que contengan los proyectos, cómo se conservarán los archivos de proyecto y qué modelo de compromiso va a usar.  
  
## <a name="project-items"></a>Elementos de proyecto  
 ¿Va a usar el proyecto de archivos u objetos abstractos? ¿Si utiliza archivos, estarán basados en la referencia o directorio de archivos? ¿Son los archivos u objetos abstractos que va a ser local o remota?  
  
 Los elementos de un proyecto pueden ser archivos, o pueden ser objetos más abstractos, como los objetos en una base de datos repositorio o conexiones de datos a través de Internet. Si los elementos son archivos, el proyecto puede ser basada en una referencia o un proyecto basado en el directorio.  
  
 En los proyectos basados en referencias, los elementos pueden aparecer en más de un proyecto. Sin embargo, el archivo real que representa un elemento se encuentra en un solo directorio. En proyectos basados en el directorio, todos los elementos de proyecto existen en la estructura de directorios. Para obtener más información, consulte [NIB: administración elementos en proyectos de](http://msdn.microsoft.com/en-us/762e606b-7f44-4b66-97a1-e30a703654a0).  
  
 Los elementos locales se almacenan en el mismo equipo donde está instalada la aplicación. Elementos remotos pueden almacenarse en un servidor independiente en una red local o en otro lugar en Internet.  
  
## <a name="project-file-persistence"></a>Persistencia del archivo de proyecto  
 ¿Datos se almacenarán en sistemas de archivos sin formato común, o en el almacenamiento estructurado? ¿Se abrirán los archivos mediante un editor estándar o un editor específico del proyecto?  
  
 Para conservar sus datos, mayoría de las aplicaciones guarda sus datos en un archivo y, a continuación, leerlo cuando un usuario debe revisar o cambiar la información.  
  
 Almacenamiento estructurado, denominado también archivos compuestos, normalmente se utiliza cuando varios objetos de modelo de objetos componentes (COM) necesitan almacenar sus datos almacenados en un único archivo. Con el almacenamiento estructurado, varios componentes de software diferentes pueden compartir un único archivo de disco.  
  
 Tiene varias opciones para tener en cuenta en relación con la persistencia para los elementos de su proyecto. Puede realizar cualquiera de las siguientes opciones:  
  
-   Guarde cada archivo individualmente cuando se ha cambiado.  
  
-   Capturar muchas transacciones en un único **guardar** operación.  
  
-   Guardar localmente, archivos y, a continuación, publicar en un servidor o usar otro enfoque para guardar elementos de proyecto cuando el elemento representa una conexión de datos a un objeto remoto.  
  
 Para obtener más información acerca de la persistencia, consulte [persistencia de un proyecto](../../extensibility/internals/project-persistence.md) y [abrir y guardar elementos de proyecto](../../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="project-commitment-model"></a>Modelo de compromiso de proyecto  
 ¿Se abrirá objetos de datos almacenados en modo directo o en modo de transacción?  
  
 Cuando los objetos de datos se abre en modo directo, se incorporan los cambios realizados en los datos inmediatamente o cuando el usuario guarda manualmente el archivo.  
  
 Cuando se abren los objetos de datos utilizando el modo de transacción, los cambios se guardan en una ubicación temporal en la memoria y no se confirman hasta que el usuario decide guardar el archivo manualmente. En ese momento, todos los cambios se producen juntos o no se realizará ningún cambio.  
  
## <a name="see-also"></a>Vea también  
 [Lista de comprobación: Creación de nuevos tipos de proyecto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [NIB: administración elementos en proyectos](http://msdn.microsoft.com/en-us/762e606b-7f44-4b66-97a1-e30a703654a0)   
 [Abrir y guardar elementos de proyecto](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Persistencia de un proyecto](../../extensibility/internals/project-persistence.md)   
 [Elementos de un modelo de proyecto](../../extensibility/internals/elements-of-a-project-model.md)   
 [Componentes principales del proyecto de modelo](../../extensibility/internals/project-model-core-components.md)   
 [Creación de tipos de proyecto](../../extensibility/internals/creating-project-types.md)