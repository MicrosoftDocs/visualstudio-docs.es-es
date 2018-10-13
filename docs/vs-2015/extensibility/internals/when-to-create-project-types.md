---
title: Cuándo se debe crear tipos de proyecto | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project types, conditions for creating
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 98dd3f0058e2dacd1a6ab8ed3fc048dfd2e6397e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49245406"
---
# <a name="when-to-create-project-types"></a>Momento para la creación de tipos de proyecto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Crear un nuevo tipo de proyecto proporciona una base para personalizar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] para los usuarios. Sin embargo, crear un nuevo tipo de proyecto no es necesario para todos los [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] personalizaciones. Las instrucciones siguientes le ayudarán a determinar si un nuevo tipo de proyecto es necesario para su escenario.  
  
## <a name="create-a-new-project-type"></a>Crear un nuevo tipo de proyecto  
 Debe crear un tipo de proyecto si desea personalizar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] para actuar en una o varias de las maneras siguientes:  
  
-   Participa en la compilación, implementación, las configuraciones y control de código fuente.  
  
-   Ofrece compatibilidad con la depuración.  
  
-   Mostrar elementos de proyecto en **el Explorador de soluciones**.  
  
-   Use la **Abrir proyecto** o **nuevo proyecto** cuadro de diálogo.  
  
-   Admite el anidamiento de proyecto.  
  
## <a name="extend-an-existing-project-type"></a>Extender un tipo de proyecto existente  
 Desea crear un nuevo tipo de proyecto que puede usar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] en los siguientes métodos para modificar o extender el comportamiento de un tipo de proyecto existente, por ejemplo, modificar el proceso de compilación para [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] proyectos:  
  
-   Trabajar con varios archivos como una sola unidad.  
  
-   Mostrar un único archivo como una jerarquía de elementos secundarios.  
  
-   Mostrar un contexto de comandos en torno a los editores.  
  
-   Mostrar un contexto de servicio para los editores.  
  
## <a name="use-an-existing-project-type"></a>Utilizar un tipo de proyecto existente  
 Crear un nuevo proyecto a veces no es necesario. En la tabla siguiente se muestra las tareas que no es necesario para crear un tipo de proyecto para.  
  
|Tarea|Descripción|  
|----------|-----------------|  
|Control de comandos|Cualquier VSPackage puede controlar los comandos.|  
|Creación de un editor|Editores personalizados se pueden registrar. Para obtener más información, consulte [editores y documentos Windows](http://msdn.microsoft.com/en-us/603625e1-62b6-413a-bc44-089346e166bc).|  
|Propietario de windows|Puede crear ventanas de herramientas y documentos sin agregar un nuevo tipo de proyecto.|  
|Expone las propiedades en la ventana Propiedades|Todos los objetos pueden exponer propiedades.|  
  
## <a name="create-a-project-subtype"></a>Creación de un subtipo de proyecto  
 Subtipos de proyecto se pueden usar para extender un tipo de proyecto administrado sin tener que crear un nuevo tipo de proyecto. Subtipos de proyecto usar agregación COM para ampliar proyectos administrados, escritos en Microsoft [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] o [!INCLUDE[csprcs](../../includes/csprcs-md.md)]. Con la agregación de COM, puede reutilizar gran parte de la implementación de sistema de proyecto administrado y personalizar para un escenario determinado mediante la agregación y el uso de interfaces admitidas. Para obtener más información acerca de subtipos de proyecto, vea [subtipos de proyecto](../../extensibility/internals/project-subtypes.md).  
  
## <a name="see-also"></a>Vea también  
 [Editores y documentos Windows](http://msdn.microsoft.com/en-us/603625e1-62b6-413a-bc44-089346e166bc)   
 [Lista de comprobación: Creación de nuevos tipos de proyecto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Jerarquías en Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)

