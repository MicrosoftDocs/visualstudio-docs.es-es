---
title: Comandos definidos por IDE para la ampliación de sistemas de proyectos Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 61c0b2924548f50ad650389e3ad81759be1986a4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707732"
---
# <a name="ide-defined-commands-for-extending-project-systems"></a>Comandos definidos por el IDE para ampliar sistemas del proyecto
Cuando desee ampliar los sistemas de proyecto, puede [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilizar comandos y grupos de comandos proporcionados por el IDE.

 En las secciones siguientes se enumeran los elementos de comando que son especialmente útiles para ampliar los sistemas de proyecto.

## <a name="command-menus"></a>Menús de comandos
 En la tabla siguiente se muestran los menús de comandos que son ubicaciones útiles para colocar comandos de alto nivel que invocan un extensor de proyecto.

|Menú de comandos|Descripción|
|------------------|-----------------|
|IDM_VS_MENU_PROJECT|El menú de nivel superior **del proyecto.**|
|IDM_VS_TOOL_PROJWIN|La barra de **herramientas del Explorador de soluciones.**|

## <a name="shortcut-menus"></a>Menús contextuales
 En la tabla siguiente se muestran los menús contextuales que se aplican cuando se selecciona un único nodo en el **Explorador**de soluciones o cuando hay varias selecciones homogéneas en el **Explorador**de soluciones, que es cuando todos los nodos seleccionados son del mismo tipo.

|Menú contextual|Descripción|
|-------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|Se aplica cuando se selecciona el nodo del proyecto.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|Se aplica cuando se selecciona un archivo.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|Se aplica cuando se selecciona una carpeta.|
|IDM_VS_CTXT_WEBREFFOLDER|Se aplica cuando se selecciona la carpeta Referencia web.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|Se aplica cuando se selecciona el nodo raíz de referencias denominado "Referencias".|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|Se aplica cuando se seleccionan nodos de referencia; estos incluyen solo referencias de ensamblado, COM y proyecto. No incluye referencias Web.|

 En la tabla siguiente se muestran los menús contextuales que se aplican cuando la selección en el **Explorador** de soluciones abarca varias jerarquías,

|Menú contextual|Descripción|
|-------------------|-----------------|
|IDM_VS_CTXT_XPROJ_SLNPROJ|Se aplica cuando la selección actual contiene el nodo de solución y los nodos raíz del proyecto.|
|IDM_VS_CTXT_XPROJ_SLNITEM|Se aplica cuando la selección actual contiene el nodo de solución y los elementos del proyecto.|
|IDM_VS_CTXT_XPROJ_MULTIPROJ|Se aplica cuando la selección actual consta únicamente de varios nodos de proyecto raíz.|
|IDM_VS_CTXT_XPROJ_PROJITEM|Se aplica cuando la selección actual contiene una combinación de nodos de proyecto raíz y elementos de proyecto. Además, la selección puede contener el nodo de solución.|
|IDM_VS_CTXT_XPROJ_MULTIITEM|Se aplica cuando la selección actual contiene elementos de proyecto de varios proyectos de la solución o cuando se seleccionan elementos de diferentes tipos en el mismo proyecto.|

## <a name="command-groups"></a>Grupos de comandos
 En la tabla siguiente se muestran los grupos de comandos que <xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE> puede utilizar al ampliar proyectos y a los que puede acceder a través del menú contextual.

|Grupo de comandos|Descripción|
|-------------------|-----------------|
|IDG_VS_CTXT_PROJECT_BUILD|Comandos para crear, reconstruir e implementar el proyecto.|
|IDG_VS_CTXT_COMPILELINK|Comandos para compilar y vincular el proyecto.|
|IDG_VS_CTXT_PROJECT_CONFIG|Comandos que establecen la configuración del proyecto y el orden de compilación.|
|IDG_VS_CTXT_PROJECT_ADD|Comandos que agregan elementos al proyecto.|
|IDG_VS_CTXT_PROJECT_START|Comandos que establecen el proyecto de inicio asociado a la tecla F5.|
|IDG_VS_CTXT_PROJECT_SAVE|Comandos para guardar elementos de proyecto.|
|IDG_VS_CTXT_PROJECT_DEBUG|Comandos para la depuración.|
|IDG_VS_CTXT_PROJECT_SCC|Comandos para el control de código fuente.|
|IDG_VS_CTXT_PROJECT_TRANSFER|Comandos para cortar, copiar y pegar operaciones.|
|IDG_VS_CTXT_PROJECT_PROPERTIES|Comandos que proporcionan acceso al cuadro de diálogo Propiedades del **proyecto.**|

## <a name="see-also"></a>Vea también

- [Cómo VSPackages agrega elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Creación de grupos reutilizables de botones](../../extensibility/creating-reusable-groups-of-buttons.md)
