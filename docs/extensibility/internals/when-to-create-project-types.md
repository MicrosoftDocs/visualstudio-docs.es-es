---
title: Cuándo crear tipos de proyecto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, conditions for creating
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 861250dac25288f353cbd5c57f510bf67dadce70
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80703428"
---
# <a name="when-to-create-project-types"></a>Momento para la creación de tipos de proyecto
La creación de un nuevo tipo de proyecto proporciona una base para la personalización [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para los usuarios. Sin embargo, no es necesario crear un nuevo tipo de proyecto para todas las [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] personalizaciones. Las instrucciones siguientes le ayudarán a determinar si es necesario un nuevo tipo de proyecto para su escenario.

## <a name="create-a-new-project-type"></a>Crear un nuevo tipo de proyecto
 Debe crear un tipo de proyecto si desea personalizar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para que actúe de una o varias de las siguientes maneras:

- Participar en la compilación, implementación, configuración y control de código fuente.

- Ofrecer compatibilidad con la depuración.

- Mostrar los elementos de proyecto en **Explorador de soluciones**.

- Utilice el cuadro de diálogo **Abrir proyecto** o **nuevo proyecto** .

- Compatibilidad con el anidamiento del proyecto.

## <a name="extend-an-existing-project-type"></a>Extender un tipo de proyecto existente
 Es posible que desee crear un nuevo tipo de proyecto que pueda usar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de las siguientes maneras para modificar o extender el comportamiento de un tipo de proyecto existente, por ejemplo, modificando el proceso de compilación de los [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] proyectos:

- Trabajar con varios archivos como una sola unidad.

- Muestra un único archivo como una jerarquía de subelementos.

- Mostrar un contexto de comandos alrededor de los editores.

- Mostrar un contexto de servicio para los editores.

## <a name="use-an-existing-project-type"></a>Usar un tipo de proyecto existente
 A veces no es necesario crear un nuevo proyecto. En la tabla siguiente se muestran las tareas para las que no tiene que crear un tipo de proyecto.

|Tarea|Descripción|
|----------|-----------------|
|Controlar comandos|Cualquier VSPackage puede controlar comandos.|
|Compilar un editor|Los editores personalizados se pueden registrar. Para obtener más información, vea [ventanas de documento y editores](https://msdn.microsoft.com/library/603625e1-62b6-413a-bc44-089346e166bc).|
|Ventanas propietarias|Puede crear ventanas de herramientas y de documentos sin agregar un nuevo tipo de proyecto.|
|Exponer propiedades en el ventana Propiedades|Todos los objetos pueden exponer propiedades.|

## <a name="create-a-project-subtype"></a>Crear un subtipo de proyecto
 Puede usar subtipos de proyecto para extender un tipo de proyecto administrado sin tener que crear un nuevo tipo de proyecto. Los subtipos de proyecto utilizan la agregación COM para extender los proyectos administrados escritos en Microsoft [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] o [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] . Con la agregación COM, puede volver a usar gran parte de la implementación del sistema de proyectos administrados y seguir personalizando para un escenario concreto a través de la agregación y el uso de interfaces auxiliares. Para obtener más información sobre los subtipos de proyecto, vea [subtipos de proyecto](../../extensibility/internals/project-subtypes.md).

## <a name="see-also"></a>Vea también
- [Ventanas de documento y editores](https://msdn.microsoft.com/library/603625e1-62b6-413a-bc44-089346e166bc)
- [Lista de comprobación: Creación de nuevos tipos de proyectos](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Jerarquías en Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
