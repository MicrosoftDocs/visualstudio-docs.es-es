---
title: IDE-Defined comandos para extender los sistemas de proyecto | Microsoft Docs
description: Obtenga información sobre los comandos y grupos de comandos definidos en Visual Studio entorno de desarrollo integrado (IDE) que se usan para extender los sistemas de proyecto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4525802bf308d740ea5c468fac171e74bff2b34e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901167"
---
# <a name="ide-defined-commands-for-extending-project-systems"></a>Comandos definidos por el IDE para ampliar sistemas del proyecto
Si desea ampliar los sistemas de proyecto, puede usar comandos y grupos de comandos proporcionados por el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

 En las secciones siguientes se enumeran los elementos de comando que son especialmente útiles para extender los sistemas de proyecto.

## <a name="command-menus"></a>Menús de comandos
 En la tabla siguiente se muestran los menús de comandos que son ubicaciones útiles para colocar comandos de alto nivel que invocan un extensor de proyecto.

|Menú Comandos|Descripción|
|------------------|-----------------|
|IDM_VS_MENU_PROJECT|Menú **de** nivel superior del proyecto.|
|IDM_VS_TOOL_PROJWIN|Barra **Explorador de soluciones** de herramientas.|

## <a name="shortcut-menus"></a>Menús contextuales
 En la tabla siguiente se muestran los menús contextuales que se aplican cuando se selecciona un solo nodo en **Explorador de soluciones** o cuando hay varias selecciones homogéneos en **Explorador de soluciones**, que es cuando todos los nodos seleccionados son del mismo tipo.

|Menú contextual|Descripción|
|-------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|Se aplica cuando se selecciona el nodo del proyecto.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|Se aplica cuando se selecciona un archivo.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|Se aplica cuando se selecciona una carpeta.|
|IDM_VS_CTXT_WEBREFFOLDER|Se aplica cuando se selecciona la carpeta Referencia web.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|Se aplica cuando se selecciona el nodo raíz de referencias denominado "Referencias".|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|Se aplica cuando se seleccionan los nodos de referencia; incluyen solo referencias de ensamblado, COM y proyecto. No incluye referencias web.|

 En la tabla siguiente se muestran los menús contextuales que se aplican cuando la **selección** del Explorador de soluciones abarca varias jerarquías,

|Menú contextual|Descripción|
|-------------------|-----------------|
|IDM_VS_CTXT_XPROJ_SLNPROJ|Se aplica cuando la selección actual contiene el nodo de solución y los nodos raíz del proyecto.|
|IDM_VS_CTXT_XPROJ_SLNITEM|Se aplica cuando la selección actual contiene el nodo de la solución y los elementos del proyecto.|
|IDM_VS_CTXT_XPROJ_MULTIPROJ|Se aplica cuando la selección actual consta solo de varios nodos raíz del proyecto.|
|IDM_VS_CTXT_XPROJ_PROJITEM|Se aplica cuando la selección actual contiene una combinación de nodos de proyecto raíz y elementos de proyecto. Además, la selección puede contener el nodo de la solución.|
|IDM_VS_CTXT_XPROJ_MULTIITEM|Se aplica cuando la selección actual contiene elementos de proyecto de varios proyectos de la solución o cuando se seleccionan elementos de tipos diferentes en el mismo proyecto.|

## <a name="command-groups"></a>Grupos de comandos
 En la tabla siguiente se muestran los grupos de comandos que puede usar al extender proyectos y a los que puede acceder a través del <xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE> menú contextual.

|Grupo de comandos|Descripción|
|-------------------|-----------------|
|IDG_VS_CTXT_PROJECT_BUILD|Comandos para compilar, recompilar e implementar el proyecto.|
|IDG_VS_CTXT_COMPILELINK|Comandos para compilar y vincular el proyecto.|
|IDG_VS_CTXT_PROJECT_CONFIG|Comandos que establecen la configuración del proyecto y el orden de compilación.|
|IDG_VS_CTXT_PROJECT_ADD|Comandos que agregan elementos al proyecto.|
|IDG_VS_CTXT_PROJECT_START|Comandos que establecen el proyecto de inicio asociado a la clave F5.|
|IDG_VS_CTXT_PROJECT_SAVE|Comandos para guardar elementos del proyecto.|
|IDG_VS_CTXT_PROJECT_DEBUG|Comandos para la depuración.|
|IDG_VS_CTXT_PROJECT_SCC|Comandos para el control de código fuente.|
|IDG_VS_CTXT_PROJECT_TRANSFER|Comandos para las operaciones de cortar, copiar y pegar.|
|IDG_VS_CTXT_PROJECT_PROPERTIES|Comandos que proporcionan acceso al cuadro de **diálogo Propiedades** del proyecto.|

## <a name="see-also"></a>Consulta también

- [Cómo VSPackages agrega elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Creación de grupos reutilizables de botones](../../extensibility/creating-reusable-groups-of-buttons.md)
