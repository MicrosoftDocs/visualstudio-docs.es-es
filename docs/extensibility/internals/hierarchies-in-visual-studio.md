---
title: Jerarquías en Visual Studio ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- hierarchies, Visual Studio IDE
- IDE, hierarchies
ms.assetid: 0a029a7c-79fd-4b54-bd63-bd0f21aa8d30
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cdbb8a0e58f6b1e5bc6e32f8c319d1480c4db4b5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708184"
---
# <a name="hierarchies-in-visual-studio"></a>Jerarquías en Visual Studio
El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno de desarrollo integrado (IDE) muestra un proyecto como una *jerarquía.* En el IDE, una jerarquía es un árbol de nodos, donde cada nodo tiene un conjunto de propiedades asociadas. Una jerarquía de *proyecto* es un contenedor que contiene los elementos del proyecto, las relaciones de los elementos y las propiedades y comandos asociados de los elementos.

 En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], se administran las jerarquías <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>de proyecto mediante la interfaz de jerarquía, . La <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfaz redirige los comandos que se invocan desde los elementos del proyecto a la ventana de jerarquía adecuada en lugar del controlador de comandos estándar.

## <a name="project-hierarchies"></a>Jerarquías de proyectos
 Cada jerarquía de proyectos contiene elementos que puede ver y editar. Estos elementos varían según el tipo de proyecto. Por ejemplo, un proyecto de base de datos puede contener procedimientos almacenados, vistas de base de datos y tablas de base de datos. Un proyecto de lenguaje de programación, por otro lado, probablemente incluirá archivos de origen y archivos de recursos para mapas de bits y cuadros de diálogo. Las jerarquías se pueden anidar, lo que proporciona cierta flexibilidad adicional al crear una jerarquía de proyecto.

 Al crear un nuevo tipo de proyecto, el tipo de proyecto controla el conjunto completo de elementos que se pueden editar en él. Sin embargo, los proyectos pueden contener elementos para los que no tienen compatibilidad con la edición. Por ejemplo, los proyectos de Visual C++ pueden contener archivos HTML, aunque Visual C++ no proporciona ningún editor personalizado para el tipo de archivo HTML.

 Las jerarquías administran la persistencia de los elementos que contienen. La implementación de la jerarquía debe controlar las propiedades especiales que afectan a la persistencia de los elementos dentro de la jerarquía. Por ejemplo, si los elementos representan objetos en un repositorio en lugar de archivos, la implementación de la jerarquía debe controlar la persistencia de esos objetos. El propio IDE dirige la jerarquía para guardar los elementos de acuerdo con la entrada del usuario, pero el IDE no controla las acciones necesarias para guardar esos elementos. En su lugar, el proyecto está en control.

 Cuando un usuario abre un elemento en un editor, la jerarquía que controla ese elemento está seleccionada y se convierte en la jerarquía activa. La jerarquía seleccionada determina el conjunto de comandos disponibles para actuar sobre el elemento. El seguimiento del foco del usuario de esta manera permite que la jerarquía refleje el contexto actual del usuario.

## <a name="see-also"></a>Vea también
- [Tipos de proyecto](../../extensibility/internals/project-types.md)
- [Selección y moneda en el IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Muestras VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples)
