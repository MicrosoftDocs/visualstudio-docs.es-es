---
title: Jerarquías en Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- hierarchies, Visual Studio IDE
- IDE, hierarchies
ms.assetid: 0a029a7c-79fd-4b54-bd63-bd0f21aa8d30
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 08005b69a1af16b07212cb29547875fad89e1d6a
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75848939"
---
# <a name="hierarchies-in-visual-studio"></a>Jerarquías en Visual Studio
El entorno de desarrollo integrado (IDE) de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] muestra un proyecto como una *jerarquía*. En el IDE, una jerarquía es un árbol de nodos, donde cada nodo tiene un conjunto de propiedades asociadas. Una *jerarquía de proyecto* es un contenedor que contiene los elementos del proyecto, las relaciones de los elementos y las propiedades y los comandos asociados de los elementos.

 En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], las jerarquías de proyecto se administran mediante la interfaz de la jerarquía <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>. La interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> redirige los comandos que se invocan desde los elementos de proyecto a la ventana de jerarquía adecuada en lugar del controlador de comandos estándar.

## <a name="project-hierarchies"></a>Jerarquías de proyecto
 Cada jerarquía de proyecto contiene elementos que puede ver y editar. Estos elementos varían según el tipo de proyecto. Por ejemplo, un proyecto de base de datos podría contener procedimientos almacenados, vistas de base de datos y tablas de base de datos. Un proyecto de lenguaje de programación, por otro lado, probablemente incluirá archivos de código fuente y archivos de recursos para los mapas de bits y los cuadros de diálogo. Las jerarquías se pueden anidar, lo que proporciona una flexibilidad adicional al crear una jerarquía de proyecto.

 Cuando se crea un nuevo tipo de proyecto, el tipo de proyecto controla el conjunto completo de elementos que se pueden editar en él. Sin embargo, los proyectos pueden contener elementos para los que no son compatibles con la edición. Por ejemplo, los C++ proyectos visuales pueden contener archivos HTML, aunque visual C++ no proporciona ningún editor personalizado para el tipo de archivo HTML.

 Las jerarquías administran la persistencia de los elementos que contienen. La implementación de la jerarquía debe controlar cualquier propiedad especial que afecte a la persistencia de los elementos dentro de la jerarquía. Por ejemplo, si los elementos representan objetos en un repositorio en lugar de archivos, la implementación de la jerarquía debe controlar la persistencia de esos objetos. El propio IDE dirige la jerarquía para guardar los elementos conforme a los datos proporcionados por el usuario, pero el IDE no controla ninguna acción necesaria para guardar dichos elementos. En su lugar, el proyecto se encuentra en el control.

 Cuando un usuario abre un elemento en un editor, la jerarquía que controla ese elemento se selecciona y se convierte en la jerarquía activa. La jerarquía seleccionada determina el conjunto de comandos disponibles para actuar sobre el elemento. El seguimiento del foco del usuario de esta manera permite que la jerarquía refleje el contexto actual del usuario.

## <a name="see-also"></a>Vea también
- [Tipos de proyecto](../../extensibility/internals/project-types.md)
- [Selección y moneda en el IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Ejemplos de VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples)
