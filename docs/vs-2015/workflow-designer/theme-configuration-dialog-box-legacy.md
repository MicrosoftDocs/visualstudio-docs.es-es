---
title: Configuración de tema (cuadro de diálogo) (heredado) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.ComponentModel.Design.ThemeConfigurationDialog.UI
helpviewer_keywords:
- themes, configuring
- Theme Configuration dialog box
ms.assetid: 9e6d182a-c4d9-4e71-b2b9-02f675fc2b29
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8171c6dcfe285ade07531896893915d0e209e0c1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670190"
---
# <a name="theme-configuration-dialog-box-legacy"></a>Configuración de tema (Cuadro de diálogo) (Heredado)
En este tema se describe cómo usar el cuadro de diálogo **configuración de tema** en el [!INCLUDE[wfd1](../includes/wfd1-md.md)] heredado. Use el [!INCLUDE[wfd2](../includes/wfd2-md.md)] heredado cuando deba tener como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Un tema define los colores de fondo y de primer plano, estilos, iconos y otros elementos visuales de un flujo de trabajo. Puede guardar los temas para volverlos a usar en otros flujos de trabajo.

 Puede crear y editar temas mediante el cuadro de diálogo **configuración de tema** . Para abrir el cuadro de diálogo, seleccione **crear nuevo tema** en el menú **flujo** de trabajo o haga clic con el botón derecho en la superficie de diseño de flujo de trabajo y seleccione **crear nuevo tema**.

 En la tabla siguiente se describen los elementos de la interfaz de usuario (UI) del cuadro de diálogo **configuración de tema** .

|Elemento de la interfaz de usuario|Descripción|
|----------------|-----------------|
|**Nombre del tema:**|Nombre que identifica el tema en los [temas, diseñador de flujo de trabajo, opciones (cuadro de diálogo) (heredado)](../workflow-designer/themes-workflow-designer-options-dialog-box-legacy.md). Para los temas nuevos se genera un nombre que se puede cambiar.|
|**Ubicación del tema:**|Nombre y ruta de acceso del archivo del tema. Para los nuevos temas se genera un nombre de archivo que se puede cambiar, basado en el nombre del tema generado. Si cambia el nombre del tema generado, puede que desee cambiar el nombre de archivo para que coincida con el nombre del tema.|
|**...**|Haga clic para seleccionar la ubicación para guardar el archivo de tema de flujo de trabajo, que utiliza la extensión de nombre de archivo .wtm. La ruta de acceso seleccionada se verá en el cuadro de texto **Ubicación del tema** .|
|**Seleccionar diseñador y configurar propiedades:**|En el panel izquierdo se muestra una vista de árbol de las actividades para las que se puede personalizar el tema. Seleccione una actividad en la vista de árbol y se mostrarán las propiedades del tema para la actividad en el panel de propiedades, situado a la derecha del panel de vista del árbol. Haga clic en una propiedad para cambiar su valor.|
|**Vista previa**|Haga clic para mostrar una ventana con una vista previa de los efectos de los cambios realizados en la propiedad.|

## <a name="see-also"></a>Vea también
 [Temas, diseñador de flujo de trabajo, cuadro de diálogo Opciones (heredado)](../workflow-designer/themes-workflow-designer-options-dialog-box-legacy.md) [Diseñador heredado para Windows Workflow Foundation ayuda de la interfaz de usuario](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)