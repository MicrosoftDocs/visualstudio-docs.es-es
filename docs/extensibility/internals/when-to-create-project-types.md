---
title: Cuándo crear tipos de proyecto ? Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703428"
---
# <a name="when-to-create-project-types"></a>Momento para la creación de tipos de proyecto
La creación de un nuevo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tipo de proyecto proporciona una base para personalizar para los usuarios. Sin embargo, no es necesario [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] crear un nuevo tipo de proyecto para todas las personalizaciones. Las siguientes directrices deben ayudarle a determinar si se requiere un nuevo tipo de proyecto para su escenario.

## <a name="create-a-new-project-type"></a>Crear un nuevo tipo de proyecto
 Debe crear un tipo de proyecto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] si desea personalizar para que actúe de una o varias de las siguientes maneras:

- Participe en la compilación, la implementación, las configuraciones y el control de código fuente.

- Ofrezca compatibilidad con la depuración.

- Mostrar elementos de proyecto en el Explorador de **soluciones**.

- Utilice el cuadro de diálogo **Abrir proyecto** o **Nuevo proyecto.**

- Apoyar el anidamiento de proyectos.

## <a name="extend-an-existing-project-type"></a>Extender un tipo de proyecto existente
 Es posible que desee crear un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nuevo tipo de proyecto que se puede utilizar de las siguientes maneras para modificar o ampliar el comportamiento de un tipo de proyecto existente, por ejemplo, modificar el proceso de compilación de [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] proyectos:

- Trabaje con varios archivos como una sola unidad.

- Mostrar un único archivo como una jerarquía de subelementos.

- Mostrar un contexto de comando alrededor de los editores.

- Mostrar un contexto de servicio para los editores.

## <a name="use-an-existing-project-type"></a>Usar un tipo de proyecto existente
 A veces no es necesario crear un nuevo proyecto. En la tabla siguiente se muestran las tareas para las que no es necesario crear un tipo de proyecto.

|Tarea|Descripción|
|----------|-----------------|
|Gestión de comandos|Cualquier VSPackage puede controlar comandos.|
|Construir un editor|Los editores personalizados se pueden registrar. Para obtener más información, consulte [Documento de Windows y editores](https://msdn.microsoft.com/library/603625e1-62b6-413a-bc44-089346e166bc).|
|Poseer ventanas|Puede crear ventanas de herramientas y documentos sin agregar un nuevo tipo de proyecto.|
|Exposición de propiedades en la ventana Propiedades|Todos los objetos pueden exponer propiedades.|

## <a name="create-a-project-subtype"></a>Crear un subtipo de proyecto
 Puede usar subtipos de proyecto para extender un tipo de proyecto administrado sin tener que crear un nuevo tipo de proyecto. Los subtipos de proyecto utilizan la [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] agregación COM para extender proyectos administrados escritos en Microsoft o [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]. Con la agregación COM, puede reutilizar gran parte de la implementación del sistema de proyectos administrados y personalizar para un escenario determinado mediante la agregación y el uso de interfaces auxiliares. Para obtener más información acerca de los subtipos de proyecto, vea [Subtipos de proyecto](../../extensibility/internals/project-subtypes.md).

## <a name="see-also"></a>Vea también
- [Documentar Windows y Editores](https://msdn.microsoft.com/library/603625e1-62b6-413a-bc44-089346e166bc)
- [Lista de comprobación: creación de nuevos tipos de proyecto](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Jerarquías en Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
