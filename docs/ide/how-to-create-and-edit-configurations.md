---
title: "Cómo: Crear y editar configuraciones | Microsoft Docs"
ms.custom: 
ms.date: 06/21/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- solution build configurations, editing
- build configurations, creating
- solution build configurations, creating
- build configurations, editing
- builds [Visual Studio], setting up
- property pages
- Configuration Manager
- project build configurations, creating
- project build configurations, editing
ms.assetid: 19be121c-148e-4ece-bbfc-d20b08cfc3f7
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: afa939c0b8a033930f5e8e7bcc525d6f33e55f86
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-and-edit-configurations"></a>Cómo: Crear y editar configuraciones
Se pueden crear configuraciones de compilación para una solución. Por ejemplo, se puede configurar una compilación de depuración que los evaluadores pueden utilizar para buscar y corregir problemas, y se pueden configurar diferentes tipos de compilaciones que se pueden distribuir a distintos clientes.  

 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  

## <a name="creating-build-configurations"></a>Crear configuraciones de compilación  
 Puede usar el cuadro de diálogo **Administrador de configuración** para seleccionar o modificar configuraciones de compilación existentes, o para crear configuraciones nuevas.  

#### <a name="to-open-the-configuration-manager-dialog-box"></a>Para abrir el cuadro de diálogo Administrador de configuración  

-   En el **Explorador de soluciones**, abra el menú contextual de la solución y, después, pulse **Administrador de configuración**.  

    > [!NOTE]
    >  Si el comando **Administrador de configuración** no aparece en el menú contextual, busque bajo el menú **Compilar** en la barra de menús. Si tampoco aparece allí, en la barra de menús, pulse **Herramientas**, **Opciones**; después, en el panel izquierdo del cuadro de diálogo **Opciones**, expanda **Proyectos y soluciones**, **General** y, en el panel derecho, active la casilla **Mostrar configuraciones de compilación avanzadas**.  

     En el cuadro de diálogo **Administrador de configuración**, puede usar la lista desplegable **Configuración de soluciones activas** para seleccionar una configuración de compilación para toda la solución, modificar una configuración existente o crear una nueva configuración. Puede usar la lista desplegable **Plataforma de soluciones activas** para seleccionar la plataforma de destino de la configuración, modificar una plataforma existente o agregar una nueva plataforma. El panel **Contextos del proyecto** enumera los proyectos de la solución. Para cada proyecto, puede seleccionar una configuración y una plataforma específicas del proyecto, modificar las existentes, o crear una nueva configuración o agregar una nueva plataforma. También puede activar casillas que indican si cada proyecto se incluye o no cuando se utiliza la configuración para toda la solución al compilar o implementar la solución.  

 Después de establecer las configuraciones deseadas, puede establecer las propiedades del proyecto adecuadas para esas configuraciones.  

#### <a name="to-set-properties-based-on-configurations"></a>Para establecer propiedades basadas en configuraciones  

-   En el **Explorador de soluciones**, abra el menú contextual de un proyecto y, después, pulse **Propiedades**.  

     Se abre la ventana **Páginas de propiedades**.  

     Puede establecer propiedades para las configuraciones. Por ejemplo, para una configuración de Release, puede especificar que se optimice el código cuando se compile la solución, y para una configuración de Debug, puede especificar que se incluya el símbolo de compilación condicional `DEBUG`. Para obtener más información sobre la configuración de la página propiedades, vea [Administrar propiedades de soluciones y proyectos](../ide/managing-project-and-solution-properties.md).  

## <a name="creating-and-modifying-project-configurations"></a>Crear y modificar configuraciones de proyecto  

#### <a name="to-create-a-project-configuration"></a>Para crear una configuración de proyecto  

1.  Abra el cuadro de diálogo **Administrador de configuración**.  

2.  Seleccione un proyecto en la columna **Proyecto**.  

3.  En la lista desplegable **Configuración** de ese proyecto, pulse **Nueva**.  

     Se abre el cuadro de diálogo **Nueva configuración del proyecto**.  

4.  En el cuadro **Nombre**, escriba un nombre para la nueva configuración.  

5.  Para usar las opciones de propiedad de una configuración de proyecto existente, en la lista desplegable **Copiar configuración de**, pulse una configuración.  

6.  Para crear una configuración para toda la solución al mismo tiempo, active la casilla **Crear nueva configuración de solución**.  

#### <a name="to-rename-a-project-configuration"></a>Para cambiar el nombre de una configuración de proyecto  

1.  Abra el cuadro de diálogo **Administrador de configuración**.  

2.  En la columna **Proyecto**, seleccione el proyecto cuyo nombre de configuración del proyecto quiere cambiar.  

3.  En la lista desplegable **Configuración** de ese proyecto, pulse **Editar**.  

     Se abre el cuadro de diálogo **Editar configuraciones del proyecto**.  

4.  Seleccione el nombre de la configuración del proyecto que desea cambiar.  

5.  Seleccione **Cambiar nombre** y escriba un nuevo nombre.  

## <a name="creating-and-modifying-solution-wide-build-configurations"></a>Crear y modificar configuraciones de compilación para toda la solución  

#### <a name="to-create-a-solution-wide-build-configuration"></a>Para crear una configuración de compilación para toda la solución  

1.  Abra el cuadro de diálogo **Administrador de configuración**.  

2.  En la lista desplegable **Configuración de soluciones activas**, pulse **Nueva**.  

     Se abre el cuadro de diálogo **Nueva configuración de la solución**.  

3.  En el cuadro de texto **Nombre**, escriba el nombre de la nueva configuración.  

4.  Para usar las opciones de una configuración de solución existente, en la lista desplegable **Copiar configuración de**, pulse una configuración.  

5.  Si quiere crear configuraciones de proyecto al mismo tiempo, active la casilla **Crear nuevas configuraciones de proyecto**.  

#### <a name="to-rename-a-solution-wide-build-configuration"></a>Para cambiar el nombre de una configuración de compilación para toda la solución  

1.  Abra el cuadro de diálogo **Administrador de configuración**.  

2.  En la lista desplegable **Configuración de soluciones activas**, pulse **Editar**.  

     Se abre el cuadro de diálogo **Editar configuraciones de soluciones**.  

3.  Seleccione el nombre de la configuración de soluciones que desea cambiar.  

4.  Seleccione **Cambiar nombre** y escriba un nuevo nombre.  

#### <a name="to-modify-a-solution-wide-build-configuration"></a>Para modificar una configuración de compilación en toda la solución  

1.  Abra el cuadro de diálogo **Administrador de configuración**.  

2.  En la lista desplegable **Configuración de soluciones activas**, seleccione la configuración que quiera.  

3.  En el panel **Contextos del proyecto**, para cada proyecto, seleccione la **Configuración** y la **Plataforma** que quiera, y seleccione si quiere que sea de **Compilación** o **Implementación**.  

## <a name="see-also"></a>Vea también  
 [Descripción de las configuraciones de compilación](../ide/understanding-build-configurations.md)   
 [Compilar y limpiar proyectos y soluciones en Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)   
 [Administrar propiedades de soluciones y proyectos](managing-project-and-solution-properties.md)

