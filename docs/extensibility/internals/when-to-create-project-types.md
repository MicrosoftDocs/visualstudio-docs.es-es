---
title: Cuándo se debe crear tipos de proyecto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, conditions for creating
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eaf8982afb01ee07eb8c2d672f351c6e917620a6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62907593"
---
# <a name="when-to-create-project-types"></a>Momento para la creación de tipos de proyecto
Crear un nuevo tipo de proyecto proporciona una base para personalizar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para los usuarios. Sin embargo, crear un nuevo tipo de proyecto no es necesario para todos los [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] personalizaciones. Las instrucciones siguientes le ayudarán a determinar si un nuevo tipo de proyecto es necesario para su escenario.

## <a name="create-a-new-project-type"></a>Crear un nuevo tipo de proyecto
 Debe crear un tipo de proyecto si desea personalizar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para actuar en una o varias de las maneras siguientes:

- Participa en la compilación, implementación, las configuraciones y control de código fuente.

- Ofrece compatibilidad con la depuración.

- Mostrar elementos de proyecto en **el Explorador de soluciones**.

- Use la **Abrir proyecto** o **nuevo proyecto** cuadro de diálogo.

- Admite el anidamiento de proyecto.

## <a name="extend-an-existing-project-type"></a>Extender un tipo de proyecto existente
 Desea crear un nuevo tipo de proyecto que puede usar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] en los siguientes métodos para modificar o extender el comportamiento de un tipo de proyecto existente, por ejemplo, modificar el proceso de compilación para [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] proyectos:

- Trabajar con varios archivos como una sola unidad.

- Mostrar un único archivo como una jerarquía de elementos secundarios.

- Mostrar un contexto de comandos en torno a los editores.

- Mostrar un contexto de servicio para los editores.

## <a name="use-an-existing-project-type"></a>Utilizar un tipo de proyecto existente
 Crear un nuevo proyecto a veces no es necesario. En la tabla siguiente se muestra las tareas que no es necesario para crear un tipo de proyecto para.

|Tarea|Descripción|
|----------|-----------------|
|Control de comandos|Cualquier VSPackage puede controlar los comandos.|
|Creación de un editor|Editores personalizados se pueden registrar. Para obtener más información, consulte [editores y documentos Windows](https://msdn.microsoft.com/library/603625e1-62b6-413a-bc44-089346e166bc).|
|Propietario de windows|Puede crear ventanas de herramientas y documentos sin agregar un nuevo tipo de proyecto.|
|Expone las propiedades en la ventana Propiedades|Todos los objetos pueden exponer propiedades.|

## <a name="create-a-project-subtype"></a>Creación de un subtipo de proyecto
 Subtipos de proyecto se pueden usar para extender un tipo de proyecto administrado sin tener que crear un nuevo tipo de proyecto. Subtipos de proyecto usar agregación COM para ampliar proyectos administrados, escritos en Microsoft [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] o [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]. Con la agregación de COM, puede reutilizar gran parte de la implementación de sistema de proyecto administrado y personalizar para un escenario determinado mediante la agregación y el uso de interfaces admitidas. Para obtener más información acerca de subtipos de proyecto, vea [subtipos de proyecto](../../extensibility/internals/project-subtypes.md).

## <a name="see-also"></a>Vea también
- [Editores y documentos Windows](https://msdn.microsoft.com/library/603625e1-62b6-413a-bc44-089346e166bc)
- [Lista de comprobación: Creación de tipos de proyectos](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Jerarquías en Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)