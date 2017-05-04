---
title: "Examinar las conexiones de SharePoint utilizando el Explorador de servidores | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.SharePointExplorer.SharePointConnection"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "conexiones de SharePoint [desarrollo de SharePoint en Visual Studio]"
  - "desarrollo de SharePoint en Visual Studio, explorar sitios de SharePoint"
  - "desarrollo de SharePoint en Visual Studio, Conexiones de SharePoint"
ms.assetid: b3b1d97b-e990-414c-8ba5-3fd1b463fbef
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Examinar las conexiones de SharePoint utilizando el Explorador de servidores
  Ahora puede examinar las conexiones locales de SharePoint en **Explorador de servidores**.  Con esta técnica, puede navegar por los componentes de un sitio de SharePoint en el sistema.  Los componentes de sitio de SharePoint, como definiciones y tipos de contenido enumerados, aparecen en un nodo denominado **Conexiones de SharePoint** en la vista de árbol de **Explorador de servidores**.  Para mostrar **Explorador de servidores**, en la barra de menú, elija **Visualización**, **Explorador de servidores**.  Además de mostrar los componentes de sitio de SharePoint, puede quitar elementos, ver sus propiedades, o actualizar la vista de árbol mediante comandos del menú contextual.  
  
> [!IMPORTANT]  
>  Para examinar un sitio de SharePoint, debe ser administrador de la colección de sitios de SharePoint, y debe ejecutar Visual Studio como administrador del equipo local.  Si no, el sitio aparecerá en **Explorador de servidores**, pero no podrá expandir su nodo.  Para comprobar si es un administrador de colección de sitios, abra el sitio en un explorador web, abra el menú de **Acciones del sitio** , elija **Permisos de sitio**y, a continuación, en la página de **Permisos: Team Site** , elija el comando de **Los administradores de colecciones de sitios** del grupo de **Administrar** en la cinta de opciones.  Su nombre aparecerá en el cuadro de texto si es un administrador de la colección de sitios.  Si el comando de **Los administradores de colecciones de sitios** no aparece en el grupo de control de la cinta de opciones, no es administrador de la colección de sitios, y debe obtener los permisos adecuados site administrator.  
  
## Nodos del explorador de servidores  
 Un nodo en la vista de árbol de **Explorador de servidores** en **Conexiones de SharePoint**representa cada componente de un sitio de SharePoint.  Por ejemplo, los sitios de SharePoint predeterminados incluyen un tipo de contenido denominado Discusión, que representa un tipo de discusión que muestra en la página **Discusiones** del sitio de SharePoint.  El tipo de contenido Discusiones contiene varios campos.  Para ver estos campos en **Explorador de servidores**, expanda el nodo de **Tipos de contenido** , y el nodo de **Discusión** .  Bajo él hay varios nodos de campos, como Cuerpo, Asunto de la discusión y Título.  
  
## Comandos del menú contextual de los nodos  
 Cada nodo tiene un menú contextual al que se tiene acceso haciendo clic con el botón secundario en el nodo o eligiendo y elige las teclas mayús\+f10.  Los comandos de nodo pueden incluir lo siguiente:  
  
|Nombre de comando|Descripción|  
|-----------------------|-----------------|  
|Actualizar|Actualiza la vista de árbol para reflejar cualquier cambio que se pueda haber producido desde la última vez que se mostró el nodo.|  
|Delete|Quita el nodo raíz seleccionado de la vista de árbol. **Note:**  Este comando solo está habilitado en las conexiones de SharePoint enumeradas bajo el nodo **Conexiones de SharePoint**.|  
|Propiedades|La ventana **Propiedades** muestra las propiedades disponibles del nodo seleccionado.  Las propiedades son todas de solo lectura y no todos los nodo tiene propiedades asociadas.|  
|Agregar conexión|Le permite especificar un sitio de SharePoint que desea examinar.  Esta disponible en el nodo **Conexiones de SharePoint** y los nodos de subsitio.|  
|Ver en el explorador|Muestra la lista seleccionada en el explorador web.  Este comando está disponible en algunas listas bajo el nodo **Listas** que se incluye en **Listas y bibliotecas**.|  
  
## Temas relacionados  
  
|Título|Descripción|  
|------------|-----------------|  
|[Cómo: Agregar o quitar conexiones de SharePoint](../sharepoint/how-to-add-or-remove-sharepoint-connections.md)|Describe los pasos que se requieren para agregar un nuevo sitio de SharePoint al nodo **Conexiones de SharePoint** en el **Explorador de servidores**.|  
  
## Vea también  
 [Server Explorer](http://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  