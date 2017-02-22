---
title: "Cu&#225;ndo crear tipos de proyecto | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tipos de proyecto, las condiciones para la creación de"
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Cu&#225;ndo crear tipos de proyecto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

crear un nuevo tipo de proyecto proporciona una base para personalizar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para los usuarios.  Sin embargo, un nuevo tipo de proyecto no se requiere para todas las personalizaciones de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  Las instrucciones siguientes pueden ayudarle a determinar si se requiere un nuevo tipo de proyecto para el escenario.  
  
## Cree un tipo de proyecto nuevo  
 Debe crear un tipo de proyecto si desea personalizar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para representar de uno o más de las siguientes maneras:  
  
-   Participan en compilación, implementación, configuraciones, y el control de código fuente.  
  
-   Compatibilidad de depuración ofrecen.  
  
-   Elementos de proyecto de presentación de **Explorador de soluciones**.  
  
-   Use el cuadro de diálogo **Abrir proyecto** o de **Nuevo proyecto** .  
  
-   Anidamiento de proyecto compatible con.  
  
## Extender un tipo de proyecto existente  
 Puede crear un nuevo tipo de proyecto que puede utilizar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de las siguientes maneras de modificar o extender el comportamiento de un tipo de proyecto existente, por ejemplo, modificar el proceso de compilación de los proyectos de [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] :  
  
-   Trabajo con varios archivos como una unidad.  
  
-   Muestre un único archivo como jerarquía de sub\-elementos.  
  
-   Mostrar un contexto de comando alrededor de editores.  
  
-   Mostrar un contexto de servicio para los editores.  
  
## Utilice un tipo de proyecto existente  
 Crear un nuevo proyecto no a veces es necesario.  La tabla siguiente se muestran las tareas que no tiene que crear un tipo de proyecto de.  
  
|Tarea|Descripción|  
|-----------|-----------------|  
|Control de comandos|Cualquier VSPackage puede controlar los comandos.|  
|compilar un editor|Editores personalizados pueden registrarse.  Para obtener más información, vea [Document Windows and Editors](http://msdn.microsoft.com/es-es/603625e1-62b6-413a-bc44-089346e166bc).|  
|Propiedad de las ventanas|Puede crear la herramienta y las ventanas de documento sin agregar un nuevo tipo de proyecto.|  
|exponer propiedades en la ventana Propiedades|todos los objetos pueden exponer propiedades.|  
  
## cree un proyecto Subtype  
 Puede utilizar subtipos de proyecto para extender un tipo de proyecto administrado sin tener que crear un nuevo tipo de proyecto.  Los subtipos de proyectos utilizan la agregación COM para extender los proyectos administrados escritos en Microsoft [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] o [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)].  Con la agregación COM, puede reutilizar gran parte de la aplicación del sistema de proyectos administrados y todavía personalizarla para un escenario determinado con la agregación y el uso de admitir interfaces.  Para obtener más información sobre subtipos de proyectos, vea [Subtipos de proyecto](../../extensibility/internals/project-subtypes.md).  
  
## Vea también  
 [Document Windows and Editors](http://msdn.microsoft.com/es-es/603625e1-62b6-413a-bc44-089346e166bc)   
 [Lista de comprobación: Crear nuevos tipos de proyecto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Jerarquías en Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)