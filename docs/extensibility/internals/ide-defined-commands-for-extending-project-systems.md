---
title: "Comandos definidos por el IDE para ampliar sistemas del proyecto | Microsoft Docs"
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
  - "comandos de sistemas del proyecto"
  - "sistemas de proyectos, los comandos definidos por el entorno"
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
caps.latest.revision: 19
caps.handback.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
---
# Comandos definidos por el IDE para ampliar sistemas del proyecto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cuando desee extender los sistemas de proyectos, puede utilizar los comandos y grupos de comando proporcionados por [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el IDE.  
  
 Las secciones siguientes se enumeran los elementos command que son especialmente útiles para los sistemas de proyectos que extienden.  
  
## menús de comandos  
 La tabla siguiente se muestran los menús de comandos que son útiles para poner los comandos de alto nivel que invocan un extensor de proyecto.  
  
|menú de comandos|Descripción|  
|----------------------|-----------------|  
|IDM\_VS\_MENU\_PROJECT|El menú de nivel superior de **proyecto** .|  
|IDM\_VS\_TOOL\_PROJWIN|la barra de herramientas de **Explorador de soluciones** .|  
  
## Menús contextuales  
 La tabla siguiente se muestran los menús contextuales que se aplican a un único nodo está seleccionado en **Explorador de soluciones**, o cuando hay selecciones homogéneas en varias **Explorador de soluciones**, que es cuando todos los nodos seleccionados son del mismo tipo.  
  
|Menú contextual|Descripción|  
|---------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|Se aplica cuando el nodo del proyecto está seleccionado.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|Se aplica cuando un archivo está seleccionado.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|Se aplica cuando una carpeta está seleccionado.|  
|IDM\_VS\_CTXT\_WEBREFFOLDER|Se aplica a la carpeta de referencia web está seleccionado.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|Se aplica cuando el nodo raíz de las referencias denominado “referencias” está seleccionado.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|Se aplica a los nodos de referencia son seleccionado; éstos incluyen el ensamblado, COM, y referencias de proyecto solo.  no incluye referencias web.|  
  
 La tabla siguiente se muestran los menús contextuales que se aplican cuando la selección en **Explorador de soluciones** abarca varias jerarquías,  
  
|Menú contextual|Descripción|  
|---------------------|-----------------|  
|IDM\_VS\_CTXT\_XPROJ\_SLNPROJ|Se aplica a la selección actual contiene nodos de nodo y raíz del proyecto de la solución.|  
|IDM\_VS\_CTXT\_XPROJ\_SLNITEM|Se aplica a la selección actual contiene el nodo y elementos de proyecto de la solución.|  
|IDM\_VS\_CTXT\_XPROJ\_MULTIPROJ|Se aplica a la selección actual consta de varios nodos raíz del proyecto.|  
|IDM\_VS\_CTXT\_XPROJ\_PROJITEM|Se aplica a la selección actual contiene una mezcla de nodos y elementos de proyecto raíz.  además, la selección puede contener el nodo de la solución.|  
|IDM\_VS\_CTXT\_XPROJ\_MULTIITEM|Se aplica a la selección actual contiene elementos de proyecto de varios proyectos de la solución, o cuando los elementos de distintos tipos son seleccionado en el mismo proyecto.|  
  
## grupos de comando  
 La tabla siguiente se muestran los grupos de comandos que puede utilizar al extender proyectos de, y que puede tener acceso a través del menú contextual de <xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE> .  
  
|Grupo de comandos|Descripción|  
|-----------------------|-----------------|  
|IDG\_VS\_CTXT\_PROJECT\_BUILD|Comandos para compilar, recompilar, e implementar el proyecto.|  
|IDG\_VS\_CTXT\_COMPILELINK|comandos para compilar y vincular el proyecto.|  
|IDG\_VS\_CTXT\_PROJECT\_CONFIG|Comandos que establecen orden de instalación y configuración de compilación del proyecto.|  
|IDG\_VS\_CTXT\_PROJECT\_ADD|Comandos que agregan elementos al proyecto.|  
|IDG\_VS\_CTXT\_PROJECT\_START|Comandos que establecen el proyecto de inicio asociado con la tecla F5.|  
|IDG\_VS\_CTXT\_PROJECT\_SAVE|comandos para guardar elementos de proyecto.|  
|IDG\_VS\_CTXT\_PROJECT\_DEBUG|comandos para depurar.|  
|IDG\_VS\_CTXT\_PROJECT\_SCC|Comandos del control de código fuente.|  
|IDG\_VS\_CTXT\_PROJECT\_TRANSFER|Comandos para operaciones de cortar, copy y pegar.|  
|IDG\_VS\_CTXT\_PROJECT\_PROPERTIES|Comandos que proporcionan acceso al cuadro de diálogo de **Propiedades del proyecto** .|  
  
## Vea también  
 [Cómo VSPackages agregar elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [MenuCommands frente a OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md)   
 [Creación de grupos reutilizables de botones](../../extensibility/creating-reusable-groups-of-buttons.md)