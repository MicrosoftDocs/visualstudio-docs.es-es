---
title: Comandos definidos por el IDE para ampliar sistemas del proyecto | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b00a83774185b4fe65ee2b7171e25492320b5bfb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47577663"
---
# <a name="ide-defined-commands-for-extending-project-systems"></a>Comandos definidos por el IDE para ampliar sistemas del proyecto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDE-Defined comandos para ampliar sistemas del proyecto](https://docs.microsoft.com/visualstudio/extensibility/internals/ide-defined-commands-for-extending-project-systems).  
  
Cuando desea ampliar sistemas del proyecto, puede usar los comandos y proporcionados por los grupos de comandos la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE.  
  
 Las secciones siguientes enumeran los elementos de comando que son especialmente útiles para ampliar sistemas del proyecto.  
  
## <a name="command-menus"></a>Menús de comandos  
 La siguiente tabla muestra los menús de comandos que son ubicaciones útiles para colocar los comandos de alto nivel que invocan un extensor de proyecto.  
  
|Menú de comandos|Descripción|  
|------------------|-----------------|  
|IDM_VS_MENU_PROJECT|El **proyecto** menú de nivel superior.|  
|IDM_VS_TOOL_PROJWIN|El **el Explorador de soluciones** barra de herramientas.|  
  
## <a name="shortcut-menus"></a>Menús contextuales  
 La siguiente tabla muestra los menús contextuales que se aplican cuando se selecciona un solo nodo en el **el Explorador de soluciones**, o cuando hay varias selecciones homogéneas en el **el Explorador de soluciones**, que es cuando todos los nodos seleccionados son del mismo tipo.  
  
|Menú contextual|Descripción|  
|-------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|Se aplica cuando se selecciona el nodo del proyecto.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|Se aplica cuando se selecciona un archivo.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|Se aplica cuando se selecciona una carpeta.|  
|IDM_VS_CTXT_WEBREFFOLDER|Se aplica cuando se selecciona la carpeta de referencia Web.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|Se aplica cuando se selecciona el nodo raíz de referencias denominado "Referencias".|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|Se aplica cuando se seleccionan los nodos de referencia; Estos incluyen el ensamblado, COM y las referencias de proyecto. No incluye referencias Web.|  
  
 La siguiente tabla muestra los menús contextuales que se aplican cuando la selección en el **el Explorador de soluciones** abarca varias jerarquías  
  
|Menú contextual|Descripción|  
|-------------------|-----------------|  
|IDM_VS_CTXT_XPROJ_SLNPROJ|Se aplica cuando la selección actual contiene el nodo de la solución y los nodos raíz del proyecto.|  
|IDM_VS_CTXT_XPROJ_SLNITEM|Se aplica cuando la selección actual contiene los elementos de proyecto y el nodo de solución.|  
|IDM_VS_CTXT_XPROJ_MULTIPROJ|Se aplica cuando la selección actual se compone de varios nodos de proyecto de raíz solo.|  
|IDM_VS_CTXT_XPROJ_PROJITEM|Se aplica cuando la selección actual contiene una combinación de nodos raíz del proyecto y elementos de proyecto. Además, la selección puede contener el nodo de la solución.|  
|IDM_VS_CTXT_XPROJ_MULTIITEM|Se aplica cuando la selección actual contiene elementos de proyecto de varios proyectos en la solución, o cuando se seleccionan elementos de diferentes tipos en el mismo proyecto.|  
  
## <a name="command-groups"></a>Grupos de comandos  
 La siguiente tabla muestra los grupos de comandos que puede usar al extender los proyectos y que puede tener acceso a través de la <xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE> menú contextual.  
  
|Grupo de comandos|Descripción|  
|-------------------|-----------------|  
|IDG_VS_CTXT_PROJECT_BUILD|Comandos para crear, volver a generar e implementar el proyecto.|  
|IDG_VS_CTXT_COMPILELINK|Comandos para compilar y vincular el proyecto.|  
|IDG_VS_CTXT_PROJECT_CONFIG|Comandos que establece la configuración del proyecto y orden de compilación.|  
|IDG_VS_CTXT_PROJECT_ADD|Comandos que agregue elementos al proyecto.|  
|IDG_VS_CTXT_PROJECT_START|Comandos que establezca el proyecto de inicio asociado con la tecla F5.|  
|IDG_VS_CTXT_PROJECT_SAVE|Comandos para guardar elementos de proyecto.|  
|IDG_VS_CTXT_PROJECT_DEBUG|Comandos para la depuración.|  
|IDG_VS_CTXT_PROJECT_SCC|Comandos para el control de código fuente.|  
|IDG_VS_CTXT_PROJECT_TRANSFER|Comandos de cortar, copiar y pegar.|  
|IDG_VS_CTXT_PROJECT_PROPERTIES|Los comandos que proporcionan acceso a la **las propiedades del proyecto** cuadro de diálogo.|  
  
## <a name="see-also"></a>Vea también  
 [Cómo VSPackages agregar elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [MenuCommands frente a OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md)   
 [Creación de grupos reutilizables de botones](../../extensibility/creating-reusable-groups-of-buttons.md)

