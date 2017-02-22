---
title: "C&#243;mo: Crear y editar configuraciones | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configuraciones de compilación, crear"
  - "configuraciones de compilación, editar"
  - "compilaciones [Visual Studio], configurar"
  - "Administrador de configuración"
  - "configuraciones de compilación del proyecto, crear"
  - "configuraciones de compilación del proyecto, editar"
  - "páginas de propiedades"
  - "configuraciones de compilación de la solución, crear"
  - "configuraciones de compilación de la solución, editar"
ms.assetid: 19be121c-148e-4ece-bbfc-d20b08cfc3f7
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# C&#243;mo: Crear y editar configuraciones
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se pueden crear configuraciones de compilación para una solución.  Por ejemplo, se puede configurar una compilación de depuración que los evaluadores pueden utilizar para buscar y corregir problemas, y se pueden configurar diferentes tipos de compilaciones que se pueden distribuir a distintos clientes.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Crear configuraciones de compilación  
 Puede utilizar el cuadro de diálogo **Administrador de configuración** para seleccionar o modificar configuraciones de compilación existentes, o para crear configuraciones nuevas.  
  
#### Para abrir el cuadro de diálogo Administrador de configuración  
  
-   En el **Explorador de soluciones**, abra el menú contextual de la solución y, a continuación, elija **Administrador de configuración**.  
  
    > [!NOTE]
    >  Si el comando **Administrador de configuración** no aparece en el menú contextual, busque bajo el menú **Compilar** en la barra de menús.  Si tampoco aparece allí, en la barra de menús, elija **Herramientas**, **Opciones**; después, en el panel izquierdo del cuadro de diálogo **Opciones**, expanda **Proyectos y soluciones**, **General** y, en el panel derecho, active la casilla **Mostrar configuraciones de compilación avanzadas**.  
  
     En el cuadro de diálogo **Administrador de configuración**, puede utilizar la lista desplegable **Configuración de soluciones activas** para seleccionar una configuración de compilación para toda la solución, modificar una configuración existente o crear una nueva configuración.  Puede utilizar la lista desplegable **Plataforma de soluciones activas** para seleccionar la plataforma de destino de la configuración, modificar una plataforma existente o agregar una nueva plataforma.  El panel **Contextos del proyecto** enumera los proyectos de la solución.  Para cada proyecto, puede seleccionar una configuración y una plataforma específicas del proyecto, modificar las existentes, o crear una nueva configuración o agregar una nueva plataforma.  También puede activar casillas que indican si cada proyecto se incluye o no cuando se utiliza la configuración para toda la solución al compilar o implementar la solución.  
  
 Después de establecer las configuraciones deseadas, puede establecer las propiedades del proyecto adecuadas para esas configuraciones.  
  
#### Para establecer propiedades basadas en configuraciones  
  
-   En el **Explorador de soluciones**, abra el menú contextual de un proyecto y, a continuación, elija **Propiedades**.  
  
     Se abre la ventana **Páginas de propiedades**.  
  
     Puede establecer propiedades para las configuraciones.  Por ejemplo, para una configuración de Release, puede especificar que se optimice el código cuando se compile la solución, y para una configuración de Debug, puede especificar que se incluya el símbolo de compilación condicional `DEBUG`.  Para obtener más información sobre las configuraciones de las páginas de propiedades, vea [Introduction to the Project Designer](http://msdn.microsoft.com/es-es/898dd854-c98d-430c-ba1b-a913ce3c73d7).  
  
## Crear y modificar configuraciones de proyecto  
  
#### Para crear una configuración de proyecto  
  
1.  Abra el cuadro de diálogo **Administrador de configuración**.  
  
2.  Seleccione un proyecto en la columna **Proyecto**.  
  
3.  En la lista desplegable **Configuración** de ese proyecto, elija **Nueva**.  
  
     Se abre el cuadro de diálogo **Nueva configuración del proyecto**.  
  
4.  En el cuadro **Nombre**, escriba un nombre para la nueva configuración.  
  
5.  Para utilizar las opciones de propiedad de una configuración de proyecto existente, en la lista desplegable **Copiar configuración de**, elija una configuración.  
  
6.  Para crear una configuración para toda la solución al mismo tiempo, active la casilla **Crear nueva configuración de solución**.  
  
#### Para cambiar el nombre de una configuración de proyecto  
  
1.  Abra el cuadro de diálogo **Administrador de configuración**.  
  
2.  En la columna **Proyecto**, seleccione el proyecto cuyo nombre de configuración del proyecto desea cambiar.  
  
3.  En la lista desplegable **Configuración** de ese proyecto, elija **Editar**.  
  
     Se abre el cuadro de diálogo **Editar configuraciones del proyecto**.  
  
4.  Seleccione el nombre de la configuración del proyecto que desea cambiar.  
  
5.  Seleccione **Cambiar nombre** y escriba un nuevo nombre.  
  
## Crear y modificar configuraciones de compilación para toda la solución  
  
#### Para crear una configuración de compilación para toda la solución  
  
1.  Abra el cuadro de diálogo **Administrador de configuración**.  
  
2.  En la lista desplegable **Configuración de soluciones activas**, elija **Nueva**.  
  
     Se abre el cuadro de diálogo **Nueva configuración de la solución**.  
  
3.  En el cuadro de texto **Nombre**, escriba el nombre de la nueva configuración.  
  
4.  Para utilizar las opciones de una configuración de solución existente, en la lista desplegable **Copiar configuración de**, elija una configuración.  
  
5.  Si desea crear configuraciones de proyecto al mismo tiempo, active la casilla **Crear nuevas configuraciones de proyecto**.  
  
#### Para cambiar el nombre de una configuración de compilación para toda la solución  
  
1.  Abra el cuadro de diálogo **Administrador de configuración**.  
  
2.  En la lista desplegable **Configuración de soluciones activas**, elija **Editar**.  
  
     Se abre el cuadro de diálogo **Editar configuraciones de soluciones**.  
  
3.  Seleccione el nombre de la configuración de soluciones que desea cambiar.  
  
4.  Seleccione **Cambiar nombre** y escriba un nuevo nombre.  
  
#### Para modificar una configuración de compilación en toda la solución  
  
1.  Abra el cuadro de diálogo **Administrador de configuración**.  
  
2.  En la lista desplegable **Configuración de soluciones activas**, seleccione la configuración que desee.  
  
3.  En el panel **Contextos del proyecto**, para cada proyecto, seleccione la **Configuración** y la **Plataforma** que desee, y seleccione si desea que sea de **Compilación** o **Implementación**.  
  
## Vea también  
 [Descripción de las configuraciones de compilación](../ide/understanding-build-configurations.md)   
 [Compilar y limpiar proyectos y soluciones en Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)   
 [Cómo: Modificar las propiedades y los valores de configuración del proyecto](http://msdn.microsoft.com/es-es/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)