---
title: "Cuándo se debe crear tipos de proyecto | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: project types, conditions for creating
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b532ad4e72fb15cd9409c362259347f6f3833d2e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="when-to-create-project-types"></a>Cuándo se debe crear tipos de proyecto
Crear un nuevo tipo de proyecto proporciona el punto de partida para personalizar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para los usuarios. Sin embargo, crear un nuevo tipo de proyecto no es necesario para todos los [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] las personalizaciones. Las instrucciones siguientes puede ayudarle a determinar si un nuevo tipo de proyecto es necesario para su escenario.  
  
## <a name="create-a-new-project-type"></a>Crear un nuevo tipo de proyecto  
 Debe crear un tipo de proyecto si desea personalizar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para que actúe en una o varias de las siguientes maneras:  
  
-   Participa en la compilación, implementación, configuraciones y control de código fuente.  
  
-   Ofrece compatibilidad con la depuración.  
  
-   Mostrar elementos de proyecto en **el Explorador de soluciones**.  
  
-   Use la **Abrir proyecto** o **nuevo proyecto** cuadro de diálogo.  
  
-   Admite el anidamiento de proyecto.  
  
## <a name="extend-an-existing-project-type"></a>Extender un tipo de proyecto existente  
 Podría ser conveniente crear un nuevo tipo de proyecto que puede usar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de las maneras siguientes para modificar o extender el comportamiento de un tipo de proyecto existente, por ejemplo, modificar el proceso de compilación de [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] proyectos:  
  
-   Trabajar con varios archivos como una sola unidad.  
  
-   Mostrar un único archivo como una jerarquía de elementos secundarios.  
  
-   Mostrar un contexto de los comandos alrededor de editores.  
  
-   Mostrar un contexto de servicio para los editores.  
  
## <a name="use-an-existing-project-type"></a>Utilizar un tipo de proyecto existente  
 Crear un nuevo proyecto a veces no es necesario. En la tabla siguiente muestra las tareas que no es necesario crear un tipo de proyecto para.  
  
|Tarea|Descripción|  
|----------|-----------------|  
|Control de comandos|Cualquier VSPackage puede controlar comandos.|  
|Creación de un editor|Editores personalizados se pueden registrar. Para obtener más información, consulte [editores y ventanas de documento](http://msdn.microsoft.com/en-us/603625e1-62b6-413a-bc44-089346e166bc).|  
|Propietario de windows|Puede crear ventanas de herramientas y documentos sin tener que agregar un nuevo tipo de proyecto.|  
|Expone las propiedades en la ventana Propiedades|Todos los objetos pueden exponer propiedades.|  
  
## <a name="create-a-project-subtype"></a>Crear un subtipo de proyecto  
 Puede usar los subtipos de proyecto para ampliar un tipo de proyecto administrado sin tener que crear un nuevo tipo de proyecto. Subtipos de proyecto usan la agregación de COM para extender los proyectos administrados, escritos en Microsoft [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] o [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]. Con la agregación de COM, puede reutilizar gran parte de la implementación de sistema de proyecto administrado y personalizar para un escenario determinado mediante la agregación y el uso de interfaces de admitir. Para obtener más información acerca de los subtipos de proyecto, vea [subtipos de proyecto](../../extensibility/internals/project-subtypes.md).  
  
## <a name="see-also"></a>Vea también  
 [Ventanas de documento y editores](http://msdn.microsoft.com/en-us/603625e1-62b6-413a-bc44-089346e166bc)   
 [Lista de comprobación: Creación de nuevos tipos de proyecto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Jerarquías en Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)