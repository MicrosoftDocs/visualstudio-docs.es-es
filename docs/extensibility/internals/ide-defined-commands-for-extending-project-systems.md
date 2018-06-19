---
title: Comandos definidos por el IDE para ampliar sistemas del proyecto | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4941f5d842f311f078594ee9a9deef02219ea05d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132020"
---
# <a name="ide-defined-commands-for-extending-project-systems"></a>Comandos definidos por el IDE para ampliar sistemas del proyecto
Si desea ampliar sistemas del proyecto, puede usar comandos y comando grupos proporcionados por el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 Las siguientes secciones enumeran los elementos de comando que son especialmente útiles para ampliar sistemas del proyecto.  
  
## <a name="command-menus"></a>Menús de comando  
 La siguiente tabla muestra los menús de comando que se indican las ubicaciones útiles para colocar los comandos de alto nivel que invocan un extensor de proyecto.  
  
|Menú de comandos|Descripción|  
|------------------|-----------------|  
|IDM_VS_MENU_PROJECT|El **proyecto** menú de nivel superior.|  
|IDM_VS_TOOL_PROJWIN|El **el Explorador de soluciones** barra de herramientas.|  
  
## <a name="shortcut-menus"></a>Menús contextuales  
 La siguiente tabla muestra los menús contextuales que se aplican cuando se selecciona un nodo único en el **el Explorador de soluciones**, o cuando hay varias selecciones homogéneas en el **el Explorador de soluciones**, que es cuando todos los nodos seleccionados son del mismo tipo.  
  
|Menú contextual|Descripción|  
|-------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|Se aplica cuando se selecciona el nodo del proyecto.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|Se aplica cuando se selecciona un archivo.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|Se aplica cuando se selecciona una carpeta.|  
|IDM_VS_CTXT_WEBREFFOLDER|Se aplica cuando se selecciona la carpeta de referencia Web.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|Se aplica cuando se selecciona el nodo raíz de referencias denominado "Referencias".|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|Se aplica cuando se seleccionan los nodos de referencia; se trata de ensamblado, COM y las referencias de proyecto. No incluye referencias Web.|  
  
 La siguiente tabla muestra los menús contextuales que se aplican cuando la selección de la **el Explorador de soluciones** abarca varias jerarquías  
  
|Menú contextual|Descripción|  
|-------------------|-----------------|  
|IDM_VS_CTXT_XPROJ_SLNPROJ|Se aplica cuando la selección actual contiene el nodo de la solución y los nodos raíz del proyecto.|  
|IDM_VS_CTXT_XPROJ_SLNITEM|Se aplica cuando la selección actual contiene los elementos de proyecto y el nodo de la solución.|  
|IDM_VS_CTXT_XPROJ_MULTIPROJ|Se aplica cuando la selección actual está formada por varios nodos de proyecto de raíz sólo.|  
|IDM_VS_CTXT_XPROJ_PROJITEM|Se aplica cuando la selección actual contiene una combinación de nodos raíz del proyecto y elementos de proyecto. Además, la selección puede contener el nodo de la solución.|  
|IDM_VS_CTXT_XPROJ_MULTIITEM|Se aplica cuando la selección actual contiene elementos de proyecto de varios proyectos en la solución, o cuando se seleccionan elementos de diferentes tipos en el mismo proyecto.|  
  
## <a name="command-groups"></a>Grupos de comandos  
 La siguiente tabla muestra los grupos de comandos que puede utilizar cuando extender proyectos, y que puede tener acceso a través de la <xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE> menú contextual.  
  
|Grupo de comandos|Descripción|  
|-------------------|-----------------|  
|IDG_VS_CTXT_PROJECT_BUILD|Comandos para crear, volver a generar e implementar el proyecto.|  
|IDG_VS_CTXT_COMPILELINK|Comandos para compilar y vincular el proyecto.|  
|IDG_VS_CTXT_PROJECT_CONFIG|Comandos que establecen la configuración de proyecto y orden de compilación.|  
|IDG_VS_CTXT_PROJECT_ADD|Comandos que agregue elementos al proyecto.|  
|IDG_VS_CTXT_PROJECT_START|Comandos que se establezca el proyecto de inicio asociado a la tecla F5.|  
|IDG_VS_CTXT_PROJECT_SAVE|Comandos para guardar elementos de proyecto.|  
|IDG_VS_CTXT_PROJECT_DEBUG|Comandos para la depuración.|  
|IDG_VS_CTXT_PROJECT_SCC|Comandos de control de código fuente.|  
|IDG_VS_CTXT_PROJECT_TRANSFER|Comandos de cortar, copiar y pegar las operaciones.|  
|IDG_VS_CTXT_PROJECT_PROPERTIES|Comandos que proporcionan acceso a la **propiedades del proyecto** cuadro de diálogo.|  
  
## <a name="see-also"></a>Vea también  
 [¿Cómo VSPackages agregar elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [MenuCommands frente a OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)   
 [Creación de grupos reutilizables de botones](../../extensibility/creating-reusable-groups-of-buttons.md)