---
title: "GUID e identificadores de comandos de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "comandos"
  - "id"
  - "colocación del comando"
  - "comando de Visual studio"
  - "GUID"
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# GUID e identificadores de comandos de Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

El GUID y los valores de identificador de los comandos incluidos en el entorno de desarrollo integrado de \(IDE\) Visual Studio se definen en los archivos de .vsct que se instalan como parte del SDK de Visual Studio.  Para obtener más información, vea [Grupos, menús y comandos definidos por el IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
 Para obtener más información sobre cómo trabajar con objetos del IDE que se definen en archivos de .vsct, vea [Comandos y menús de extensión](../../extensibility/extending-menus-and-commands.md).  
  
## Buscar una definición de comando  
 Dado que Visual Studio define más de mil comandos, es práctico enumerarlos todos aquí.  En su lugar, siga estos pasos para buscar la definición de un comando.  
  
#### Para encontrar una definición de comando  
  
1.  En Visual Studio, abra los archivos siguientes en *ruta de instalación de Visual Studio SDK*\\VisualStudioIntegration\\Common\\Inc\\ folder: SharedCmdDef.vsct, ShellCmdDef.vsct, VsDbgCmdUsed.vsct, Venusmenu .vsct.  
  
     La mayoría de los comandos de Visual Studio se definen en SharedCmdDef.vsct y ShellCmdDef.vsct.  VsDbgCmdUsed.vsct define los comandos que pertenecen al depurador, y Venusmenu.vsct define los comandos que son específicos del desarrollo web.  
  
2.  Si el comando es un elemento de menú, observe el texto exacto del elemento de menú.  Si el comando es un botón de una barra de herramientas, observe el texto de información sobre herramientas que aparece cuando se pausa en él.  
  
3.  Presione CTRL\+F para abrir el cuadro de diálogo de **Buscar** .  
  
4.  En el cuadro de **Buscar** , escriba el texto que anotó en el paso 2.  
  
5.  Compruebe que **Todos los documentos abiertos** se muestra en el cuadro de **Buscar en** .  
  
6.  Haga clic en el botón de **Buscar siguiente** hasta que el texto esté seleccionada en la sección de `<Strings>` de [Elemento Button](../../extensibility/button-element.md).  
  
     El elemento de `<Button>` que el comando aparecerá en es la definición de comando.  
  
 Cuando encuentre la definición de comando, puede colocar una copia del comando en otro menú o la barra de herramientas creando [Elemento CommandPlacement](../../extensibility/commandplacement-element.md) que tiene la `guid` y valores de `id` que el comando.  Para obtener más información, vea [Creación de grupos reutilizables de botones](../../extensibility/creating-reusable-groups-of-buttons.md).  
  
### casos especiales  
 En los casos siguientes, el texto de menú o el texto de información sobre herramientas puede no coincidir exactamente qué hay en la definición de comando.  
  
-   Elementos de menú que incluyen un carácter de subrayado, como el comando de **Imprimir** en el menú de **Archivo** , en el que se subraya p.  
  
     Los caracteres que va precedido por “y” el carácter en nombres de elementos de menú se muestran como subrayado.  Sin embargo, los archivos de .vsct se escriben en XML, que utiliza “y” carácter para indicar los caracteres especiales y requiere que una y comercial que debe ser mostrada debe ser tal como '&amp;'.  Por tanto, en un archivo de .vsct, el comando print aparece “&\#38;amp;imprimir”.  
  
-   Comandos que tienen texto dinámico, como **Guardar** *nombre de archivo actual*, y elementos de menú generados dinámicamente, como los elementos de la lista de **Archivos recientes** .  
  
     No hay ninguna forma confiable de búsqueda con el texto dinámico.  En su lugar, busque un grupo que hospeda el comando deseado consultando [GUID e identificadores de menús de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) o [GUID e identificadores de las barras de herramientas de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md), y búsqueda en el identificador del grupo.  Si la definición de comando no tiene el grupo como su [Elemento Parent](../../extensibility/parent-element.md), búsqueda SharedCmdPlace.vsct y ShellCmdPlace.vsct \(o VsDbgCmdPlace.vsct para los comandos del depurador\) para un elemento de `<CommandPlacement>` que establezca el elemento primario del comando.  SharedCmdPlace.vsct, ShellCmdPlace.vsct, andVsDbgCmdPlace.vsct están en *ruta de instalación de Visual Studio SDK*\\VisualStudioIntegration\\Common\\Inc \\.  
  
## Vea también  
 [MenuCommands frente a OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md)   
 [Tabla de comandos de Visual Studio \(. Archivos de Vsct\)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Referencia del esquema XML de VSCT](../../extensibility/vsct-xml-schema-reference.md)